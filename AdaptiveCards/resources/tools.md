---
title: Инструменты адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 819788313d78b4057fb5d3dc4d5a9be658566642
ms.sourcegitcommit: 996fc604e59f72ba1dd96c29f4b517862a5264e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87566028"
---
# <a name="tools-and-samples"></a><span data-ttu-id="8e018-102">Инструменты и примеры</span><span class="sxs-lookup"><span data-stu-id="8e018-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="8e018-103">Конструктор карточек</span><span class="sxs-lookup"><span data-stu-id="8e018-103">Card Designer</span></span> 

<span data-ttu-id="8e018-104">Вам нужен инструмент для проектирования карточек?</span><span class="sxs-lookup"><span data-stu-id="8e018-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="8e018-105">Можете больше не искать! Вот удобный браузерный конструктор адаптивных карточек: [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="8e018-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="8e018-106">[![снимок экрана конструктора](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="8e018-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="8e018-107">Внедрение конструктора в приложение</span><span class="sxs-lookup"><span data-stu-id="8e018-107">Embed the designer into your app</span></span>

<span data-ttu-id="8e018-108">Но зачем отправлять пользователей куда-то, если можно **внедрить конструктор карточек непосредственно в свое веб-приложение** с помощью нашей библиотеки JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8e018-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="8e018-109">Чтобы приступить к работе, ознакомьтесь с пакетом [adaptivecards-designer](https://npmjs.com/adaptivecards-designer).</span><span class="sxs-lookup"><span data-stu-id="8e018-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="8e018-110">Проверка схемы</span><span class="sxs-lookup"><span data-stu-id="8e018-110">Schema validation</span></span>

<span data-ttu-id="8e018-111">Проверка схемы — это эффективный способ упрощения процесса разработки и добавления инструментов.</span><span class="sxs-lookup"><span data-stu-id="8e018-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="8e018-112">Мы предоставили полный [JSON-файл](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) для редактирования и проверки адаптивных карт на основе JSON.</span><span class="sxs-lookup"><span data-stu-id="8e018-112">We have provided a complete [JSON Schema file](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="8e018-113">Обратите внимание на то, что URL-адрес схемы соответствует версии, поэтому более новые версии адаптивных карточек будут иметь соответствующий URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="8e018-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="8e018-114">В Visual Studio и Visual Studio Code можно включить автоматическую функцию IntelliSense, добавив ссылку `$schema`.</span><span class="sxs-lookup"><span data-stu-id="8e018-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![Неправильное значение](media/tools/invalidjson1.png)

![Автозаполнение](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="8e018-117">Пример</span><span class="sxs-lookup"><span data-stu-id="8e018-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extensions"></a><span data-ttu-id="8e018-118">Расширения Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8e018-118">Visual Studio Code Extensions</span></span>

### <a name="adaptive-cards-studio"></a><span data-ttu-id="8e018-119">**Студия адаптивных карточек**</span><span class="sxs-lookup"><span data-stu-id="8e018-119">**Adaptive Cards Studio**</span></span>

![магазин](https://madewithcards.blob.core.windows.net/uploads/29bb3d02-2158-40b8-8420-4dd1f15da34c-acstudio.png)

<span data-ttu-id="8e018-121">С помощью Студии адаптивных карточек можно создавать карточки непосредственно в Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8e018-121">With AdaptiveCards Studio you can author cards directly in Visual Studio Code.</span></span> <span data-ttu-id="8e018-122">Расширение автоматически обнаруживает все адаптивные карточки в рабочем пространстве и позволяет легко изменять шаблон карточки, а также примеры данных.</span><span class="sxs-lookup"><span data-stu-id="8e018-122">The Extension automatically detects all Adaptive Cards in your working space and lets you easily edit the card template and sample data.</span></span>

[<span data-ttu-id="8e018-123">Дополнительные сведения и установка из Visual Studio Code Marketplace</span><span class="sxs-lookup"><span data-stu-id="8e018-123">Read more and install it from the Visual Studio Code Marketplace</span></span>](https://marketplace.visualstudio.com/items?itemName=madewithcardsio.adaptivecardsstudiobeta)


### <a name="adaptive-card-viewer"></a><span data-ttu-id="8e018-124">**Средство просмотра адаптивных карточек**</span><span class="sxs-lookup"><span data-stu-id="8e018-124">**Adaptive Card Viewer**</span></span>

<span data-ttu-id="8e018-125">Мы создали расширение Visual Studio Code, которое позволяет визуализировать редактируемую карту в реальном времени в самом редакторе.</span><span class="sxs-lookup"><span data-stu-id="8e018-125">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![Расширение](media/tools/vscode-extension.png)

<span data-ttu-id="8e018-127">Чтобы установить его, откройте Marketplace для расширений и выполните поиск **Adaptive Card Viewer**.</span><span class="sxs-lookup"><span data-stu-id="8e018-127">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![магазин](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="8e018-129">Использование</span><span class="sxs-lookup"><span data-stu-id="8e018-129">Usage</span></span>

<span data-ttu-id="8e018-130">При редактировании JSON-файла со свойством адаптивной карточки `$schema` его можно просмотреть с помощью `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="8e018-130">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="8e018-131">Параметры</span><span class="sxs-lookup"><span data-stu-id="8e018-131">Options</span></span>

<span data-ttu-id="8e018-132">Следующий параметр Visual Studio Code доступен для Adaptive Card Viewer.</span><span class="sxs-lookup"><span data-stu-id="8e018-132">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="8e018-133">Его можно задать в разделе "Параметры пользователя" или "Параметры рабочей области".</span><span class="sxs-lookup"><span data-stu-id="8e018-133">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="8e018-134">Пример визуализатора WPF</span><span class="sxs-lookup"><span data-stu-id="8e018-134">WPF Visualizer Sample</span></span>

<span data-ttu-id="8e018-135">[Пример проекта визуализатора WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карточки с использованием WPF или XAML на компьютере с Windows.</span><span class="sxs-lookup"><span data-stu-id="8e018-135">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="8e018-136">Доступен встроенный редактор `hostconfig`, в котором можно редактировать и просматривать параметры HostConfig.</span><span class="sxs-lookup"><span data-stu-id="8e018-136">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="8e018-137">Сохраните эти параметры в JSON-файл, чтобы использовать их для отрисовки в своем приложении.</span><span class="sxs-lookup"><span data-stu-id="8e018-137">Save these settings as a JSON to use them in rendering in your application.</span></span>

![Визуализатор WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="8e018-139">Пример ImageRender для WPF</span><span class="sxs-lookup"><span data-stu-id="8e018-139">WPF ImageRender Sample</span></span>

<span data-ttu-id="8e018-140">[Пример проекта ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) превращает любую карточку в PNG-файл из командной строки с помощью WPF.</span><span class="sxs-lookup"><span data-stu-id="8e018-140">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
