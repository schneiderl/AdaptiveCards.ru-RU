---
title: Визуализации карт - пакета SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: b93ce97a41152641892e6a69d5221842181fcb72
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552516"
---
# <a name="render-a-card---android"></a><span data-ttu-id="67a8f-102">Визуализации карт - Android</span><span class="sxs-lookup"><span data-stu-id="67a8f-102">Render a card - Android</span></span>

<span data-ttu-id="67a8f-103">Вот способ визуализации карт, с помощью пакета SDK для Android.</span><span class="sxs-lookup"><span data-stu-id="67a8f-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="67a8f-104">Создайте экземпляр объекта инструмент Adaptive Cards из текста JSON</span><span class="sxs-lookup"><span data-stu-id="67a8f-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```

## <a name="render-a-card"></a><span data-ttu-id="67a8f-105">Визуализации карт</span><span class="sxs-lookup"><span data-stu-id="67a8f-105">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```