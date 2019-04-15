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
# <a name="javascript-sdk-for-creating-cards"></a>Пакет SDK JavaScript для создания карт

> [!IMPORTANT]
> Библиотека для сериализации JSON находится в разработке и вашей milage может различаться.

Как было описано в разделе по началу работы, инструмент adaptive Cards является не более, а затем объект сериализованный json карты объектной модели.  Для упрощения управления объектной моделью мы определили некоторые библиотеки, которые определяют иерархию строго типизированных классов, которая проста для сериализации или десериализации json.

Можно использовать любые средства, которые вы хотите создать инструмент adaptive Cards json.

`adaptivecards` Пакета npm определяет библиотеку для работы с адаптивной карточек в javascript

## <a name="to-install"></a>Для установки
```console
npm install adaptivecards
```

## <a name="example-creating"></a>Пример. Создание 
Существуют определения интерфейса в `schema.d.ts` , описывающих фигуры схемы

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

Имеется также объектной модели для создания карт.


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
