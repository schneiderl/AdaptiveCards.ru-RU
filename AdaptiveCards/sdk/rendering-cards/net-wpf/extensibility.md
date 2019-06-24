---
title: Расширяемость – пакет SDK .NET для WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 4f89784f711727deb538b2ed2195007ca8e6aca1
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134313"
---
# <a name="extensibility---net-wpf"></a><span data-ttu-id="b025d-102">Расширяемость – .NET WPF</span><span class="sxs-lookup"><span data-stu-id="b025d-102">Extensibility - .NET WPF</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="b025d-103">Визуализация пользовательских элементов</span><span class="sxs-lookup"><span data-stu-id="b025d-103">Custom Element Rendering</span></span>

<span data-ttu-id="b025d-104">Для полного контроля можно использовать свойство `ElementRenderers`, чтобы **добавлять**, **удалять** или **переопределять** требуемое средство визуализации.</span><span class="sxs-lookup"><span data-stu-id="b025d-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="b025d-105">В следующем примере показано, как можно определить пользовательский элемент `"type": "Rating"` и визуализировать его.</span><span class="sxs-lookup"><span data-stu-id="b025d-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

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
