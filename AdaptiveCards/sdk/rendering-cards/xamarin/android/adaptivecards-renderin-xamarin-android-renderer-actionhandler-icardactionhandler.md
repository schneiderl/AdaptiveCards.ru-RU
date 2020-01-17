---
title: Класс Икардактионхандлер — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 8b526ccb66be3a261384d6c4f68a850558e2549e
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146158"
---
# <a name="icardactionhandler"></a><span data-ttu-id="9bef1-102">икардактионхандлер</span><span class="sxs-lookup"><span data-stu-id="9bef1-102">ICardActionHandler</span></span>

```csharp
public interface ICardActionHandler : IJavaObject 
```

<span data-ttu-id="9bef1-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="9bef1-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler
```

### <a name="summary"></a><span data-ttu-id="9bef1-104">Сводка</span><span class="sxs-lookup"><span data-stu-id="9bef1-104">Summary</span></span>

| <span data-ttu-id="9bef1-105">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="9bef1-105">Public methods</span></span> | |
| --- | ---- |
| ```abstract void``` | [```OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)```](#onaction) |
| ```abstract void``` | [```OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)```](#onmediaplay) |
| ```abstract void``` | [```OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)```](#onmediastop) |

## <a name="public-methods"></a><span data-ttu-id="9bef1-106">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="9bef1-106">Public Methods</span></span>
--- 
### <a id="onaction"></a><span data-ttu-id="9bef1-107">OnAction</span><span class="sxs-lookup"><span data-stu-id="9bef1-107">OnAction</span></span>
<p style='text-align:right'><span data-ttu-id="9bef1-108">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="9bef1-108">Added in version 0.1.0</span></span></p>

```csharp
void OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)
```

<span data-ttu-id="9bef1-109">Прослушиватель вызывается при щелчке Опенурлактион, Субмитактион или Шовкардактион (если не встроено).</span><span class="sxs-lookup"><span data-stu-id="9bef1-109">Listener called when a OpenUrlAction, SubmitAction or ShowCardAction (if not inline) are clicked.</span></span>

| <span data-ttu-id="9bef1-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="9bef1-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="9bef1-111">P0</span><span class="sxs-lookup"><span data-stu-id="9bef1-111">p0</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElement``` |
| <span data-ttu-id="9bef1-112">ниже</span><span class="sxs-lookup"><span data-stu-id="9bef1-112">p1</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) |

#### <a name="sample"></a><span data-ttu-id="9bef1-113">Пример</span><span class="sxs-lookup"><span data-stu-id="9bef1-113">Sample</span></span>

```csharp
public class MyCardActionHandler : ICardActionHandler
{

    public void OnAction(BaseActionElement element, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = element.ElementType;
        if (actionType == ActionType.Submit)
        {
            var inputs = renderedCard.Inputs;
            string inputValues = string.Empty;
            foreach (var inputString in inputs)
            {
                inputValues += $"{{{inputString.Key} : {inputString.Value}}}\n";
            }
            submitData(inputValues);
        }
        else if (actionType == ActionType.ShowCard)
        {
            var showcardAction = ShowCardAction.Dynamic_cast(element);
            showCard(showcardAction.Card)
        }
        else if (actionType == ActionType.OpenUrl)
        {
            var openUrlAction = OpenUrlAction.Dynamic_cast(element);
            openUrl(openUrlAction.Url);
        }
    }
}
```

---
### <a id="onmediaplay"></a><span data-ttu-id="9bef1-114">онмедиаплай</span><span class="sxs-lookup"><span data-stu-id="9bef1-114">OnMediaPlay</span></span>
<p style='text-align:right'><span data-ttu-id="9bef1-115">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="9bef1-115">Added in version 0.1</span></span></p>

```csharp
void OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)
```

<span data-ttu-id="9bef1-116">Прослушиватель, вызываемый при запуске воспроизведения элемента мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="9bef1-116">Listener called when the media element starts playing.</span></span>

| <span data-ttu-id="9bef1-117">Параметры</span><span class="sxs-lookup"><span data-stu-id="9bef1-117">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="9bef1-118">P0</span><span class="sxs-lookup"><span data-stu-id="9bef1-118">p0</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement``` |
| <span data-ttu-id="9bef1-119">ниже</span><span class="sxs-lookup"><span data-stu-id="9bef1-119">p1</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) |

#### <a name="sample"></a><span data-ttu-id="9bef1-120">Пример</span><span class="sxs-lookup"><span data-stu-id="9bef1-120">Sample</span></span>

```csharp
public class MyCardActionHandler : ICardActionHandler
{
    public void OnMediaPlay(BaseCardElement element, RenderedAdaptiveCard renderedCard)
    {
    }
}
```

--- 

### <a id="onmediastop"></a><span data-ttu-id="9bef1-121">онмедиастоп</span><span class="sxs-lookup"><span data-stu-id="9bef1-121">OnMediaStop</span></span>
<p style='text-align:right'><span data-ttu-id="9bef1-122">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="9bef1-122">Added in version 0.1</span></span></p>

```csharp
void OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)
```

<span data-ttu-id="9bef1-123">Прослушиватель, вызываемый при остановке воспроизведения элемента мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="9bef1-123">Listener called when the media element stops playing.</span></span>

| <span data-ttu-id="9bef1-124">Параметры</span><span class="sxs-lookup"><span data-stu-id="9bef1-124">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="9bef1-125">P0</span><span class="sxs-lookup"><span data-stu-id="9bef1-125">p0</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement``` |
| <span data-ttu-id="9bef1-126">ниже</span><span class="sxs-lookup"><span data-stu-id="9bef1-126">p1</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) |

#### <a name="sample"></a><span data-ttu-id="9bef1-127">Пример</span><span class="sxs-lookup"><span data-stu-id="9bef1-127">Sample</span></span>

```csharp
public class MyCardActionHandler : ICardActionHandler
{
    public void OnMediaStop(BaseCardElement element, RenderedAdaptiveCard renderedCard)
    {
    }
}
```