---
title: Визуализация карточки — пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c9fbfa788af0b0c7f16824bf9c369fa59a1b80f5
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145474"
---
# <a name="render-a-card---android"></a><span data-ttu-id="8e91a-102">Визуализация карточки — Android</span><span class="sxs-lookup"><span data-stu-id="8e91a-102">Render a card - Android</span></span>

<span data-ttu-id="8e91a-103">Преобразовать карточку для просмотра можно с помощью пакета SDK для Android следующим образом.</span><span class="sxs-lookup"><span data-stu-id="8e91a-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="8e91a-104">Создание экземпляра объекта адаптивной карточки из текста JSON</span><span class="sxs-lookup"><span data-stu-id="8e91a-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="8e91a-105">**Критические изменения в версии 1.2**</span><span class="sxs-lookup"><span data-stu-id="8e91a-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="8e91a-106">Параметр Елементпарсеррегистратион изменен на Парсеконтекст, включающий Елементпарсеррегистратион и объект Актионпарсеррегистратион</span><span class="sxs-lookup"><span data-stu-id="8e91a-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="8e91a-107">или</span><span class="sxs-lookup"><span data-stu-id="8e91a-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="8e91a-108">Визуализация карточки</span><span class="sxs-lookup"><span data-stu-id="8e91a-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
