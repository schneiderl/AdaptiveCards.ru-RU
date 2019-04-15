---
title: Расширяемость – пакет SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: af301ec4d73b6791c1d132b9df7040d71cf70d7b
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552626"
---
# <a name="extensibility---net-wpf"></a><span data-ttu-id="e078e-102">Расширяемость – .NET WPF</span><span class="sxs-lookup"><span data-stu-id="e078e-102">Extensibility - .NET WPF</span></span>

## <a name="custom-element-rendering"></a><span data-ttu-id="e078e-103">Пользовательский элемент визуализации</span><span class="sxs-lookup"><span data-stu-id="e078e-103">Custom Element Rendering</span></span>

<span data-ttu-id="e078e-104">Для полного доступа модуля подготовки отчетов можно использовать `ElementRenderers` свойства **добавить**, **удалить**, или **переопределить** по умолчанию модули подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="e078e-104">For full control of the renderer you can use the `ElementRenderers` property to **add**, **remove**, or **override** default renderers.</span></span>

<span data-ttu-id="e078e-105">В следующем примере показано, как можно определить пользовательский `"type": "Rating"` элемент и визуализировать его.</span><span class="sxs-lookup"><span data-stu-id="e078e-105">The following example shows how you could define a custom `"type": "Rating"` element and render it.</span></span>

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
