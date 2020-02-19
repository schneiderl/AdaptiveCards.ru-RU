---
title: Пакет SDK для JavaScript для адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454807"
---
# <a name="javascript-sdk-for-creating-cards"></a>Пакет SDK для JavaScript для создания карточек

> [!IMPORTANT]
> Библиотека для сериализации JSON все еще разрабатывается, и милаже может отличаться.

Как мы уже упоминали в [Начало работы](../../authoring-cards/getting-started.md), адаптивная карта — это лишь сериализованный объект JSON объектной модели карты.  Чтобы упростить обработку объектной модели, мы определили некоторые библиотеки, определяющие строго типизированную иерархию классов, которая проста в сериализации и десериализации JSON.

Вы можете использовать любые средства, которые необходимо создать с помощью формата JSON для адаптивной карты.

Пакет `adaptivecards` NPM определяет библиотеку для работы с адаптивными картами в JavaScript

## <a name="to-install"></a>Установка
```console
npm install adaptivecards
```

## <a name="example"></a>Пример

Следующий API показывает, как создать адаптивную карту с помощью объектной модели и сериализовать ее в JSON.

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
