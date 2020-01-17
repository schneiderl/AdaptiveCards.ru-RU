---
title: Пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: ae5c1b2addf6fc5bcdda3defebb6de5925b58507
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145514"
---
# <a name="extensibility---android"></a>Расширяемость — Android

Модуль подготовки Android можно расширить для поддержки нескольких сценариев, в том числе:
* [Пользовательский синтаксический анализ элементов карточек](#custom-parsing-of-card-elements)
* [Пользовательская отрисовка элементов карточек](#custom-rendering-of-card-elements)
* [Пользовательская отрисовка действий](#custom-rendering-of-actions) (начиная с версии 1.2)
* [Пользовательская загрузка образа](#custom-image-loading) (начиная с v 1.0.1)
* [Пользовательская Загрузка носителя](#custom-media-loading) (начиная с версии 1.1)

## <a name="custom-parsing-of-card-elements"></a>Пользовательский анализ элементов карточки

Средство синтаксического анализа можно расширить, чтобы включить поддержку определяемых пользователем элементов карточки. Например, есть новый тип элемента, который выглядит так:
```json
{
    "type" : "MyType",
    "MyTypeData" : "My data"
}
```

Следующий пример демонстрирует, как преобразовать его в CardElement, который является расширением BaseCardElement:
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

Чтобы зарегистрировать средство синтаксического анализа и получить объект адаптивной карточки, который содержит пользовательский элемент, сделайте следующее:
```java
// Create an ElementParserRegistrationObject and add your parser to it
ElementParserRegistration elementParserRegistration = new ElementParserRegistration();
elementParserRegistration.AddParser("MyType", new MyCardElementParser());

AdaptiveCard adaptiveCard = AdaptiveCard.DeserializeFromString(jsonText, elementParserRegistration);
```

Далее рассматривается визуализация пользовательского элемента.

## <a name="custom-rendering-of-card-elements"></a>Пользовательская визуализация элементов карточки

> [!IMPORTANT]
>
> **Список критических изменений**
>
> [Критические изменения в версии 1.2](#breaking-changes-for-v12)

Чтобы определить собственный пользовательский модуль подготовки отчетов для нашего типа, сначала необходимо создать класс, который расширяется из ```BaseCardElementRenderer```:
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

Затем необходимо зарегистрировать средство визуализации следующим образом:
```java
CardRendererRegistration.getInstance().registerRenderer("MyType", new CustomBlahRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler,  hostConfig);
```

### <a name="breaking-changes-for-v12"></a>Критические изменения для версии 1.2

Метод ```render``` был изменен для включения параметра ```RenderedAdaptiveCard```, а ```ContainerStyle``` был изменен для Рендераргс, где Контаинерстиле теперь содержится, поэтому класс, расширяющий Басекарделементрендерер, должен выглядеть следующим образом.

```
public class MyCardElementRenderer extends BaseCardElementRenderer
{
    @Override
    public View render(RenderedAdaptiveCard renderedAdaptiveCard, Context context, FragmentManager fragmentManager, ViewGroup viewGroup,
                       BaseCardElement baseCardElement, ICardActionHandler cardActionHandler, HostConfig hostConfig, RenderArgs renderArgs)
    { }
}
```

## <a name="custom-parsing-of-card-actions"></a>Пользовательский анализ действий карточек

Аналогично анализу пользовательских элементов карт в версии 1.2 появилась возможность анализировать пользовательские действия. Например, предположим, что у нас есть новый тип действия, который выглядит следующим образом:
```json
{
    "type" : "MyAction",
    "ActionData" : "My data"
}
```

Затем в следующих строках показано, как проанализировать его в Актионелемент, который расширяется ```BaseActionElement```:
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

А в следующих строках показано, как зарегистрировать средство синтаксического анализа и получить объект Адаптивекард, содержащий элемент настраиваемого действия:
```java
// Create an ActionParserRegistration and add your parser to it
ActionParserRegistration actionParserRegistration = new ActionParserRegistration();
actionParserRegistration.AddParser(MyActionElement.MyActionId, new MyActionParser());

ParseContext context = new ParseContext(null, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

Далее идет подготовка настраиваемого действия к просмотру.

## <a name="custom-rendering-of-actions"></a>Пользовательская отрисовка действий

Чтобы определить собственный обработчик настраиваемых действий для нашего типа, сначала необходимо создать класс, который расширяется из ```BaseActionElementRenderer```:
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

Затем необходимо зарегистрировать средство визуализации следующим образом:
```java
CardRendererRegistration.getInstance().registerActionRenderer("myAction", new CustomActionRenderer());

RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
```

## <a name="custom-rendering-of-actions"></a>Пользовательская визуализация действий

> [!IMPORTANT]
> Реализация изменений в пользовательской визуализации действий, запланированная в версии 1.2, пока не завершена.

## <a name="custom-image-loading"></a>Пользовательская загрузка изображений

### <a name="ionlineimageloader"></a>IOnlineImageLoader

> [!IMPORTANT]
> **Зарегистрировать можно только IOnlineImageLoader с приоритетом над стандартным способом получения изображений**.

Мы добавили IOnlineImageLoader, чтобы разработчики могли извлекать изображения, не только скачивая или получая их из Интернета. Кроме того, им теперь не нужно выполнять предварительные действия для получения изображений. Для реализации OnlineImageLoader необходимо просто реализовать метод. 

```java
public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException
```

Ниже приведен пример OnlineImageLoader для изменения всех изображений, связанных с изображением кота.

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

Наконец, чтобы зарегистрировать этот загрузчик изображений, необходимо добавить в код следующую строку.

```java
CardRendererRegistration.getInstance().registerOnlineImageLoader(new OnlineImageLoader());
```

### <a name="iresourceresolver-deprecates-ionlineimageloader"></a>IResourceResolver (замена IOnlineImageLoader)

В версии 1.2 добавлена поддержка ResourceResolvers для средства визуализации Android. Реализация сопоставителя ресурсов соответствует реализации IOnlineImageLoader. При этом ResourceResolver позволяет разработчику использовать одну карточку для разных способов получения изображений из любых источников. Это возможно путем связывания каждого ResourceResolver с уникальным префиксом, который запрашивается при попытке получить изображение. 

ResourceResolver можно реализовать следующим образом:

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

Как упоминалось ранее, можно зарегистрировать несколько экземпляров ResourceResolver. Сделать это можно следующим образом:

```java
 CardRendererRegistration.getInstance().registerResourceResolver("data", new ResourceResolver());
 CardRendererRegistration.getInstance().registerResourceResolver("anotherPrefix", new AnotherResourceResolver());
```

#### <a name="transforming-an-ionlineimageloader-to-an-iresourceresolver"></a>Преобразование IOnlineImageLoader в IResourceResolver 

Преобразование IOnlineImageLoader в IResourceResolver — это довольно простая задача благодаря сходству методов.

```java
 // IOnlineImageLoader
 public HttpRequestResult<Bitmap> loadOnlineImage(String url, GenericImageLoaderAsync loader) throws IOException, URISyntaxException

 // IResourceResolver
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync) throws IOException, URISyntaxException
 public HttpRequestResult<Bitmap> resolveImageResource(String uri, GenericImageLoaderAsync genericImageLoaderAsync, int maxWidth) throws IOException, URISyntaxException
```

Как можно видеть, наиболее существенными являются следующие изменения:

* Параметр ```loadOnlineImage(String, GenericImageLoaderAsync)``` переименован в ```resolveImageResource(String, GenericImageLoaderAsync)```.
* перегрузка для ```resolveImageResource(String, GenericImageLoaderAsync)``` была добавлена как ```resolveImageResource(String, GenericImageLoaderAsync, int)``` для поддержки сценариев, в которых требуется максимальная ширина.

## <a name="custom-media-loading"></a>Пользовательская загрузка мультимедиа

> [!IMPORTANT]
> **Помните, ```IOnlineMediaLoader``` требует ```MediaDataSource```, который был добавлен на уровне API 23 или Android M.**

Вместе с элементом мультимедиа был также добавлен интерфейс IOnlineMediaLoader, который позволяет разработчикам переопределять [MediaDataSource](https://developer.android.com/reference/android/media/MediaDataSource) базового элемента mediaPlayer. **(Требуется Android M)**

В первую очередь необходимо создать класс, реализующий IOnlineImageLoader.

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

После реализации этого класса можно зарегистрировать класс OnlineMediaLoader, добавив следующее: 
```java
  CardRendererRegistration.getInstance().registerOnlineMediaLoader(new OnlineMediaLoader());
```
