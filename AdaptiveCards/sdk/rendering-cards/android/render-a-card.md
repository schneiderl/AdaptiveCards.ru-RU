---
title: Визуализация карточки — пакет SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 55e0fa828abf3b9af857d1deb7ecd3744b5a7280
ms.sourcegitcommit: 8c8067206f283d97a5aa4ec65ba23d3fe18962f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299522"
---
# <a name="render-a-card---android"></a><span data-ttu-id="57508-102">Визуализация карточки — Android</span><span class="sxs-lookup"><span data-stu-id="57508-102">Render a card - Android</span></span>

<span data-ttu-id="57508-103">Преобразовать карточку для просмотра можно с помощью пакета SDK для Android следующим образом.</span><span class="sxs-lookup"><span data-stu-id="57508-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="57508-104">Создание экземпляра объекта адаптивной карточки из текста JSON</span><span class="sxs-lookup"><span data-stu-id="57508-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="57508-105">**Критические изменения в версии 1.2**</span><span class="sxs-lookup"><span data-stu-id="57508-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="57508-106">Параметр Елементпарсеррегистратион изменен на Парсеконтекст, включающий Елементпарсеррегистратион и объект Актионпарсеррегистратион</span><span class="sxs-lookup"><span data-stu-id="57508-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="57508-107">или диспетчер конфигурации служб</span><span class="sxs-lookup"><span data-stu-id="57508-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="57508-108">Визуализация карточки</span><span class="sxs-lookup"><span data-stu-id="57508-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
