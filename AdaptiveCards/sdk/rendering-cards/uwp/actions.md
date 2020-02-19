---
title: Действия — пакет SDK для UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 98b4374ce6a31d6d7ec2416d3b4e451ef1c59d1b
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454107"
---
# <a name="actions---uwp"></a>Действия — UWP

Все **действия** в карточке будут отображаться как **кнопки**UWP, но приложение будет обрабатывать события, происходящие при нажатии пользователем (за исключением действий шовкард... Дополнительные сведения см. в фрагменте кода.

Для этого объект `RenderedAdaptiveCard` предоставляет событие `Action`.

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
