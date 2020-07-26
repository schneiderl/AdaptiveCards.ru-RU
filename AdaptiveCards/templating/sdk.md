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
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="6753b-102">Пакеты SDK для работы с шаблонами адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="6753b-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="6753b-103">Пакеты SDK для работы с шаблонами адаптивных карточек упрощают заполнение [шаблона карточки](language.md) реальными данными на любой поддерживаемой платформе.</span><span class="sxs-lookup"><span data-stu-id="6753b-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="6753b-104">Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).</span><span class="sxs-lookup"><span data-stu-id="6753b-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="6753b-105">**Критические изменения** в **версии-кандидате за май 2020 г.**</span><span class="sxs-lookup"><span data-stu-id="6753b-105">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="6753b-106">Мы приложили немало усилий, чтобы этот выпуск увидел свет, и уже находимся на финишной прямой.</span><span class="sxs-lookup"><span data-stu-id="6753b-106">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="6753b-107">В окончательную версию нам пришлось внести небольшие критические изменения.</span><span class="sxs-lookup"><span data-stu-id="6753b-107">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="6753b-108">Критические изменения в версии за май 2020 г.</span><span class="sxs-lookup"><span data-stu-id="6753b-108">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="6753b-109">Синтаксис привязки изменен с `{...}` на `${...}`.</span><span class="sxs-lookup"><span data-stu-id="6753b-109">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="6753b-110">Например, вместо `"text": "Hello {name}"` теперь используется `"text": "Hello ${name}"`.</span><span class="sxs-lookup"><span data-stu-id="6753b-110">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="6753b-111">API JavaScript больше не содержит объект `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="6753b-111">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="6753b-112">Просто передайте данные в функцию `expand`.</span><span class="sxs-lookup"><span data-stu-id="6753b-112">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="6753b-113">Дополнительные сведения см. на [странице о пакете SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="6753b-113">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="6753b-114">API .NET был модернизирован для обеспечения более точного соответствия API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6753b-114">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="6753b-115">Полные сведения см. ниже.</span><span class="sxs-lookup"><span data-stu-id="6753b-115">Please below for full details.</span></span>

## <a name="javascript"></a><span data-ttu-id="6753b-116">JavaScript</span><span class="sxs-lookup"><span data-stu-id="6753b-116">JavaScript</span></span>

<span data-ttu-id="6753b-117">К библиотеке [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) можно получить с помощью npm и CDN.</span><span class="sxs-lookup"><span data-stu-id="6753b-117">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="6753b-118">Полную документацию см. по ссылке на пакет.</span><span class="sxs-lookup"><span data-stu-id="6753b-118">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="6753b-119">npm</span><span class="sxs-lookup"><span data-stu-id="6753b-119">npm</span></span>

<span data-ttu-id="6753b-120">[![Установка с помощью npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="6753b-120">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="6753b-121">CDN</span><span class="sxs-lookup"><span data-stu-id="6753b-121">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### <a name="usage"></a><span data-ttu-id="6753b-122">Использование</span><span class="sxs-lookup"><span data-stu-id="6753b-122">Usage</span></span>

<span data-ttu-id="6753b-123">В приведенном ниже примере предполагается, что вы также установили библиотеку [adaptivecards](https://www.npmjs.com/package/adaptivecards) для отрисовки карточек.</span><span class="sxs-lookup"><span data-stu-id="6753b-123">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="6753b-124">Если вы не планируете выполнять отрисовку карточек, то можете удалить код `parse` и `render`.</span><span class="sxs-lookup"><span data-stu-id="6753b-124">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="6753b-125">.NET</span><span class="sxs-lookup"><span data-stu-id="6753b-125">.NET</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="6753b-126">Версия-кандидат .NET станет доступной предположительно 23 мая.</span><span class="sxs-lookup"><span data-stu-id="6753b-126">The .NET Release Candidate will be available around 05/23.</span></span> <span data-ttu-id="6753b-127">Ищите версию `1.0.0-RC1`.</span><span class="sxs-lookup"><span data-stu-id="6753b-127">Look for version `1.0.0-RC1`</span></span>
>

<span data-ttu-id="6753b-128">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="6753b-128">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span>

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a><span data-ttu-id="6753b-129">Использование</span><span class="sxs-lookup"><span data-stu-id="6753b-129">Usage</span></span>

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

### <a name="custom-functions"></a><span data-ttu-id="6753b-130">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="6753b-130">Custom Functions</span></span>

<span data-ttu-id="6753b-131">В дополнение к предварительно созданным функциям в адаптивную библиотеку выражений можно добавлять пользовательские функции.</span><span class="sxs-lookup"><span data-stu-id="6753b-131">Custom functions can be added to Adaptive Expression Library in addition to the prebuilt functions.</span></span>

<span data-ttu-id="6753b-132">В примере ниже показано, как добавить пользовательскую функцию stringFormat для форматирования строки.</span><span class="sxs-lookup"><span data-stu-id="6753b-132">In the below example, stringFormat custom function is added, and the funtion is used to format a string.</span></span>
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

## <a name="troubleshooting"></a><span data-ttu-id="6753b-133">Диагностика</span><span class="sxs-lookup"><span data-stu-id="6753b-133">Troubleshooting</span></span>
<span data-ttu-id="6753b-134">Вопрос.</span><span class="sxs-lookup"><span data-stu-id="6753b-134">Q.</span></span> <span data-ttu-id="6753b-135">Почему AdaptiveTemplateException вызывает ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="6753b-135">Why am I running into an AdaptiveTemplateException calling ```expand()```?</span></span>   
<span data-ttu-id="6753b-136">А)</span><span class="sxs-lookup"><span data-stu-id="6753b-136">A.</span></span> <span data-ttu-id="6753b-137">Вы можете получить такое сообщение об ошибке: "\<offending item>" в строке \<line number> **неправильно сформирован для пары "$data:"** .</span><span class="sxs-lookup"><span data-stu-id="6753b-137">If your error message looks like '\<offending item>' at line, '\<line number>' is **malformed for '$data : ' pair**".</span></span>   
<span data-ttu-id="6753b-138">Убедитесь, что заданное для $data значение является допустимым в JSON (числовым или логическим значением, объектом или массивом) или соответствует правильному синтаксису для языка шаблона адаптивных карточек, а запись существует в контексте данных по номеру строки.</span><span class="sxs-lookup"><span data-stu-id="6753b-138">Please ensure that value provided for "$data" is valid json such as number, boolean, object, and array, or follows correct syntax for Adaptive Template language,  and the entry exists in the data context at the line number.</span></span>

<span data-ttu-id="6753b-139">Вопрос.</span><span class="sxs-lookup"><span data-stu-id="6753b-139">Q.</span></span> <span data-ttu-id="6753b-140">Почему ArgumentNullException вызывает ```expand()```?</span><span class="sxs-lookup"><span data-stu-id="6753b-140">Why am I running into an ArgumentNullException calling ```expand()```?</span></span>   
<span data-ttu-id="6753b-141">А)</span><span class="sxs-lookup"><span data-stu-id="6753b-141">A.</span></span> <span data-ttu-id="6753b-142">Вы можете получить такое сообщение об ошибке: "**Проверьте, установлен ли родительский контекст данных, или введите значение, отличающееся от NULL, для** "\<offending item>" в строке \<line number>.</span><span class="sxs-lookup"><span data-stu-id="6753b-142">If your error message looks like" **Check if parent data context is set, or please enter a non-null value for** '\<offending item>' at line, '\<line number>'".</span></span>   
<span data-ttu-id="6753b-143">Это свидетельствует о том, что контекст данных для запрошенной привязки данных отсутствует.</span><span class="sxs-lookup"><span data-stu-id="6753b-143">It indicates that there doesn't exist data context for the requested data binding.</span></span> <span data-ttu-id="6753b-144">Убедитесь, что задан корневой контекст данных, если он существует, и что для текущей привязки доступен любой контекст данных в соответствии с номером строки.</span><span class="sxs-lookup"><span data-stu-id="6753b-144">Please ensure that root data context is set, if exists, ensure that any data context is available for current binding as indicated by the line number.</span></span>

<span data-ttu-id="6753b-145">Вопрос.</span><span class="sxs-lookup"><span data-stu-id="6753b-145">Q.</span></span> <span data-ttu-id="6753b-146">Почему формат даты и времени RFC 3389, например "2017-02-14T06:08:00Z", при использовании с шаблоном не работает с функциями TIME и DATE?</span><span class="sxs-lookup"><span data-stu-id="6753b-146">Why date/time in RFC 3389 format e.g "2017-02-14T06:08:00Z" when used with template doesn't works with TIME/DATE functions?</span></span>   
<span data-ttu-id="6753b-147">А)</span><span class="sxs-lookup"><span data-stu-id="6753b-147">A.</span></span> <span data-ttu-id="6753b-148">Такое поведение наблюдается в пакете NuGet для SDK .NET версии 1.0.0-rc.0.</span><span class="sxs-lookup"><span data-stu-id="6753b-148">.NET sdk nuget version 1.0.0-rc.0 exhibits this behavior.</span></span> <span data-ttu-id="6753b-149">Это поведение исправлено в последующих версиях.</span><span class="sxs-lookup"><span data-stu-id="6753b-149">this behavior is corrected in the subsequent releases.</span></span> <span data-ttu-id="6753b-150">По умолчанию десерилизатор json.Net меняет строки в формате даты и времени. Но такое поведение отсутствует в последующих выпусках.</span><span class="sxs-lookup"><span data-stu-id="6753b-150">json.Net deserilizer's default behavior changes date/time format string, and it's disabled for the subsequent releases.</span></span> <span data-ttu-id="6753b-151">Используйте функцию formatDateTime() для форматирования строки даты и времени в соответствии со стандартом RFC 3389, как показано в [этом примере](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28). Либо вместо функций TIME и DATE вы можете использовать функции formatDateTime().</span><span class="sxs-lookup"><span data-stu-id="6753b-151">Please use formatDateTime() function to format the date/time string to RFC 3389 as seen in [this example](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28), or you can bypass TIME/DATE functions, and just use formatDateTime().</span></span> <span data-ttu-id="6753b-152">Дополнительные сведения о formatDateTime() см. [здесь](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).</span><span class="sxs-lookup"><span data-stu-id="6753b-152">For more information on formatDateTime(), please go [here](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).</span></span>
