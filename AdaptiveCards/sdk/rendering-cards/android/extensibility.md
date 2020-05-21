---
title: Расширяемость пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 1281a31c333474c1899831acab28c962ce8e4514
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631309"
---
# <a name="extensibility---android"></a><span data-ttu-id="075dc-102">Расширяемость — Android</span><span class="sxs-lookup"><span data-stu-id="075dc-102">Extensibility - Android</span></span>

<span data-ttu-id="075dc-103">Модуль подготовки Android можно расширить для поддержки нескольких сценариев, в том числе:</span><span class="sxs-lookup"><span data-stu-id="075dc-103">The Android renderer can be extended to support multiple scenarios including:</span></span>
* [<span data-ttu-id="075dc-104">Пользовательский анализ элементов карточки</span><span class="sxs-lookup"><span data-stu-id="075dc-104">Custom Parsing of Card Elements</span></span>](#custom-parsing-of-card-elements)
* [<span data-ttu-id="075dc-105">Пользовательская визуализация элементов карточки</span><span class="sxs-lookup"><span data-stu-id="075dc-105">Custom Rendering of Card Elements</span></span>](#custom-rendering-of-card-elements)
* <span data-ttu-id="075dc-106">[Пользовательская отрисовка действий](#custom-rendering-of-actions) (начиная с версии 1.2)</span><span class="sxs-lookup"><span data-stu-id="075dc-106">[Custom Rendering of Actions](#custom-rendering-of-actions) (Since v1.2)</span></span>
* <span data-ttu-id="075dc-107">[Пользовательская загрузка образа](#custom-image-loading) (начиная с v 1.0.1)</span><span class="sxs-lookup"><span data-stu-id="075dc-107">[Custom Image Loading](#custom-image-loading) (Since v1.0.1)</span></span>
* <span data-ttu-id="075dc-108">[Пользовательская Загрузка носителя](#custom-media-loading) (начиная с версии 1.1)</span><span class="sxs-lookup"><span data-stu-id="075dc-108">[Custom Media Loading](#custom-media-loading) (Since v1.1)</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="075dc-109">Пользовательский анализ элементов карточки</span><span class="sxs-lookup"><span data-stu-id="075dc-109">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="075dc-110">Средство синтаксического анализа можно расширить, чтобы включить поддержку определяемых пользователем элементов карточки.</span><span class="sxs-lookup"><span data-stu-id="075dc-110">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="075dc-111">Например, есть новый тип элемента, который выглядит так:</span><span class="sxs-lookup"><span data-stu-id="075dc-111">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="075dc-112">Следующий пример демонстрирует, как преобразовать его в CardElement, который является расширением BaseCardElement:</span><span class="sxs-lookup"><span data-stu-id="075dc-112">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
```java
public class MyCustomCardElement extends BaseCardElement
{

    public MyCustomCardElement(CardElementType type) {
        super(type);
    }

    public String getMyTypeData()
    {
        return myTypeData;
    }

    public void setMyTypeData(String data)
    {
        myTypeData = data;
    }

    private String myTypeData;
}

public class MyCardElementParser extends BaseCardElementParser
{
    @Override
    public BaseCardElement Deserialize(ElementParserRegistration elementParserRegistration, ActionParserRegistration actionParserRegistration, JsonValue value)
    {
        MyCustomCardElement element = new CustomCardElement(CardElementType.Custom);
        element.SetElementTypeString("MyType");
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setMyTypeData(obj.getString("secret"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setMyTypeData("Failed");
        }
        return element;
    }
}
```

<span data-ttu-id="075dc-113">Чтобы зарегистрировать средство синтаксического анализа и получить объект адаптивной карточки, который содержит пользовательский элемент, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="075dc-113">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="075dc-114">Далее рассматривается визуализация пользовательского элемента.</span><span class="sxs-lookup"><span data-stu-id="075dc-114">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="075dc-115">Пользовательская визуализация элементов карточки</span><span class="sxs-lookup"><span data-stu-id="075dc-115">Custom Rendering of Card Elements</span></span>

> [!IMPORTANT]
>
> <span data-ttu-id="075dc-116">**Список критических изменений**</span><span class="sxs-lookup"><span data-stu-id="075dc-116">**List of Breaking Changes**</span></span>
>
> [<span data-ttu-id="075dc-117">Критические изменения в версии 1.2</span><span class="sxs-lookup"><span data-stu-id="075dc-117">Breaking changes for v1.2</span></span>](#breaking-changes-for-v12)

<span data-ttu-id="075dc-118">Чтобы определить собственный пользовательский модуль подготовки отчетов для нашего типа, сначала необходимо создать класс, который расширяется из ```BaseCardElementRenderer``` :</span><span class="sxs-lookup"><span data-stu-id="075dc-118">To define our own custom renderer for our type, we must first create a class that extends from ```BaseCardElementRenderer```:</span></span>
```java
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(Context context, FragmentManager fragmentManager, ViewGroup viewGroup, BaseCardElement baseCardElement, Vector<IInputHandler> inputActionHandlerList, ICardActionHandler cardActionHandler, HostConfig hostConfig, ContainerStyle containerStyle) {

        //Call findImplObj on baseCardElement to get the instance we returned at parse. We can then cast that object to our type
        CustomCardElement element = (CustomCardElement) baseCardElement.findImplObj();

        //Create some view and add it to the view group
        TextView textView = new TextView(context);
        textView.setText(element.getMyTypeData());
        textView.setAllCaps(true);
        viewGroup.addView(textView);

        //return the view
        return textView;
    }
}
```

<span data-ttu-id="075dc-119">Затем необходимо зарегистрировать средство визуализации следующим образом:</span><span class="sxs-lookup"><span data-stu-id="075dc-119">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a><span data-ttu-id="075dc-120">Критические изменения в версии 1.2</span><span class="sxs-lookup"><span data-stu-id="075dc-120">Breaking changes for v1.2</span></span>

<span data-ttu-id="075dc-121">```render```Метод был изменен для включения ```RenderedAdaptiveCard``` параметра и ```ContainerStyle``` был изменен для рендераргс, где теперь содержится контаинерстиле, поэтому класс, расширяющий басекарделементрендерер, должен выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="075dc-121">The ```render``` method was changed to include the ```RenderedAdaptiveCard``` parameter and ```ContainerStyle``` was changed for a RenderArgs where the ContainerStyle is now contained so a class that extends BaseCardElementRenderer should look like this</span></span>

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a><span data-ttu-id="075dc-122">Пользовательский анализ действий карточек</span><span class="sxs-lookup"><span data-stu-id="075dc-122">Custom Parsing of Card Actions</span></span>

<span data-ttu-id="075dc-123">Аналогично анализу пользовательских элементов карт в версии 1.2 появилась возможность анализировать пользовательские действия.</span><span class="sxs-lookup"><span data-stu-id="075dc-123">Similarly to parsing custom card elements in v1.2 the possibility to parse custom actions was introduced.</span></span> <span data-ttu-id="075dc-124">Например, предположим, что у нас есть новый тип действия, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="075dc-124">For example, say we have a new action type that looks like this:</span></span>
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

<span data-ttu-id="075dc-125">Затем в следующих строках показано, как выполнить синтаксический анализ в Актионелемент, который расширяется из ```BaseActionElement``` :</span><span class="sxs-lookup"><span data-stu-id="075dc-125">Then the following lines demonstrate how to parse it into a ActionElement that extends from the ```BaseActionElement```:</span></span>
```java
public class MyActionElement extends BaseActionElement
{
    public MyActionElement(ActionType type) 
    {
        super(type);
    }

    public String getActionData()
    {
        return mActionData;
    }

    public void setActionData(String s)
    {
        mActionData = s;
    }

    private String mActionData;
    public static final String MyActionId = "myAction";
}

public class MyActionParser extends ActionElementParser
{
    @Override
    public BaseActionElement Deserialize(ParseContext context, JsonValue value)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        String val = value.getString();
        try {
            JSONObject obj = new JSONObject(val);
            element.setActionData(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setActionData("Failure");
        }
        return element;
    }

    @Override
    public BaseActionElement DeserializeFromString(ParseContext context, String jsonString)
    {
        MyActionElement element = new MyActionElement(ActionType.Custom);
        element.SetElementTypeString(MyActionElement.MyActionId);
        try {
            JSONObject obj = new JSONObject(jsonString);
            element.setBackwardString(obj.getString("ActionData"));
        } catch (JSONException e) {
            e.printStackTrace();
            element.setBackwardString("Failure");
        }
        return element;
    }
}
```

<span data-ttu-id="075dc-126">А в следующих строках показано, как зарегистрировать средство синтаксического анализа и получить объект Адаптивекард, содержащий элемент настраиваемого действия:</span><span class="sxs-lookup"><span data-stu-id="075dc-126">And the next lines demonstrate how to register the parser and get an AdaptiveCard object that contains the custom action element:</span></span>
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="075dc-127">Далее идет подготовка настраиваемого действия к просмотру.</span><span class="sxs-lookup"><span data-stu-id="075dc-127">Next comes rendering the custom action</span></span>

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="075dc-128">Пользовательская отрисовка действий</span><span class="sxs-lookup"><span data-stu-id="075dc-128">Custom Rendering of Actions</span></span>

<span data-ttu-id="075dc-129">Чтобы определить собственный обработчик настраиваемых действий для нашего типа, сначала необходимо создать класс, который расширяется из ```BaseActionElementRenderer``` :</span><span class="sxs-lookup"><span data-stu-id="075dc-129">To define our own custom action renderer for our type, we must first create a class that extends from ```BaseActionElementRenderer```:</span></span>
```java
public class MyActionRenderer extends BaseActionElementRenderer
{
    @Override
    public Button render(RenderedAdaptiveCard renderedCard,
                         Context context,
                         FragmentManager fragmentManager,
                         ViewGroup viewGroup,
                         BaseActionElement baseActionElement,
                         ICardActionHandler cardActionHandler,
                         HostConfig hostConfig,
                         RenderArgs renderArgs)
    {
        Button myActionButton = new Button(context);

        CustomActionElement customAction = (CustomActionElement) baseActionElement.findImplObj();

        myActionButton.setBackgroundColor(getResources().getColor(R.color.greenActionColor));
        myActionButton.setText(customAction.getMessage());
        myActionButton.setAllCaps(false);
        myActionButton.setOnClickListener(new BaseActionElementRenderer.ActionOnClickListener(renderedCard, baseActionElement, cardActionHandler));

        viewGroup.addView(myActionButton);

        return myActionButton;
    }
}
```

<span data-ttu-id="075dc-130">Затем необходимо зарегистрировать средство визуализации следующим образом:</span><span class="sxs-lookup"><span data-stu-id="075dc-130">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="075dc-131">Пользовательская визуализация действий</span><span class="sxs-lookup"><span data-stu-id="075dc-131">Custom rendering of actions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="075dc-132">Реализация изменений в пользовательской визуализации действий, запланированная в версии 1.2, пока не завершена.</span><span class="sxs-lookup"><span data-stu-id="075dc-132">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="075dc-133">Пользовательская загрузка изображений</span><span class="sxs-lookup"><span data-stu-id="075dc-133">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="075dc-134">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="075dc-134">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="075dc-135">**Зарегистрировать можно только IOnlineImageLoader с приоритетом над стандартным способом получения изображений**.</span><span class="sxs-lookup"><span data-stu-id="075dc-135">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="075dc-136">Мы добавили IOnlineImageLoader, чтобы разработчики могли извлекать изображения, не только скачивая или получая их из Интернета. Кроме того, им теперь не нужно выполнять предварительные действия для получения изображений.</span><span class="sxs-lookup"><span data-stu-id="075dc-136">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="075dc-137">Для реализации OnlineImageLoader необходимо просто реализовать метод.</span><span class="sxs-lookup"><span data-stu-id="075dc-137">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="075dc-138">Ниже приведен пример OnlineImageLoader для изменения всех изображений, связанных с изображением кота.</span><span class="sxs-lookup"><span data-stu-id="075dc-138">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImageUri);
        }

        Bitmap bitmap = BitmapFactory.decodeByteArray(bytes, 0, bytes.length);

        if (bitmap == null)
        {
            throw new IOException("Failed to convert content to bitmap: " + new String(bytes));
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

<span data-ttu-id="075dc-139">Наконец, чтобы зарегистрировать этот загрузчик изображений, необходимо добавить в код следующую строку.</span><span class="sxs-lookup"><span data-stu-id="075dc-139">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="075dc-140">IResourceResolver (замена IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="075dc-140">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="075dc-141">В версии 1.2 добавлена поддержка ResourceResolvers для средства визуализации Android.</span><span class="sxs-lookup"><span data-stu-id="075dc-141">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="075dc-142">Реализация сопоставителя ресурсов соответствует реализации IOnlineImageLoader. При этом ResourceResolver позволяет разработчику использовать одну карточку для разных способов получения изображений из любых источников. Это возможно путем связывания каждого ResourceResolver с уникальным префиксом, который запрашивается при попытке получить изображение.</span><span class="sxs-lookup"><span data-stu-id="075dc-142">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="075dc-143">ResourceResolver можно реализовать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="075dc-143">You can implement a ResourceResolver similar to this</span></span>

```java
public class ResourceResolver implements IResourceResolver
{
    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);
        byte[] decodedByteArray = Util.getBytes(decodedDataUri);
        bitmap = BitmapFactory.decodeByteArray(decodedByteArray, 0, decodedByteArray.length);

        return new HttpRequestResult<>(bitmap);
    }

    @Override
    public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
    {
        Bitmap bitmap;
        String dataUri = AdaptiveBase64Util.ExtractDataFromUri(uri);
        CharVector decodedDataUri = AdaptiveBase64Util.Decode(dataUri);

        if (uri.startsWith("data:image/svg")) {
            String svgString = AdaptiveBase64Util.ExtractDataFromUri(uri);
            String decodedSvgString = URLDecoder.decode(svgString, "UTF-8");
            Sharp sharp = Sharp.loadString(decodedSvgString);
            Drawable drawable = sharp.getDrawable();
            bitmap = ImageUtil.drawableToBitmap(drawable, maxWidth);
        }
        else
        {
            try
            {
                return genericImageLoaderAsync.loadDataUriImage(uri);
            }
            catch (Exception e)
            {
                return new HttpRequestResult<>(e);
            }
        }

        return new HttpRequestResult<>(bitmap);
    }
}
```

<span data-ttu-id="075dc-144">Как упоминалось ранее, можно зарегистрировать несколько экземпляров ResourceResolver. Сделать это можно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="075dc-144">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="075dc-145">Преобразование IOnlineImageLoader в IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="075dc-145">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="075dc-146">Преобразование IOnlineImageLoader в IResourceResolver — это довольно простая задача благодаря сходству методов.</span><span class="sxs-lookup"><span data-stu-id="075dc-146">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="075dc-147">Как можно видеть, наиболее существенными являются следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="075dc-147">As you can see, the biggest changes are</span></span>

* <span data-ttu-id="075dc-148">Параметр ```loadOnlineImage(String, GenericImageLoaderAsync)``` переименован в ```resolveImageResource(String, GenericImageLoaderAsync)```.</span><span class="sxs-lookup"><span data-stu-id="075dc-148">```loadOnlineImage(String, GenericImageLoaderAsync)``` was renamed to ```resolveImageResource(String, GenericImageLoaderAsync)```</span></span>
* <span data-ttu-id="075dc-149">перегрузка для ```resolveImageResource(String, GenericImageLoaderAsync)``` была добавлена как для ```resolveImageResource(String, GenericImageLoaderAsync, int)``` поддержки сценариев, в которых требуется максимальная ширина.</span><span class="sxs-lookup"><span data-stu-id="075dc-149">an overload for ```resolveImageResource(String, GenericImageLoaderAsync)``` was added as ```resolveImageResource(String, GenericImageLoaderAsync, int)``` in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="075dc-150">Пользовательская загрузка мультимедиа</span><span class="sxs-lookup"><span data-stu-id="075dc-150">Custom Media Loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="075dc-151">**```IOnlineMediaLoader```Необходимо помнить ```MediaDataSource``` , что было добавлено на уровне API 23 или Android M.**</span><span class="sxs-lookup"><span data-stu-id="075dc-151">**Remember ```IOnlineMediaLoader``` requires ```MediaDataSource``` which was added in API level 23 or Android M**</span></span>

<span data-ttu-id="075dc-152">Вместе с элементом мультимедиа был также добавлен интерфейс IOnlineMediaLoader, который позволяет разработчикам переопределять [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) базового элемента mediaPlayer.</span><span class="sxs-lookup"><span data-stu-id="075dc-152">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="075dc-153">**(Требуется Android M)**</span><span class="sxs-lookup"><span data-stu-id="075dc-153">**(Requires android M)**</span></span>

<span data-ttu-id="075dc-154">В первую очередь необходимо создать класс, реализующий IOnlineImageLoader.</span><span class="sxs-lookup"><span data-stu-id="075dc-154">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

```java
@RequiresApi(api = Build.VERSION_CODES.M)
public class OnlineMediaLoader implements IOnlineMediaLoader
{
    /* This class checks if the media source exists */
    public class OnlineFileAvailableChecker extends AsyncTask<String, Void, Boolean>
    {
        public OnlineFileAvailableChecker(String uri)
        {
            m_uri = uri;
        }

        @Override
        protected Boolean doInBackground(String... strings) {
            // if the provided uri is a valid uri or is valid with the resource resolver, then use that
            // otherwise, try to get the media from a local file
            try
            {
                HttpRequestHelper.query(m_uri);
                return true;
            }
            catch (Exception e)
            {
                // Do nothing if the media was not found at all
                e.printStackTrace();
                return false;
            }
        }

        private String m_uri;
   }

       
   @Override
   public MediaDataSource loadOnlineMedia(MediaSourceVector mediaSources, IMediaDataSourceOnPreparedListener mediaDataSourceOnPreparedListener)
   {
       final long mediaSourcesSize = mediaSources.size();
       for(int i = 0; i < mediaSourcesSize; i++)
       {
           String mediaUri = mediaSources.get(i).GetUrl();

           OnlineFileAvailableChecker checker = new OnlineFileAvailableChecker(mediaUri);
           try
           {
               Boolean fileExists = checker.execute("").get();
               if(fileExists)
               {
                   return new MediaDataSourceImpl(mediaUri, mediaDataSourceOnPreparedListener);
               }
           }
           catch (Exception e) { }
       }
       return null;
    }
}
```

<span data-ttu-id="075dc-155">После реализации этого класса можно зарегистрировать класс OnlineMediaLoader, добавив следующее:</span><span class="sxs-lookup"><span data-stu-id="075dc-155">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
