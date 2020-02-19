---
title: ПАКЕТ SDK ДЛЯ .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 999f8ac3cd6a18fbbfc8b8bbdcf47465d8bb314f
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454287"
---
# <a name="getting-started---net-wpf"></a><span data-ttu-id="6b9db-102">Приступая к работе — .NET WPF</span><span class="sxs-lookup"><span data-stu-id="6b9db-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="6b9db-103">Как описано в [Начало работы](../../../authoring-cards/getting-started.md) странице, адаптивная карта является объектной моделью сериализованной карточки JSON.</span><span class="sxs-lookup"><span data-stu-id="6b9db-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="6b9db-104">Эта библиотека упрощает визуализацию JSON в пользовательском интерфейсе WPF, который можно использовать в приложении.</span><span class="sxs-lookup"><span data-stu-id="6b9db-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="6b9db-105">Установка NuGet</span><span class="sxs-lookup"><span data-stu-id="6b9db-105">NuGet install</span></span>

<span data-ttu-id="6b9db-106">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="6b9db-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="6b9db-107">Расширенный входной пакет ксцеед</span><span class="sxs-lookup"><span data-stu-id="6b9db-107">Xceed enhanced input package</span></span>

<span data-ttu-id="6b9db-108">Этот необязательный пакет расширяет возможности управления входными данными адаптивных карт, помимо того, что WPF предоставляет по своему желанию.</span><span class="sxs-lookup"><span data-stu-id="6b9db-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="6b9db-109">Он зависит от `Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="6b9db-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="6b9db-110">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="6b9db-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="6b9db-111">Пример визуализатора WPF</span><span class="sxs-lookup"><span data-stu-id="6b9db-111">WPF Visualizer Sample</span></span>

![Снимок экрана визуализатора](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="6b9db-113">[Пример визуализатора WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карты с помощью WPF.</span><span class="sxs-lookup"><span data-stu-id="6b9db-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="6b9db-114">Доступен встроенный редактор `Host Config`, в котором можно редактировать и просматривать параметры HostConfig.</span><span class="sxs-lookup"><span data-stu-id="6b9db-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="6b9db-115">Сохраните эти параметры в JSON-файл, чтобы использовать их для отрисовки в своем приложении.</span><span class="sxs-lookup"><span data-stu-id="6b9db-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6b9db-116">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="6b9db-116">Next steps</span></span>

<span data-ttu-id="6b9db-117">См. подробнее о [визуализации карточек](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="6b9db-117">See [Render a card](render-a-card.md) for the next steps!</span></span>
