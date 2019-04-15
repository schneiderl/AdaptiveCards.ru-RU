---
title: Визуализации карт - пакета SDK для универсальной платформы Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 1a72cb9ba72811d4e98a48116fa08245e13a6392
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552436"
---
# <a name="render-a-card---uwp"></a><span data-ttu-id="71979-102">Визуализации карт - универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="71979-102">Render a card - UWP</span></span>

<span data-ttu-id="71979-103">Вот способ визуализации карт, с помощью пакета SDK универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="71979-103">Here's how to render a card using the UWP SDK.</span></span>

## <a name="create-an-instance-of-your-renderer"></a><span data-ttu-id="71979-104">Создайте экземпляр вашего модуля подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="71979-104">Create an instance of your renderer</span></span>

<span data-ttu-id="71979-105">Создайте экземпляр библиотеки модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="71979-105">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="71979-106">Создание карточки из строки JSON</span><span class="sxs-lookup"><span data-stu-id="71979-106">Create a card from a JSON string</span></span>

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a><span data-ttu-id="71979-107">Создание карточки из объекта JSON</span><span class="sxs-lookup"><span data-stu-id="71979-107">Create a card from a JSON object</span></span>

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a><span data-ttu-id="71979-108">Визуализации карт</span><span class="sxs-lookup"><span data-stu-id="71979-108">Render a card</span></span>

<span data-ttu-id="71979-109">Получить карточку из источника и визуализировать его.</span><span class="sxs-lookup"><span data-stu-id="71979-109">Acquire a card from a source and render it.</span></span>

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a><span data-ttu-id="71979-110">Пример</span><span class="sxs-lookup"><span data-stu-id="71979-110">Example</span></span>

<span data-ttu-id="71979-111">Вот пример из модуля подготовки отчетов универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="71979-111">Here is an example from the UWP renderer.</span></span>

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```