---
title: Визуализация карточки — пакет SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: a4eeda54a80c959ff9a1246371240954b4c3fb12
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134289"
---
# <a name="render-a-card---android"></a><span data-ttu-id="b8e48-102">Визуализация карточки — Android</span><span class="sxs-lookup"><span data-stu-id="b8e48-102">Render a card - Android</span></span>

<span data-ttu-id="b8e48-103">Преобразовать карточку для просмотра можно с помощью пакета SDK для Android следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b8e48-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="b8e48-104">Создание экземпляра объекта адаптивной карточки из текста JSON</span><span class="sxs-lookup"><span data-stu-id="b8e48-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="b8e48-105">**Критические изменения в версии 1.2**</span><span class="sxs-lookup"><span data-stu-id="b8e48-105">**Breaking changes for v1.2**</span></span>
> 
> 1. <span data-ttu-id="b8e48-106">Параметр ElementParserRegistration изменен на ParseContext, который включает в себя ElementParserRegistration и объект ActionRegistration.</span><span class="sxs-lookup"><span data-stu-id="b8e48-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionRegistration object</span></span>
> ```java
> ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
> ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
> ```

## <a name="render-a-card"></a><span data-ttu-id="b8e48-107">Визуализация карточки</span><span class="sxs-lookup"><span data-stu-id="b8e48-107">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```
