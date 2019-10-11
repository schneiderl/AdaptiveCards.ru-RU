---
title: Пакеты SDK для создания шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 3a9bfcd1bf8f87959a747997e04f5c5ad2a79980
ms.sourcegitcommit: 90afb3729931b0e4cae19b17ef9e49453c2d2bf6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163613"
---
# <a name="adaptive-card-templating-sdks"></a>Пакеты SDK для адаптивных шаблонов карт

Пакеты SDK для шаблонов адаптивной карты упрощают заполнение [шаблона карты](language.md) реальными данными на любой поддерживаемой платформе.

> Дополнительные [сведения о шаблонах адаптивных карт](index.md) см. в этой статье.

> [!IMPORTANT] 
> 
> Эти функции предоставляются в **ознакомительной версии и могут быть изменены**. Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.
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

Если вы не планируете рендеринг карты, то можете удалить код `parse` и `render`. 

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

## <a name="net"></a>.NET 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> Попробуйте изменить версию выше до последней опубликованной версии

Импорт библиотеки 

```cs
using AdaptiveCards.Templating
```

Используйте модуль шаблонов, передав шаблон JSON и данные JSON.

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello {name}""
        }
    ]
}";

var dataJson = @"
{
    ""name"": ""Mickey Mouse""
}";

var transformer = new AdaptiveTransformer();
var cardJson = transformer.Transform(templateJson, dataJson);
```
