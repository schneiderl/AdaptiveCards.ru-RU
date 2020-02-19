---
title: Расширяемость — пакет SDK для UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ffe22e1e9b8632cbceedb4bfc26b285b4a9b0075
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454017"
---
# <a name="extensibility---uwp"></a><span data-ttu-id="12976-102">Расширяемость — UWP</span><span class="sxs-lookup"><span data-stu-id="12976-102">Extensibility - UWP</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="12976-103">Изменение отрисовки на элемент</span><span class="sxs-lookup"><span data-stu-id="12976-103">Changing per element rendering</span></span>

<span data-ttu-id="12976-104">Реализация класса модуля подготовки отчетов и его задание в модуле подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="12976-104">Implement a renderer class and set it in the renderer</span></span>

```csharp
// My custom renderer is going to replace how textblocks should render!
public class MyCustomRenderer : IAdaptiveElementRenderer
{
    public UIElement Render(IAdaptiveCardElement element, AdaptiveRenderContext context)
    {
        var adaptiveTextBlock = element as AdaptiveTextBlock;
        TextBlock textblock = new TextBlock()
        {
            Text = adaptiveTextBlock.Text + "I want every single textblock to append this text, and it should be aligned to the right!",
            HorizontalAlignment = HorizontalAlignment.Right
        };

        return textblock;
    }
}

renderer.ElementRenderers.Set("TextBlock", new MyCustomRenderer());
```