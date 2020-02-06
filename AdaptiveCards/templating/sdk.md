---
title: Пакеты SDK для создания шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 3a9bfcd1bf8f87959a747997e04f5c5ad2a79980
ms.sourcegitcommit: 90afb3729931b0e4cae19b17ef9e49453c2d2bf6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163613"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="13040-102">Пакеты SDK для работы с шаблонами адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="13040-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="13040-103">Пакеты SDK для работы с шаблонами адаптивных карточек упрощают заполнение [шаблона карточки](language.md) реальными данными на любой поддерживаемой платформе.</span><span class="sxs-lookup"><span data-stu-id="13040-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="13040-104">Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).</span><span class="sxs-lookup"><span data-stu-id="13040-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="13040-105">Эти функции предоставляются в **ознакомительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="13040-105">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="13040-106">Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.</span><span class="sxs-lookup"><span data-stu-id="13040-106">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>
> 
> <span data-ttu-id="13040-107">Во время действия первоначальной предварительной версии доступен только пакет SDK для JavaScript, но скоро будет предоставляться и пакет SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="13040-107">During the initial preview only the JavaScript SDK is available, but a .NET SDK should arrive shortly.</span></span>

## <a name="javascript"></a><span data-ttu-id="13040-108">JavaScript</span><span class="sxs-lookup"><span data-stu-id="13040-108">JavaScript</span></span>

<span data-ttu-id="13040-109">К библиотеке [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) можно получить с помощью npm и CDN.</span><span class="sxs-lookup"><span data-stu-id="13040-109">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="13040-110">Полную документацию см. по ссылке на пакет.</span><span class="sxs-lookup"><span data-stu-id="13040-110">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="13040-111">npm</span><span class="sxs-lookup"><span data-stu-id="13040-111">npm</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="13040-112">CDN</span><span class="sxs-lookup"><span data-stu-id="13040-112">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a><span data-ttu-id="13040-113">Использование</span><span class="sxs-lookup"><span data-stu-id="13040-113">Usage</span></span>

<span data-ttu-id="13040-114">В приведенном ниже примере предполагается, что вы также установили библиотеку [adaptivecards](https://www.npmjs.com/package/adaptivecards) для отрисовки карточек.</span><span class="sxs-lookup"><span data-stu-id="13040-114">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="13040-115">Если вы не планируете выполнять отрисовку карточек, то можете удалить код `parse` и `render`.</span><span class="sxs-lookup"><span data-stu-id="13040-115">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="13040-116">.NET</span><span class="sxs-lookup"><span data-stu-id="13040-116">.NET</span></span> 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> <span data-ttu-id="13040-117">Рекомендуем изменить указанную выше версию на последнюю опубликованную версию.</span><span class="sxs-lookup"><span data-stu-id="13040-117">Consider changing the version above to the latest published version</span></span>

<span data-ttu-id="13040-118">Импортируйте библиотеку.</span><span class="sxs-lookup"><span data-stu-id="13040-118">Import the library</span></span> 

```cs
using AdaptiveCards.Templating
```

<span data-ttu-id="13040-119">Используйте подсистему работы с шаблонами, передав шаблон и данные в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="13040-119">Use the templating engine by passing in your template JSON and data JSON.</span></span>

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
