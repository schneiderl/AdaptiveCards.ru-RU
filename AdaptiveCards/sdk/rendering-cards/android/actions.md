---
title: Действия — пакет SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 49b0b45abeb54381bd7b4b548219a09ad5da10c1
ms.sourcegitcommit: 8c8067206f283d97a5aa4ec65ba23d3fe18962f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299528"
---
# <a name="actions---android"></a><span data-ttu-id="c0256-102">Действия — Android</span><span class="sxs-lookup"><span data-stu-id="c0256-102">Actions - Android</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0256-103">**Список критических изменений**</span><span class="sxs-lookup"><span data-stu-id="c0256-103">**List of Breaking changes**</span></span>
> 
> [<span data-ttu-id="c0256-104">Критические изменения в v 1.1</span><span class="sxs-lookup"><span data-stu-id="c0256-104">Breaking changes in v1.1</span></span>](#breaking-changes-in-v11)
> 

<span data-ttu-id="c0256-105">Когда выполняется действие карточек, вызывается класс, переданный в вызов прорисовки, который реализует ```ICardActionHandler``` интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c0256-105">When a cards action is executed, the class that was passed to the render call that implements the ```ICardActionHandler``` interface gets invoked.</span></span> <span data-ttu-id="c0256-106">Обработчик действий определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c0256-106">Here is how to define your action handler:</span></span>

```java
public class ActionHandler implements ICardActionHandler
{
    @Override
    public void onAction(BaseActionElement actionElement, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = actionElement.GetElementType();
        if (actionType == ActionType.Submit)
        {
            onSubmit(actionElement, renderedCard);
        }
        else if (actionType == ActionType.ShowCard)
        {
            onShowCard(actionElement);
        }
        else if (actionType == ActionType.OpenUrl)
        {
            onOpenUrl(actionElement);
        }
        else if (actionType == ActionType.Custom)
        {
            //Handle activation of custom actions
            ...
        }
    }

    private void onSubmit(BaseActionElement actionElement, RenderedAdaptiveCard renderedAdaptiveCard)
    {
        SubmitAction submitAction = null;
        if (actionElement instanceof SubmitAction)
        {
            submitAction = (SubmitAction) actionElement;
        }
        else if ((submitAction = SubmitAction.dynamic_cast(actionElement)) == null)
        {
            throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
        }

        String data = submitAction.GetDataJson();
        Map<String, String> keyValueMap = renderedAdaptiveCard.getInputs();
        if (!data.isEmpty())
        {
            try
            {
                JSONObject object = new JSONObject(data);
                showToast("Submit data: " + object.toString() + "\nInput: " + keyValueMap.toString(), Toast.LENGTH_LONG);
            }
            catch (JSONException e)
            {
                showToast(e.toString(), Toast.LENGTH_LONG);
            }
        }
        else
        {
            showToast("Submit input: " + keyValueMap.toString(), Toast.LENGTH_LONG);
        }
    }

    private void onShowCard(BaseActionElement actionElement)
    {
        ShowCardAction showCardAction = null;
        if (actionElement instanceof ShowCardAction)
        {
            showCardAction = (ShowCardAction) actionElement;
        }
        else if ((showCardAction = ShowCardAction.dynamic_cast(actionElement)) == null)
        {
            throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
        }

        //Get the card from show card and create a view
        RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, showCardAction.GetCard(), cardActionHandler, hostConfig);

        ViewGroup viewGroup = (ViewGroup) renderedCard.getView();
        ...
    }

    private void onOpenUrl(BaseActionElement actionElement)
    {
        OpenUrlAction openUrlAction = null;
        if (actionElement instanceof ShowCardAction)
        {
            openUrlAction = (OpenUrlAction) actionElement;
        }
        else if ((openUrlAction = OpenUrlAction.dynamic_cast(actionElement)) == null)
        {
            throw new InternalError("Unable to convert BaseActionElement to ShowCardAction object model.");
        }

        Intent browserIntent = new Intent(Intent.ACTION_VIEW, Uri.parse(openUrlAction.GetUrl()));
        this.startActivity(browserIntent);
    }
}
```

## <a name="breaking-changes-in-v11"></a><span data-ttu-id="c0256-107">Критические изменения в v 1.1</span><span class="sxs-lookup"><span data-stu-id="c0256-107">Breaking changes in v1.1</span></span>

<span data-ttu-id="c0256-108">Для элемента мультимедиа, входящего в эту версию, требуются два новых метода, реализуемых классами, ```ICardActionHandler```которые реализуют эти методы:</span><span class="sxs-lookup"><span data-stu-id="c0256-108">The media element included in this version requires two new methods to be implemented by the classes that implement ```ICardActionHandler```, these methods are:</span></span>

* <span data-ttu-id="c0256-109">```onMediaPlay```вызывается, когда кнопка воспроизведения нажимается в первый раз в любом элементе мультимедиа</span><span class="sxs-lookup"><span data-stu-id="c0256-109">```onMediaPlay``` is invoked when the play button is pressed for the first time in any media element</span></span>
* <span data-ttu-id="c0256-110">```onMediaStop```вызывается, когда носитель достигает конца</span><span class="sxs-lookup"><span data-stu-id="c0256-110">```onMediaStop``` is invoked when the media reaches it's end</span></span>

<span data-ttu-id="c0256-111">Для этих методов используются следующие сигнатуры:</span><span class="sxs-lookup"><span data-stu-id="c0256-111">The signatures for these methods are:</span></span>

```java
public void onMediaPlay(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
public void onMediaStop(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
```

<span data-ttu-id="c0256-112">Реализация ActionHandler из предыдущего примера теперь будет выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="c0256-112">And the implementation for the ActionHandler from the previous example would now look similar to this:</span></span>

```java
public class ActionHandler implements ICardActionHandler
{
    @Override
    public void onAction(BaseActionElement actionElement, RenderedAdaptiveCard renderedCard)
    { }

    private void onSubmit(BaseActionElement actionElement, RenderedAdaptiveCard renderedAdaptiveCard) 
    { }

    private void onShowCard(BaseActionElement actionElement)
    { }

    private void onOpenUrl(BaseActionElement actionElement)
    { }

    @Override
    public void onMediaPlay(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
    {
        // Your logic here, i.e.
        showToast("Media started: " + mediaElement, Toast.LENGTH_LONG);
    }

    @Override
    public void onMediaStop(BaseCardElement mediaElement, RenderedAdaptiveCard renderedAdaptiveCard)
    {
        // Your logic here, i.e.
        showToast("Media ended playing: " + mediaElement, Toast.LENGTH_LONG);
    }
}
```
