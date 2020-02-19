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
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="02561-102">Пакет SDK для JavaScript для создания карточек</span><span class="sxs-lookup"><span data-stu-id="02561-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02561-103">Библиотека для сериализации JSON все еще разрабатывается, и милаже может отличаться.</span><span class="sxs-lookup"><span data-stu-id="02561-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="02561-104">Как мы уже упоминали в [Начало работы](../../authoring-cards/getting-started.md), адаптивная карта — это лишь сериализованный объект JSON объектной модели карты.</span><span class="sxs-lookup"><span data-stu-id="02561-104">As we described in the [Getting Started](../../authoring-cards/getting-started.md), an Adaptive Card is nothing more than a serialized JSON object of a card object model.</span></span>  <span data-ttu-id="02561-105">Чтобы упростить обработку объектной модели, мы определили некоторые библиотеки, определяющие строго типизированную иерархию классов, которая проста в сериализации и десериализации JSON.</span><span class="sxs-lookup"><span data-stu-id="02561-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="02561-106">Вы можете использовать любые средства, которые необходимо создать с помощью формата JSON для адаптивной карты.</span><span class="sxs-lookup"><span data-stu-id="02561-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="02561-107">Пакет `adaptivecards` NPM определяет библиотеку для работы с адаптивными картами в JavaScript</span><span class="sxs-lookup"><span data-stu-id="02561-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="02561-108">Установка</span><span class="sxs-lookup"><span data-stu-id="02561-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example"></a><span data-ttu-id="02561-109">Пример</span><span class="sxs-lookup"><span data-stu-id="02561-109">Example</span></span>

<span data-ttu-id="02561-110">Следующий API показывает, как создать адаптивную карту с помощью объектной модели и сериализовать ее в JSON.</span><span class="sxs-lookup"><span data-stu-id="02561-110">The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.</span></span>

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
