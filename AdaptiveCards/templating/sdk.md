---
title: Пакеты SDK для создания шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 3a9bfcd1bf8f87959a747997e04f5c5ad2a79980
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "72163613"
---
# <a name="adaptive-card-templating-sdks"></a>Пакеты SDK для работы с шаблонами адаптивных карточек

Пакеты SDK для работы с шаблонами адаптивных карточек упрощают заполнение [шаблона карточки](language.md) реальными данными на любой поддерживаемой платформе.

> Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).

> [!IMPORTANT] 
> 
> Эти функции предоставляются в **ознакомительной версии и могут быть изменены**. Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.
> 
> Во время действия первоначальной предварительной версии доступен только пакет SDK для JavaScript, но скоро будет предоставляться и пакет SDK для .NET.

## <a name="javascript"></a>JavaScript

К библиотеке [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) можно получить с помощью npm и CDN. Полную документацию см. по ссылке на пакет.

### <a name="npm"></a>npm

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a>Использование

В приведенном ниже примере предполагается, что вы также установили библиотеку [adaptivecards](https://www.npmjs.com/package/adaptivecards) для отрисовки карточек. 

Если вы не планируете выполнять отрисовку карточек, то можете удалить код `parse` и `render`. 

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
> Рекомендуем изменить указанную выше версию на последнюю опубликованную версию.

Импортируйте библиотеку. 

```cs
using AdaptiveCards.Templating
```

Используйте подсистему работы с шаблонами, передав шаблон и данные в формате JSON.

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
