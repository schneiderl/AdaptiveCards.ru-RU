---
title: Класс Адаптивекардрендерер — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: c90fb22f60fa75a37b6372c2660f8599535fd961
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146068"
---
# <a name="adaptivecardrenderer"></a><span data-ttu-id="08794-102">адаптивекардрендерер</span><span class="sxs-lookup"><span data-stu-id="08794-102">AdaptiveCardRenderer</span></span>

```csharp
public class AdaptiveCardRenderer : global::Java.Lang.Object
```

<span data-ttu-id="08794-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="08794-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a><span data-ttu-id="08794-104">Сводка</span><span class="sxs-lookup"><span data-stu-id="08794-104">Summary</span></span>

| <span data-ttu-id="08794-105">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="08794-105">Public methods</span></span> | |
| --- | ---- |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler)```](#render0) |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler, HostConfig hostConfig)```](#render1) |

## <a name="public-methods"></a><span data-ttu-id="08794-106">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="08794-106">Public Methods</span></span>

---

### <a id="render0"></a><span data-ttu-id="08794-107">Обрабатывает</span><span class="sxs-lookup"><span data-stu-id="08794-107">Render</span></span>
<p style='text-align:right'><span data-ttu-id="08794-108">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="08794-108">Added in version 0.1.0</span></span></p>

```csharp
public RenderedAdaptiveCard Render (Context context, 
                                    FragmentManager fragmentManager, 
                                    AdaptiveCard adaptiveCard,
                                    ICardActionHandler cardActionHandler)
```

<span data-ttu-id="08794-109">Отображает указанную адаптивную карту со значениями по умолчанию для конфигурации узла.</span><span class="sxs-lookup"><span data-stu-id="08794-109">Renders the specified adaptive card with default values for the host config.</span></span>

| <span data-ttu-id="08794-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="08794-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="08794-111">context</span><span class="sxs-lookup"><span data-stu-id="08794-111">context</span></span> | ```Android.Content.Context``` |
| <span data-ttu-id="08794-112">фрагментманажер</span><span class="sxs-lookup"><span data-stu-id="08794-112">fragmentManager</span></span> | ```Android.Support.V4.App.FragmentManager``` |
| <span data-ttu-id="08794-113">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="08794-113">adaptiveCard</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md) |
| <span data-ttu-id="08794-114">кардактионхандлер</span><span class="sxs-lookup"><span data-stu-id="08794-114">cardActionHandler</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) |

| <span data-ttu-id="08794-115">Возвращает</span><span class="sxs-lookup"><span data-stu-id="08794-115">Returns</span></span> |
| --- | --- |
| [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) | |

#### <a name="sample"></a><span data-ttu-id="08794-116">Пример</span><span class="sxs-lookup"><span data-stu-id="08794-116">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler);
```

---

### <a id="render1"></a><span data-ttu-id="08794-117">Обрабатывает</span><span class="sxs-lookup"><span data-stu-id="08794-117">Render</span></span>
<p style='text-align:right'><span data-ttu-id="08794-118">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="08794-118">Added in version 0.1.0</span></span></p>

```csharp
RenderedAdaptiveCard Render (Context context, 
                            FragmentManager fragmentManager, 
                            AdaptiveCard adaptiveCard, 
                            ICardActionHandler cardActionHandler, 
                            HostConfig hostConfig)
```

<span data-ttu-id="08794-119">Отображает указанную адаптивную карту с использованием заданного файла конфигурации узла.</span><span class="sxs-lookup"><span data-stu-id="08794-119">Renders the specified adaptive card with using the given host config.</span></span>

| <span data-ttu-id="08794-120">Параметры</span><span class="sxs-lookup"><span data-stu-id="08794-120">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="08794-121">context</span><span class="sxs-lookup"><span data-stu-id="08794-121">context</span></span> | ```Android.Content.Context``` |
| <span data-ttu-id="08794-122">фрагментманажер</span><span class="sxs-lookup"><span data-stu-id="08794-122">fragmentManager</span></span> | ```Android.Support.V4.App.FragmentManager``` |
| <span data-ttu-id="08794-123">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="08794-123">adaptiveCard</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md) |
| <span data-ttu-id="08794-124">кардактионхандлер</span><span class="sxs-lookup"><span data-stu-id="08794-124">cardActionHandler</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) |
| <span data-ttu-id="08794-125">хостконфиг</span><span class="sxs-lookup"><span data-stu-id="08794-125">hostConfig</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HostConfig``` |

| <span data-ttu-id="08794-126">Возвращает</span><span class="sxs-lookup"><span data-stu-id="08794-126">Returns</span></span> | |
| --- | --- |
| [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) | |

#### <a name="sample"></a><span data-ttu-id="08794-127">Пример</span><span class="sxs-lookup"><span data-stu-id="08794-127">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler, hostConfig);
```