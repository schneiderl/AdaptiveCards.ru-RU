---
title: Расширяемость — пакет SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: d1df38608abde9ad26c78bbc5f66eb3bbb3d1971
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454537"
---
# <a name="extensibility---net-html"></a><span data-ttu-id="17d42-102">Расширяемость — HTML-код .NET</span><span class="sxs-lookup"><span data-stu-id="17d42-102">Extensibility - .NET HTML</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="17d42-103">Визуализация пользовательских элементов</span><span class="sxs-lookup"><span data-stu-id="17d42-103">Custom Element Rendering</span></span>

<span data-ttu-id="17d42-104">Для полного контроля можно использовать свойство `ElementRenderers`, чтобы **добавлять**, **удалять** или **переопределять** требуемое средство визуализации.</span><span class="sxs-lookup"><span data-stu-id="17d42-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="17d42-105">В следующем примере показано, как можно определить пользовательский элемент `"type": "Rating"` и визуализировать его.</span><span class="sxs-lookup"><span data-stu-id="17d42-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public override string Type => "Rating";

    public double Rating { get; set; }

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
