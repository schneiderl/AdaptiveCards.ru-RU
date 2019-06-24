---
title: Пакет SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 378171186599dd8d103111da183b7fc2e6e01c42
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134263"
---
# <a name="extensibility---android"></a><span data-ttu-id="d255f-102">Расширяемость — Android</span><span class="sxs-lookup"><span data-stu-id="d255f-102">Extensibility - Android</span></span>

## <a name="custom-parsing-of-card-elements"></a><span data-ttu-id="d255f-103">Пользовательский анализ элементов карточки</span><span class="sxs-lookup"><span data-stu-id="d255f-103">Custom Parsing of Card Elements</span></span>

<span data-ttu-id="d255f-104">Средство синтаксического анализа можно расширить, чтобы включить поддержку определяемых пользователем элементов карточки.</span><span class="sxs-lookup"><span data-stu-id="d255f-104">You may extend the parser to support card elements that you have defined.</span></span> <span data-ttu-id="d255f-105">Например, есть новый тип элемента, который выглядит так:</span><span class="sxs-lookup"><span data-stu-id="d255f-105">For example, say we have a new element type that looks like this:</span></span>
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

<span data-ttu-id="d255f-106">Следующий пример демонстрирует, как преобразовать его в CardElement, который является расширением BaseCardElement:</span><span class="sxs-lookup"><span data-stu-id="d255f-106">Then the following lines demonstrate how to parse it into a CardElement that extends from the BaseCardElement:</span></span>
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

<span data-ttu-id="d255f-107">Чтобы зарегистрировать средство синтаксического анализа и получить объект адаптивной карточки, который содержит пользовательский элемент, сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="d255f-107">And this is how to register the parser and get an AdaptiveCard object that contains the custom element:</span></span>
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

<span data-ttu-id="d255f-108">Далее рассматривается визуализация пользовательского элемента.</span><span class="sxs-lookup"><span data-stu-id="d255f-108">Next comes rendering the custom element</span></span>

## <a name="custom-rendering-of-card-elements"></a><span data-ttu-id="d255f-109">Пользовательская визуализация элементов карточки</span><span class="sxs-lookup"><span data-stu-id="d255f-109">Custom Rendering of Card Elements</span></span>

<span data-ttu-id="d255f-110">Чтобы определить пользовательское средство визуализации для нашего типа, сначала нужно создать класс, полученный из BaseCardElementParser:</span><span class="sxs-lookup"><span data-stu-id="d255f-110">To define our own custom renderer for our type, we must first create a class that extends from BaseCardElementParser:</span></span>
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

<span data-ttu-id="d255f-111">Затем необходимо зарегистрировать средство визуализации следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d255f-111">We then register this renderer like so:</span></span>
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
```

## <a name="custom-rendering-of-actions"></a><span data-ttu-id="d255f-112">Пользовательская визуализация действий</span><span class="sxs-lookup"><span data-stu-id="d255f-112">Custom rendering of actions</span></span>

[!IMPORTANT]
> <span data-ttu-id="d255f-113">Реализация изменений в пользовательской визуализации действий, запланированная в версии 1.2, пока не завершена.</span><span class="sxs-lookup"><span data-stu-id="d255f-113">Changes to the custom rendering of actions are planned for v1.2 but are not completed yet</span></span>

## <a name="custom-image-loading"></a><span data-ttu-id="d255f-114">Пользовательская загрузка изображений</span><span class="sxs-lookup"><span data-stu-id="d255f-114">Custom image loading</span></span>

### <a name="ionlineimageloader"></a><span data-ttu-id="d255f-115">IOnlineImageLoader</span><span class="sxs-lookup"><span data-stu-id="d255f-115">IOnlineImageLoader</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d255f-116">**Зарегистрировать можно только IOnlineImageLoader с приоритетом над стандартным способом получения изображений**.</span><span class="sxs-lookup"><span data-stu-id="d255f-116">**Only one IOnlineImageLoader can be registered and it takes precedence against the default way of retrieving images**</span></span>

<span data-ttu-id="d255f-117">Мы добавили IOnlineImageLoader, чтобы разработчики могли извлекать изображения, не только скачивая или получая их из Интернета. Кроме того, им теперь не нужно выполнять предварительные действия для получения изображений.</span><span class="sxs-lookup"><span data-stu-id="d255f-117">In order to allow developers to get images that could not just be downloaded or retrieved from an online source or required previous steps before they could be retrieved, the IOnlineImageLoader was added to solve this kind of situations.</span></span> <span data-ttu-id="d255f-118">Для реализации OnlineImageLoader необходимо просто реализовать метод.</span><span class="sxs-lookup"><span data-stu-id="d255f-118">To implement an OnlineImageLoader you must only implement the method</span></span> 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

<span data-ttu-id="d255f-119">Ниже приведен пример OnlineImageLoader для изменения всех изображений, связанных с изображением кота.</span><span class="sxs-lookup"><span data-stu-id="d255f-119">Here's an example of an OnlineImageLoader which changes all images for a cat image</span></span>

```java
public class OnlineImageLoader implements IOnlineImageLoader
{
    public OnlineImageLoader(){}

    @Override
    public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
    {
        String catImnageUri = "http://adaptivecards.io/content/cats/1.png";
        byte[] bytes = HttpRequestHelper.get(catImnageUri);
        if (bytes == null)
        {
            throw new IOException("Failed to retrieve content from " + catImnageUri);
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

<span data-ttu-id="d255f-120">Наконец, чтобы зарегистрировать этот загрузчик изображений, необходимо добавить в код следующую строку.</span><span class="sxs-lookup"><span data-stu-id="d255f-120">Finally, to register this image loader, you must only add this line to your code.</span></span>

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a><span data-ttu-id="d255f-121">IResourceResolver (замена IOnlineImageLoader)</span><span class="sxs-lookup"><span data-stu-id="d255f-121">IResourceResolver (deprecates IOnlineImageLoader)</span></span>

<span data-ttu-id="d255f-122">В версии 1.2 добавлена поддержка ResourceResolvers для средства визуализации Android.</span><span class="sxs-lookup"><span data-stu-id="d255f-122">For v1.2, the support for full ResourceResolvers was added to the android renderer.</span></span> <span data-ttu-id="d255f-123">Реализация сопоставителя ресурсов соответствует реализации IOnlineImageLoader. При этом ResourceResolver позволяет разработчику использовать одну карточку для разных способов получения изображений из любых источников. Это возможно путем связывания каждого ResourceResolver с уникальным префиксом, который запрашивается при попытке получить изображение.</span><span class="sxs-lookup"><span data-stu-id="d255f-123">The implementation of a resource resolver is really similar to that of a IOnlineImageLoader but having ResourceResolvers allows a developer to add multiple ways to retrieve images from any kind of source in a single card, this is done by linking each ResourceResolver to a unique prefix which will be queried when trying to retrieve an image.</span></span> 

<span data-ttu-id="d255f-124">ResourceResolver можно реализовать следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d255f-124">You can implement a ResourceResolver similar to this</span></span>

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

<span data-ttu-id="d255f-125">Как упоминалось ранее, можно зарегистрировать несколько экземпляров ResourceResolver. Сделать это можно следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d255f-125">As mentioned previously, you can register multiple ResourceResolvers, to register a ResourceResolver you can do this</span></span>

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a><span data-ttu-id="d255f-126">Преобразование IOnlineImageLoader в IResourceResolver</span><span class="sxs-lookup"><span data-stu-id="d255f-126">Transforming an IOnlineImageLoader to an IResourceResolver</span></span> 

<span data-ttu-id="d255f-127">Преобразование IOnlineImageLoader в IResourceResolver — это довольно простая задача благодаря сходству методов.</span><span class="sxs-lookup"><span data-stu-id="d255f-127">Transforming an IOnlineImageLoader to an IResourceResolver is a fairly easy task as the methods for the latter were tried to keep as similar as the IOnlineImageLoader as possible</span></span>

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

<span data-ttu-id="d255f-128">Как можно видеть, наиболее существенными являются следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="d255f-128">As you can see, the biggest changes are</span></span>
* <span data-ttu-id="d255f-129">мы переименовали loadOnlineImage (String, GenericImageLoaderAsync) в resolveImageResource (String, GenericImageLoaderAsync);</span><span class="sxs-lookup"><span data-stu-id="d255f-129">loadOnlineImage(String, GenericImageLoaderAsync) was renamed to resolveImageResource(String, GenericImageLoaderAsync)</span></span>
* <span data-ttu-id="d255f-130">для resolveImageResource (String, GenericImageLoaderAsync) добавлена перегрузка в виде (String, GenericImageLoaderAsync, int) для поддержки сценариев, в которых требуется максимальная ширина.</span><span class="sxs-lookup"><span data-stu-id="d255f-130">an overload for resolveImageResource(String, GenericImageLoaderAsync) was added as resolveImageResource(String, GenericImageLoaderAsync, int) in order to support scenarios where the max width is required</span></span>

## <a name="custom-media-loading"></a><span data-ttu-id="d255f-131">Пользовательская загрузка мультимедиа</span><span class="sxs-lookup"><span data-stu-id="d255f-131">Custom media loading</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d255f-132">**Обратите внимание, что IOnlineMediaLoader, требующий MediaDataSource, был добавлен в уровень API 23 и Android M**.</span><span class="sxs-lookup"><span data-stu-id="d255f-132">**Remember IOnlineMediaLoader requires MediaDataSource was added in API level 23 or Android M**</span></span>

<span data-ttu-id="d255f-133">Вместе с элементом мультимедиа был также добавлен интерфейс IOnlineMediaLoader, который позволяет разработчикам переопределять [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) базового элемента mediaPlayer.</span><span class="sxs-lookup"><span data-stu-id="d255f-133">Along with the inclusion of the media element, also was the inclusion of the IOnlineMediaLoader interface which allows developers to override the [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) used for the underlying mediaPlayer element.</span></span> <span data-ttu-id="d255f-134">**(Требуется Android M)**</span><span class="sxs-lookup"><span data-stu-id="d255f-134">**(Requires android M)**</span></span>

<span data-ttu-id="d255f-135">В первую очередь необходимо создать класс, реализующий IOnlineImageLoader.</span><span class="sxs-lookup"><span data-stu-id="d255f-135">The first needed thing to do is creating a class that implements IOnlineImageLoader</span></span>

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

<span data-ttu-id="d255f-136">После реализации этого класса можно зарегистрировать класс OnlineMediaLoader, добавив следующее:</span><span class="sxs-lookup"><span data-stu-id="d255f-136">Once this class has been implemented, you can register your OnlineMediaLoader class by adding</span></span> 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
