---
title: Пакеты SDK для создания шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 05/15/2020
ms.topic: article
ms.openlocfilehash: d04b38d6b2a389ca31b690d3298f64b3fced7c9a
ms.sourcegitcommit: eb71aebe40a592649461e468a87993a10cbe6187
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/03/2020
ms.locfileid: "84318184"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="588ea-102">Пакеты SDK для работы с шаблонами адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="588ea-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="588ea-103">Пакеты SDK для работы с шаблонами адаптивных карточек упрощают заполнение [шаблона карточки](language.md) реальными данными на любой поддерживаемой платформе.</span><span class="sxs-lookup"><span data-stu-id="588ea-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="588ea-104">Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).</span><span class="sxs-lookup"><span data-stu-id="588ea-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="588ea-105">**Критические изменения** в **версии-кандидате за май 2020 г.**</span><span class="sxs-lookup"><span data-stu-id="588ea-105">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="588ea-106">Мы приложили немало усилий, чтобы этот выпуск увидел свет, и уже находимся на финишной прямой.</span><span class="sxs-lookup"><span data-stu-id="588ea-106">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="588ea-107">В окончательную версию нам пришлось внести небольшие критические изменения.</span><span class="sxs-lookup"><span data-stu-id="588ea-107">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="588ea-108">Критические изменения в версии за май 2020 г.</span><span class="sxs-lookup"><span data-stu-id="588ea-108">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="588ea-109">Синтаксис привязки изменен с `{...}` на `${...}`.</span><span class="sxs-lookup"><span data-stu-id="588ea-109">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="588ea-110">Например, вместо `"text": "Hello {name}"` теперь используется `"text": "Hello ${name}"`.</span><span class="sxs-lookup"><span data-stu-id="588ea-110">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="588ea-111">API JavaScript больше не содержит объект `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="588ea-111">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="588ea-112">Просто передайте данные в функцию `expand`.</span><span class="sxs-lookup"><span data-stu-id="588ea-112">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="588ea-113">Дополнительные сведения см. на [странице с описанием пакета SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="588ea-113">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="588ea-114">API .NET был модернизирован для обеспечения более точного соответствия API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="588ea-114">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="588ea-115">Полные сведения см. ниже.</span><span class="sxs-lookup"><span data-stu-id="588ea-115">Please below for full details.</span></span>

## <a name="javascript"></a><span data-ttu-id="588ea-116">JavaScript</span><span class="sxs-lookup"><span data-stu-id="588ea-116">JavaScript</span></span>

<span data-ttu-id="588ea-117">К библиотеке [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) можно получить с помощью npm и CDN.</span><span class="sxs-lookup"><span data-stu-id="588ea-117">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="588ea-118">Полную документацию см. по ссылке на пакет.</span><span class="sxs-lookup"><span data-stu-id="588ea-118">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="588ea-119">npm</span><span class="sxs-lookup"><span data-stu-id="588ea-119">npm</span></span>

<span data-ttu-id="588ea-120">[![Установка с помощью npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="588ea-120">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="588ea-121">CDN</span><span class="sxs-lookup"><span data-stu-id="588ea-121">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### <a name="usage"></a><span data-ttu-id="588ea-122">Использование</span><span class="sxs-lookup"><span data-stu-id="588ea-122">Usage</span></span>

<span data-ttu-id="588ea-123">В приведенном ниже примере предполагается, что вы также установили библиотеку [adaptivecards](https://www.npmjs.com/package/adaptivecards) для отрисовки карточек.</span><span class="sxs-lookup"><span data-stu-id="588ea-123">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="588ea-124">Если вы не планируете выполнять отрисовку карточек, то можете удалить код `parse` и `render`.</span><span class="sxs-lookup"><span data-stu-id="588ea-124">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="588ea-125">.NET</span><span class="sxs-lookup"><span data-stu-id="588ea-125">.NET</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="588ea-126">Версия-кандидат .NET станет доступной предположительно 23 мая.</span><span class="sxs-lookup"><span data-stu-id="588ea-126">The .NET Release Candidate will be available around 05/23.</span></span> <span data-ttu-id="588ea-127">Ищите версию `1.0.0-RC1`.</span><span class="sxs-lookup"><span data-stu-id="588ea-127">Look for version `1.0.0-RC1`</span></span>
>

<span data-ttu-id="588ea-128">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="588ea-128">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span>

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a><span data-ttu-id="588ea-129">Использование</span><span class="sxs-lookup"><span data-stu-id="588ea-129">Usage</span></span>

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

### <a name="custom-functions"></a><span data-ttu-id="588ea-130">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="588ea-130">Custom Functions</span></span>

<span data-ttu-id="588ea-131">В дополнение к предварительно созданным функциям в адаптивную библиотеку выражений можно добавлять пользовательские функции.</span><span class="sxs-lookup"><span data-stu-id="588ea-131">Custom functions can be added to Adaptive Expression Library in addition to the prebuilt functions.</span></span>

<span data-ttu-id="588ea-132">В примере ниже показано, как добавить пользовательскую функцию stringFormat для форматирования строки.</span><span class="sxs-lookup"><span data-stu-id="588ea-132">In the below example, stringFormat custom function is added, and the funtion is used to format a string.</span></span>
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

## <a name="troubleshooting"></a><span data-ttu-id="588ea-133">Диагностика</span><span class="sxs-lookup"><span data-stu-id="588ea-133">Troubleshooting</span></span>
<span data-ttu-id="588ea-134">Вопрос.</span><span class="sxs-lookup"><span data-stu-id="588ea-134">Q.</span></span> <span data-ttu-id="588ea-135">Почему AdaptiveTemplateException вызывает ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="588ea-135">Why am I running into an AdaptiveTemplateException calling ```expand()```?</span></span>   
<span data-ttu-id="588ea-136">А)</span><span class="sxs-lookup"><span data-stu-id="588ea-136">A.</span></span> <span data-ttu-id="588ea-137">Вы можете получить такое сообщение об ошибке: "\<offending item>" в строке \<line number> **неправильно сформирован для пары "$data:"** .</span><span class="sxs-lookup"><span data-stu-id="588ea-137">If your error message looks like '\<offending item>' at line, '\<line number>' is **malformed for '$data : ' pair**".</span></span>   
<span data-ttu-id="588ea-138">Убедитесь, что заданное для $data значение является допустимым в JSON (числовым или логическим значением, объектом или массивом) или соответствует правильному синтаксису для языка шаблона адаптивных карточек, а запись существует в контексте данных по номеру строки.</span><span class="sxs-lookup"><span data-stu-id="588ea-138">Please ensure that value provided for "$data" is valid json such as number, boolean, object, and array, or follows correct syntax for Adaptive Template language,  and the entry exists in the data context at the line number.</span></span> <span data-ttu-id="588ea-139">Обратите внимание, что значения ${LineItem} и 8 могут меняться.</span><span class="sxs-lookup"><span data-stu-id="588ea-139">Please note that ${LineItem} and '8' can change.</span></span>

<span data-ttu-id="588ea-140">Вопрос.</span><span class="sxs-lookup"><span data-stu-id="588ea-140">Q.</span></span> <span data-ttu-id="588ea-141">Почему ArgumentNullException вызывает ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="588ea-141">Why am I running into an ArgumentNullException calling ```expand()```?</span></span>   
<span data-ttu-id="588ea-142">А)</span><span class="sxs-lookup"><span data-stu-id="588ea-142">A.</span></span> <span data-ttu-id="588ea-143">Вы можете получить такое сообщение об ошибке: "**Проверьте, установлен ли родительский контекст данных, или введите значение, отличающееся от NULL, для** "\<offending item>" в строке \<line number>.</span><span class="sxs-lookup"><span data-stu-id="588ea-143">If your error message looks like" **Check if parent data context is set, or please enter a non-null value for** '\<offending item>' at line, '\<line number>'".</span></span>   
<span data-ttu-id="588ea-144">Это свидетельствует о том, что контекст данных для запрошенной привязки данных отсутствует.</span><span class="sxs-lookup"><span data-stu-id="588ea-144">It indicates that there doesn't exist data context for the requested data binding.</span></span> <span data-ttu-id="588ea-145">Убедитесь, что задан корневой контекст данных, если он существует, и что для текущей привязки доступен любой контекст данных в соответствии с номером строки.</span><span class="sxs-lookup"><span data-stu-id="588ea-145">Please ensure that root data context is set, if exists, ensure that any data context is available for current binding as indicated by the line number.</span></span>
