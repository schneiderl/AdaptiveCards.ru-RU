---
title: Пакеты SDK для создания шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 05/15/2020
ms.topic: article
ms.openlocfilehash: a8db2f5ef84203187ed1b9d0fc8dd3ce63ee3569
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417580"
---
# <a name="adaptive-card-templating-sdks"></a>Пакеты SDK для работы с шаблонами адаптивных карточек

Пакеты SDK для работы с шаблонами адаптивных карточек упрощают заполнение [шаблона карточки](language.md) реальными данными на любой поддерживаемой платформе.

> Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).

> [!IMPORTANT] 
> 
> **Критические изменения** в **версии-кандидате за май 2020 г.**
>
> Мы приложили немало усилий, чтобы этот выпуск увидел свет, и уже находимся на финишной прямой. В окончательную версию нам пришлось внести небольшие критические изменения.

## <a name="breaking-changes-as-of-may-2020"></a>Критические изменения в версии за май 2020 г.

1. Синтаксис привязки изменен с `{...}` на `${...}`. 
    * Например, вместо `"text": "Hello {name}"` теперь используется `"text": "Hello ${name}"`.
2. API JavaScript больше не содержит объект `EvaluationContext`. Просто передайте данные в функцию `expand`. Дополнительные сведения см. на [странице о пакете SDK](sdk.md).
3. API .NET был модернизирован для обеспечения более точного соответствия API JavaScript. Полные сведения см. ниже.

## <a name="javascript"></a>JavaScript

К библиотеке [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) можно получить с помощью npm и CDN. Полную документацию см. по ссылке на пакет.

### <a name="npm"></a>npm

[![Установка с помощью npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)

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
            "text": "Hello ${name}!"
        }
    ]
};
 
// Create a Template instance from the template payload
var template = new ACData.Template(templatePayload);
 
// Expand the template with your `$root` data object.
// This binds it to the data and produces the final Adaptive Card payload
var cardPayload = template.expand({
   $root: {
      name: "Matt Hidinger"
   }
});
 
// OPTIONAL: Render the card (requires that the adaptivecards library be loaded)
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(cardPayload);
document.getElementById('exampleDiv').appendChild(adaptiveCard.render());
```

## <a name="net"></a>.NET 

> [!IMPORTANT] 
> 
> Версия-кандидат .NET станет доступной предположительно 23 мая. Ищите версию `1.0.0-RC1`.
>

[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a>Использование

```cs
// Import the library 
using AdaptiveCards.Templating;
```

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.2"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello ${name}!""
        }
    ]
}";

// Create a Template instance from the template payload
AdaptiveCardTemplate template = new AdaptiveCardTemplate(templateJson);

// You can use any serializable object as your data
var myData = new
{
    Name = "Matt Hidinger"
};

// "Expand" the template - this generates the final Adaptive Card payload
string cardJson = template.Expand(myData);
```

### <a name="custom-functions"></a>Пользовательские функции

В дополнение к предварительно созданным функциям в адаптивную библиотеку выражений можно добавлять пользовательские функции.

В примере ниже показано, как добавить пользовательскую функцию stringFormat для форматирования строки.
```cs
string jsonTemplate = @"{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [{
        ""type"": ""TextBlock"",
        ""text"": ""${stringFormat(strings.myName, person.firstName, person.lastName)}""
    }]
}";

string jsonData = @"{
    ""strings"": {
        ""myName"": ""My name is {0} {1}""
    },
    ""person"": {
        ""firstName"": ""Andrew"",
        ""lastName"": ""Leader""
    }
}";

AdaptiveCardTemplate template = new AdaptiveCardTemplate(jsonTemplate);

var context = new EvaluationContext
{
    Root = jsonData
};

// a custom function is added
AdaptiveExpressions.Expression.Functions.Add("stringFormat", (args) =>
{
    string formattedString = "";

    // argument is packed in sequential order as defined in the template
    // For example, suppose we have "${stringFormat(strings.myName, person.firstName, person.lastName)}"
    // args will have following entries
    // args[0]: strings.myName
    // args[1]: person.firstName
    // args[2]: strings.lastName
    if (args[0] != null && args[1] != null && args[2] != null) 
    {
        string formatString = args[0];
        string[] stringArguments = {args[1], args[2] };
        formattedString = string.Format(formatString, stringArguments);
    }
    return formattedString;
});

string cardJson = template.Expand(context);
```

## <a name="troubleshooting"></a>Диагностика
Вопрос. Почему AdaptiveTemplateException вызывает ```expand()```?   
А) Вы можете получить такое сообщение об ошибке: "\<offending item>" в строке \<line number> **неправильно сформирован для пары "$data:"** .   
Убедитесь, что заданное для $data значение является допустимым в JSON (числовым или логическим значением, объектом или массивом) или соответствует правильному синтаксису для языка шаблона адаптивных карточек, а запись существует в контексте данных по номеру строки.

Вопрос. Почему ArgumentNullException вызывает ```expand()```?   
А) Вы можете получить такое сообщение об ошибке: "**Проверьте, установлен ли родительский контекст данных, или введите значение, отличающееся от NULL, для** "\<offending item>" в строке \<line number>.   
Это свидетельствует о том, что контекст данных для запрошенной привязки данных отсутствует. Убедитесь, что задан корневой контекст данных, если он существует, и что для текущей привязки доступен любой контекст данных в соответствии с номером строки.

Вопрос. Почему формат даты и времени RFC 3389, например "2017-02-14T06:08:00Z", при использовании с шаблоном не работает с функциями TIME и DATE?   
А) Такое поведение наблюдается в пакете NuGet для SDK .NET версии 1.0.0-rc.0. Это поведение исправлено в последующих версиях. По умолчанию десерилизатор json.Net меняет строки в формате даты и времени. Но такое поведение отсутствует в последующих выпусках. Используйте функцию formatDateTime() для форматирования строки даты и времени в соответствии со стандартом RFC 3389, как показано в [этом примере](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28). Либо вместо функций TIME и DATE вы можете использовать функции formatDateTime(). Дополнительные сведения о formatDateTime() см. [здесь](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).
