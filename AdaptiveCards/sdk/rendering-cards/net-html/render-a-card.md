---
title: Визуализации карт - пакета SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 8dc1baffb91f0755f1955ee02b8a3e820b0d34e4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553106"
---
# <a name="render-a-card---net-html"></a><span data-ttu-id="4fff2-102">Визуализации карт - .NET HTML</span><span class="sxs-lookup"><span data-stu-id="4fff2-102">Render a card - .NET HTML</span></span>

<span data-ttu-id="4fff2-103">Вот способ визуализации карт, с помощью пакета SDK для .NET HTML.</span><span class="sxs-lookup"><span data-stu-id="4fff2-103">Here's how to render a card using the .NET HTML SDK.</span></span>

## <a name="instantiate-a-renderer"></a><span data-ttu-id="4fff2-104">Создать экземпляр модуля подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="4fff2-104">Instantiate a renderer</span></span>

<span data-ttu-id="4fff2-105">Следующим шагом является создание экземпляра модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="4fff2-105">The next step is to create an instance of the renderer.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Html;
// ... 

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

## <a name="render-a-card-to-html"></a><span data-ttu-id="4fff2-106">Просмотру карточки в формате HTML</span><span class="sxs-lookup"><span data-stu-id="4fff2-106">Render a card to HTML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard()
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the output HTML 
    HtmlTag html = renderedCard.Html;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maxmimum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```
