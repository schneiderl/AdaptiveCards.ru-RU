---
title: Действия — пакет SDK для универсальной платформы Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d1d3410b19071f601b31e14882f2cccb4d1e6ccb
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552976"
---
# <a name="actions---uwp"></a><span data-ttu-id="17c1e-102">Действия, универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="17c1e-102">Actions - UWP</span></span>

<span data-ttu-id="17c1e-103">Любой **действия** в карточке отрисовывается как UWP **кнопку**элемента, но он работает в приложение для обработки, что происходит, когда пользователь нажимает их (за исключением ShowCard действия... см. фрагмент кода, Дополнительные сведения).</span><span class="sxs-lookup"><span data-stu-id="17c1e-103">Any **actions** within the card will render as UWP **Button**'s, but it's up to your app to handle what happens when a user presses them (except for ShowCard actions... see code snippet for more info).</span></span>

<span data-ttu-id="17c1e-104">`RenderedAdaptiveCard` Предоставляет `Action` событий для этой цели.</span><span class="sxs-lookup"><span data-stu-id="17c1e-104">The `RenderedAdaptiveCard` object provides an `Action` event for this purpose.</span></span>

```csharp
// Render a card (as previously shown)
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// ...

// Attach the event handler for action click events
renderedAdaptiveCard.Action += RenderedAdaptiveCard_Action;

private async void RenderedAdaptiveCard_Action(RenderedAdaptiveCard sender, AdaptiveActionEventArgs args)
{
    if (args.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        await Launcher.LaunchUriAsync(openUrlAction.Url);
    }

    else if (args.Action is AdaptiveShowCardAction showCardAction)
    {
        // This is only fired if, in HostConfig, you set the ShowCard ActionMode to Popup.
        // Otherwise, the renderer will automatically display the card inline without firing this event.
    }

    else if (args.Action is AdaptiveSubmitAction submitAction)
    {
        // Get the data and inputs
        string data = submitAction.DataJson.Stringify();
        string inputs = args.Inputs.AsJson().Stringify();

        // Process them as desired
    }
}
```
