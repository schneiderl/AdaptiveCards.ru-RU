---
title: Действия — пакет SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 9e96fd0ce6322e79f8717d8132857233f62f66f1
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553136"
---
# <a name="actions---net-wpf"></a><span data-ttu-id="31b89-102">Действия — .NET WPF</span><span class="sxs-lookup"><span data-stu-id="31b89-102">Actions - .NET WPF</span></span>

<span data-ttu-id="31b89-103">Любой `actions` в карточке отрисовывается как WPF `Button`s, но элемента в приложение для обработки, что происходит, когда пользователь нажимает их.</span><span class="sxs-lookup"><span data-stu-id="31b89-103">Any `actions` within the card will render as WPF `Button`s, but it's up to your app to handle what happens when a user presses them.</span></span> 

<span data-ttu-id="31b89-104">`RenderedAdaptiveCard` Предоставляет `OnAction` событий для этой цели.</span><span class="sxs-lookup"><span data-stu-id="31b89-104">The `RenderedAdaptiveCard` object provides an `OnAction` event for this purpose.</span></span>

```csharp
// Event handler fires when a user clicks an action within the card
renderedCard.OnAction += MyActionHandler;

private void MyActionHandler(RenderedAdaptiveCard sender, ActionEventArgs e)
{
    if (e.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        Process.Start(openUrlAction.Url);
    }
    else if (e.Action is AdaptiveShowCardAction showCardAction)
    {
        // Action.ShowCard can be rendered inline automatically
        // ... but if you want to handle show card as a "popup", you handle this event
        if (_myHostConfig.Actions.ShowCard.ActionMode == ShowCardActionMode.Popup)
        {
            var dialog = new ShowCardWindow(showCardAction.Title, showCardAction, Resources);
            dialog.Owner = this;
            dialog.ShowDialog();
        }
    }
    else if (e.Action is AdaptiveSubmitAction submitAction)
    {
        var inputs = sender.UserInputs.AsJson();
        inputs.Merge(submitAction.Data);
        MessageBox.Show(this, JsonConvert.SerializeObject(inputs, Formatting.Indented), "SubmitAction");
    }
}
```