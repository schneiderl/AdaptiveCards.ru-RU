---
title: Пакеты SDK для шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 5f60a458af99f1b88e8ee428a8f29f1849be9b62
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878881"
---
# <a name="adaptive-card-templating-sdks"></a>Пакеты SDK для адаптивных шаблонов карт

Пакеты SDK для шаблонов адаптивной карты упрощают заполнение [шаблона карты](language.md) реальными данными на любой поддерживаемой платформе.

> Дополнительные сведения о шаблонах [адаптивных карт](index.md) см. в этой статье.

> [!IMPORTANT] 
> 
> Эти функции доступны **в предварительной версии и могут быть изменены**. Ваш отзыв не только Добро пожаловать, но и важен для обеспечения того, чтобы мы доставлять нужные **вам** функции.
> 
> Во время первоначальной предварительной версии доступен только пакет SDK для JavaScript, но вскоре будет получен пакет SDK для .NET.

## <a name="javascript"></a>JavaScript

Библиотека [адаптивекардс-шаблонов](https://www.npmjs.com/package/adaptivecards-templating) доступна в NPM и с помощью CDN. Полную документацию см. в ссылке на пакет.

### <a name="npm"></a>NPM

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>СЕТЬ

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a>Использование

В примере ниже предполагается, что вы также установили библиотеку [адаптивекардс](https://www.npmjs.com/package/adaptivecards) , чтобы подготовить карту. 

Если вы не планируете отрисовку карты, то можете удалить `parse` код и. `render` 

```js
import * as ACData from "adaptivecards-templating";
import * as AdaptiveCards from "adaptivecards";
 
// Define a template payload
var templatePayload = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hello {name}!"
        }
    ]
};
 
// Create a Template instamce from the template payload
var template = new ACData.Template(templatePayload);
 
// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context = new ACData.EvaluationContext();
context.$root = {
    "name": "Mickey Mouse"
};
 
// "Expand" the template - this generates the final Adaptive Card,
// ready to render
var card = template.expand(context);
 
// Render the card
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(card);
 
var htmlElement = adaptiveCard.render();
```

## <a name="net-coming-soon"></a>.NET (*ожидается в ближайшее время*)

ЕЩЕ НЕ РАБОТАЕТ: 

```console
nuget install AdaptiveCards.Templating
```
