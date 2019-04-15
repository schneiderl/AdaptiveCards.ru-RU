---
title: Пакет SDK JavaScript для адаптивной карт
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6372f2f23a817ecc4d07d950d6513d14357547b7
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552666"
---
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="a67d9-102">Пакет SDK JavaScript для создания карт</span><span class="sxs-lookup"><span data-stu-id="a67d9-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a67d9-103">Библиотека для сериализации JSON находится в разработке и вашей milage может различаться.</span><span class="sxs-lookup"><span data-stu-id="a67d9-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="a67d9-104">Как было описано в разделе по началу работы, инструмент adaptive Cards является не более, а затем объект сериализованный json карты объектной модели.</span><span class="sxs-lookup"><span data-stu-id="a67d9-104">As we described in the getting started section, an adaptive card is nothing more then a serialized json object of a card object model.</span></span>  <span data-ttu-id="a67d9-105">Для упрощения управления объектной моделью мы определили некоторые библиотеки, которые определяют иерархию строго типизированных классов, которая проста для сериализации или десериализации json.</span><span class="sxs-lookup"><span data-stu-id="a67d9-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="a67d9-106">Можно использовать любые средства, которые вы хотите создать инструмент adaptive Cards json.</span><span class="sxs-lookup"><span data-stu-id="a67d9-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="a67d9-107">`adaptivecards` Пакета npm определяет библиотеку для работы с адаптивной карточек в javascript</span><span class="sxs-lookup"><span data-stu-id="a67d9-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="a67d9-108">Для установки</span><span class="sxs-lookup"><span data-stu-id="a67d9-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example-creating"></a><span data-ttu-id="a67d9-109">Пример. Создание</span><span class="sxs-lookup"><span data-stu-id="a67d9-109">Example creating</span></span> 
<span data-ttu-id="a67d9-110">Существуют определения интерфейса в `schema.d.ts` , описывающих фигуры схемы</span><span class="sxs-lookup"><span data-stu-id="a67d9-110">There are interface definitions in `schema.d.ts` which describe the shape of the schema</span></span>

```typescript
let card = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "Container",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "Meow!"
                },
                {
                    "type": "Image",
                    "url": "http://adaptivecards.io/content/cats/1.png"
                }
            ]
        }
    ]
};
```

<span data-ttu-id="a67d9-111">Имеется также объектной модели для создания карт.</span><span class="sxs-lookup"><span data-stu-id="a67d9-111">There is also an object model for creating cards.</span></span>


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
