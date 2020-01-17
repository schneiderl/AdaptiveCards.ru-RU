---
title: Подготовка карты к Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: dc1d48e05e99d6254b9253efa7145cefeb2ed17c
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145978"
---
# <a name="render-a-card---xamarinandroid"></a><span data-ttu-id="d9439-102">Подготовка карты к Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="d9439-102">Render a card - Xamarin.Android</span></span>

<span data-ttu-id="d9439-103">Вот как можно отобразить карту с помощью Xamarin. пакет SDK для Android.</span><span class="sxs-lookup"><span data-stu-id="d9439-103">Here's how to render a card using the Xamarin.Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="d9439-104">Создание экземпляра объекта адаптивной карточки из текста JSON</span><span class="sxs-lookup"><span data-stu-id="d9439-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
AdaptiveCard adaptiveCard = parseResult.AdaptiveCard;
```

<span data-ttu-id="d9439-105">также можно использовать объект ```ParseContext``` для десериализации настраиваемых элементов, которые включены в адаптивную карту следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d9439-105">or you can also use a ```ParseContext``` object to be able to deserialize custom elements that are included in your adaptive card like this:</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

<span data-ttu-id="d9439-106">или</span><span class="sxs-lookup"><span data-stu-id="d9439-106">or</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

## <a name="render-a-card"></a><span data-ttu-id="d9439-107">Визуализация карточки</span><span class="sxs-lookup"><span data-stu-id="d9439-107">Render a card</span></span>

<span data-ttu-id="d9439-108">Чтобы подготовить карту к просмотру, вам потребуется какая-то информация</span><span class="sxs-lookup"><span data-stu-id="d9439-108">To be able to render a card you'll need some information</span></span>
* <span data-ttu-id="d9439-109">контекст: может быть получен из действия, в котором размещена карта.</span><span class="sxs-lookup"><span data-stu-id="d9439-109">context: Obtainable from the Activity the card is hosted in</span></span>
* <span data-ttu-id="d9439-110">Фрагментманажер. также можно получить из действия размещения</span><span class="sxs-lookup"><span data-stu-id="d9439-110">fragmentManager: can also be retrieved from the hosting activity</span></span>
* <span data-ttu-id="d9439-111">Кардактионхандлер: экземпляр [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) для управления поведением действия</span><span class="sxs-lookup"><span data-stu-id="d9439-111">cardActionHandler: instance of [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) to manage the action behaviour</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;
// ...

var renderedCard = AdaptiveCardRenderer.Instance.Render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.View;
```
