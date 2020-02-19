---
title: Подготовка к просмотру карты с помощью пакета SDK для UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d7e101bbabfccf162797a3a8e154028f29bdc84b
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454087"
---
# <a name="render-a-card---uwp"></a>Визуализация карты — UWP

Вот как можно отобразить карту с помощью пакета SDK для UWP.

## <a name="create-an-instance-of-your-renderer"></a>Создание экземпляра модуля подготовки отчетов

На этом шаге необходимо создать экземпляр библиотеки средства визуализации. 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a>Создание карточки из строки JSON

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a>Создание карточки из объекта JSON

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a>Визуализация карточки

Получение карты из источника и ее отрисовка.

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a>Пример

Ниже приведен пример из модуля подготовки UWP.

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```