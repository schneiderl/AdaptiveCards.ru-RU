---
title: Визуализация карточки — пакет SDK .NET для HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 0280e37506e1034572f518b1f596e8f1a3bb30be
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454467"
---
# <a name="render-a-card---net-html"></a>Визуализация карточки — пакет SDK .NET для HTML

Преобразовать карточку для просмотра можно с помощью пакета SDK .NET для HTML следующим образом.

## <a name="instantiate-a-renderer"></a>Создание экземпляра средства визуализации

На этом шаге необходимо создать экземпляр средства визуализации. 

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

## <a name="render-a-card-to-html"></a>Визуализация карточки в формате HTML

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
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```
