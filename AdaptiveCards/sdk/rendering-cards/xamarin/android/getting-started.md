---
title: Пакет SDK Xamarin.Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: cd8dccd2aece23dd67ee8d601e8efaa2a1bcd4f2
ms.sourcegitcommit: 588f3e97ed3de96dfff54906ac666ce42ef1e7f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928834"
---
# <a name="getting-started---xamarinandroid"></a><span data-ttu-id="2ed94-102">Начало работы — Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="2ed94-102">Getting started - Xamarin.Android</span></span>

<span data-ttu-id="2ed94-103">Это библиотека модуля подготовки отчетов, предназначенная для собственных приложений Xamarin Android и основанная на модуле подготовки Android, который можно найти [здесь](../../android/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="2ed94-103">This is a renderer library which targets native xamarin android applications and is based on the Android renderer that you can find [here](../../android/getting-started.md).</span></span> 

## <a name="nuget-install"></a><span data-ttu-id="2ed94-104">Установка NuGet</span><span class="sxs-lookup"><span data-stu-id="2ed94-104">NuGet install</span></span>

<span data-ttu-id="2ed94-105">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)</span><span class="sxs-lookup"><span data-stu-id="2ed94-105">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)</span></span>

<span data-ttu-id="2ed94-106">Опубликованные пакеты можно найти [здесь](http://nuget.org) .</span><span class="sxs-lookup"><span data-stu-id="2ed94-106">You can find the published packages [here](http://nuget.org)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## <a name="namespace"></a><span data-ttu-id="2ed94-107">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="2ed94-107">Namespace</span></span>

<span data-ttu-id="2ed94-108">Необходимые пространства имен для использования этой библиотеки</span><span class="sxs-lookup"><span data-stu-id="2ed94-108">The necessary namespaces for using this library are</span></span>
```csharp
// To import the base object model classes as AdaptiveCard, TextBlock, Column, ShowCardAction, ...
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;

// To import the AdaptiveCardRenderer class
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;

// To import the ICardActionHandler interface
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;

// To use feature registration and register custom behaviour 
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration;
```

## <a name="xamarinandroid-visualizer-sample"></a><span data-ttu-id="2ed94-109">Пример визуализатора Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="2ed94-109">Xamarin.Android Visualizer Sample</span></span>

<span data-ttu-id="2ed94-110">[Пример визуализатора Xamarin. Android](https://github.com/Microsoft/AdaptiveCards/tree/main/source/xamarin/Xamarin.Droid.Sample) позволяет визуализировать карты с помощью Xamarin. Android.</span><span class="sxs-lookup"><span data-stu-id="2ed94-110">The [Xamarin.Android Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/main/source/xamarin/Xamarin.Droid.Sample) lets you visualize cards using Xamarin.Android.</span></span> <span data-ttu-id="2ed94-111">Если вы когда-либо использовали пример приложения для Android, вы увидите, что он действительно похож.</span><span class="sxs-lookup"><span data-stu-id="2ed94-111">If you have ever used the Android sample application you'll find the experience to be really similar.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ed94-112">Дальнейшие шаги</span><span class="sxs-lookup"><span data-stu-id="2ed94-112">Next steps</span></span>

<span data-ttu-id="2ed94-113">Для быстрого начала проверьте [Отображение карты](render-a-card.md) для следующих шагов.</span><span class="sxs-lookup"><span data-stu-id="2ed94-113">For a quick start check [Render a card](render-a-card.md) for the next steps!</span></span>

<span data-ttu-id="2ed94-114">Чтобы получить более подробные сведения о классах, привязанных к библиотеке модуля подготовки отчетов Xamarin. Android, можно проверить некоторые связываемые классы, щелкнув их ниже:</span><span class="sxs-lookup"><span data-stu-id="2ed94-114">For a more in depth view of the classes that have been binded for the Xamarin.Android renderer library, you can check some of the binded classes by clicking on them below:</span></span>
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)
