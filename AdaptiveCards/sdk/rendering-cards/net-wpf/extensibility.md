---
title: Расширяемость – пакет SDK .NET для WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 3e5bb9239d4b4200262648350d67d6494eed9724
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454327"
---
# <a name="extensibility---net-wpf"></a>Расширяемость – .NET WPF

## <a name="custom-element-rendering"></a>Визуализация пользовательских элементов

Для полного контроля можно использовать свойство `ElementRenderers`, чтобы **добавлять**, **удалять** или **переопределять** требуемое средство визуализации.

В следующем примере показано, как можно определить пользовательский элемент `"type": "Rating"` и визуализировать его.

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public MyCustomRating() { Type = "Rating"; }

    public override string Type { get; set; }

    public AdaptiveTextSize Size { get; set; }

    public AdaptiveTextColor Color { get; set; }

    public static FrameworkElement Render(MyCustomRating rating, AdaptiveRenderContext context)
    {
        var textBlock = new AdaptiveTextBlock
        {
            Size = rating.Size,
            Color = rating.Color
        };
        for (int i = 0; i < rating.Rating; i++)
        {
            textBlock.Text += "\u2605";
        }
        textBlock.Text += $" ({rating.Rating})";
        return context.Render(textBlock);
    }
}
```
