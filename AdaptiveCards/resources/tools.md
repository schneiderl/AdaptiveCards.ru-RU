---
title: Средства адаптивной карты
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 35ce89653a6cf2a313518be0f221a166e1eb7711
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552506"
---
# <a name="card-designer"></a><span data-ttu-id="2de64-102">Конструктор карточек</span><span class="sxs-lookup"><span data-stu-id="2de64-102">Card Designer</span></span> 

<span data-ttu-id="2de64-103">Необходимости в средстве для разработки карт?</span><span class="sxs-lookup"><span data-stu-id="2de64-103">Need for a tool to design your cards?</span></span> <span data-ttu-id="2de64-104">Нет ничего лучше конструктор на основе веб-обозревателя инструмент adaptive Cards в [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="2de64-104">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="2de64-105">[![Снимок экрана конструктора](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="2de64-105">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

## <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="2de64-106">Внедрение конструктора в приложении</span><span class="sxs-lookup"><span data-stu-id="2de64-106">Embed the designer into your app</span></span>

<span data-ttu-id="2de64-107">Но почему отправить этим пользователям существует в том случае, когда вы можете **внедрять конструкторе карты непосредственно в веб-** приложения с помощью нашей библиотеке JavaScript.</span><span class="sxs-lookup"><span data-stu-id="2de64-107">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="2de64-108">Ознакомьтесь с [adaptivecards конструктор](https://npmjs.com/adaptivecards-designer) пакета, чтобы приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="2de64-108">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

# <a name="schema-validation"></a><span data-ttu-id="2de64-109">Проверка схемы</span><span class="sxs-lookup"><span data-stu-id="2de64-109">Schema validation</span></span>

<span data-ttu-id="2de64-110">Проверка схемы — это эффективное средство, упрощает создание и включение средств.</span><span class="sxs-lookup"><span data-stu-id="2de64-110">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

## <a name="json-schema"></a><span data-ttu-id="2de64-111">Схема JSON</span><span class="sxs-lookup"><span data-stu-id="2de64-111">JSON Schema</span></span>
<span data-ttu-id="2de64-112">Мы предоставили полный [файла схемы JSON](http://adaptivecards.io/schemas/adaptive-card.json) для редактирования и проверке адаптивной карты в формате json.</span><span class="sxs-lookup"><span data-stu-id="2de64-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/adaptive-card.json) for editing and validating adaptive cards in json.</span></span>

<span data-ttu-id="2de64-113">В Visual Studio и Visual Studio Code можно получить автоматическое Intellisense, включая `$schema` ссылки.</span><span class="sxs-lookup"><span data-stu-id="2de64-113">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![Неправильный](media/tools/invalidjson1.png)

![Автозаполнение](media/tools/autocomplete.png)

### <a name="example"></a><span data-ttu-id="2de64-116">Пример</span><span class="sxs-lookup"><span data-stu-id="2de64-116">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "0.5",
    "body": []
}
```

# <a name="tools-and-samples"></a><span data-ttu-id="2de64-117">Средства и примеры</span><span class="sxs-lookup"><span data-stu-id="2de64-117">Tools and samples</span></span>
<span data-ttu-id="2de64-118">Существует несколько средств и примеров в дереве исходного кода, которые полезные ссылки, а также полезные средства.</span><span class="sxs-lookup"><span data-stu-id="2de64-118">There are some tools and samples in the source tree which are useful references as well as useful tools.</span></span>

## <a name="visual-studio-code-extension"></a><span data-ttu-id="2de64-119">Расширение Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2de64-119">Visual Studio Code Extension</span></span>
<span data-ttu-id="2de64-120">Мы создали расширение Visual Studio code, который позволяет визуализировать карты, редактируемого в режиме реального времени в самом редакторе.</span><span class="sxs-lookup"><span data-stu-id="2de64-120">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![Расширение](media/tools/vscode-extension.png)

<span data-ttu-id="2de64-122">Чтобы установить, откройте расширения Marketplace и выполните поиск **адаптивные средства просмотра карты**.</span><span class="sxs-lookup"><span data-stu-id="2de64-122">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![магазин](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="2de64-124">Использование</span><span class="sxs-lookup"><span data-stu-id="2de64-124">Usage</span></span>

<span data-ttu-id="2de64-125">При редактировании JSON-файл с инструмент Adaptive Cards `$schema` свойство, можно просмотреть с помощью `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="2de64-125">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="2de64-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="2de64-126">Options</span></span>

<span data-ttu-id="2de64-127">Следующий параметр Visual Studio Code доступен для средства просмотра AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="2de64-127">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="2de64-128">Это можно задать в параметрах пользователя или параметры рабочей области.</span><span class="sxs-lookup"><span data-stu-id="2de64-128">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="2de64-129">Пример визуализатора WPF</span><span class="sxs-lookup"><span data-stu-id="2de64-129">WPF Visualizer Sample</span></span>
<span data-ttu-id="2de64-130">[Пример проекта визуализатор WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карты, использующие WPF/Xaml на компьютере Windows.</span><span class="sxs-lookup"><span data-stu-id="2de64-130">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="2de64-131">Объект `hostconfig` встроенной в редактор для редактирования и просмотра параметров конфигурации узла.</span><span class="sxs-lookup"><span data-stu-id="2de64-131">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="2de64-132">Сохраните эти параметры в формате JSON, чтобы использовать их при подготовке к просмотру в приложении.</span><span class="sxs-lookup"><span data-stu-id="2de64-132">Save these settings as a JSON to use them in rendering in your application.</span></span>

![визуализатор WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="2de64-134">Пример ImageRender WPF</span><span class="sxs-lookup"><span data-stu-id="2de64-134">WPF ImageRender Sample</span></span>
<span data-ttu-id="2de64-135">[ImageRender пример проекта](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) превращает всех карт в PNG из командной строки с помощью WPF.</span><span class="sxs-lookup"><span data-stu-id="2de64-135">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
