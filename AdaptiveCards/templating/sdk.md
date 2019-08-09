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
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="2251e-102">Пакеты SDK для адаптивных шаблонов карт</span><span class="sxs-lookup"><span data-stu-id="2251e-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="2251e-103">Пакеты SDK для шаблонов адаптивной карты упрощают заполнение [шаблона карты](language.md) реальными данными на любой поддерживаемой платформе.</span><span class="sxs-lookup"><span data-stu-id="2251e-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="2251e-104">Дополнительные сведения о шаблонах [адаптивных карт](index.md) см. в этой статье.</span><span class="sxs-lookup"><span data-stu-id="2251e-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="2251e-105">Эти функции доступны **в предварительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="2251e-105">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="2251e-106">Ваш отзыв не только Добро пожаловать, но и важен для обеспечения того, чтобы мы доставлять нужные **вам** функции.</span><span class="sxs-lookup"><span data-stu-id="2251e-106">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>
> 
> <span data-ttu-id="2251e-107">Во время первоначальной предварительной версии доступен только пакет SDK для JavaScript, но вскоре будет получен пакет SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="2251e-107">During the initial preview only the JavaScript SDK is available, but a .NET SDK should arrive shortly.</span></span>

## <a name="javascript"></a><span data-ttu-id="2251e-108">JavaScript</span><span class="sxs-lookup"><span data-stu-id="2251e-108">JavaScript</span></span>

<span data-ttu-id="2251e-109">Библиотека [адаптивекардс-шаблонов](https://www.npmjs.com/package/adaptivecards-templating) доступна в NPM и с помощью CDN.</span><span class="sxs-lookup"><span data-stu-id="2251e-109">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="2251e-110">Полную документацию см. в ссылке на пакет.</span><span class="sxs-lookup"><span data-stu-id="2251e-110">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="2251e-111">NPM</span><span class="sxs-lookup"><span data-stu-id="2251e-111">npm</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="2251e-112">СЕТЬ</span><span class="sxs-lookup"><span data-stu-id="2251e-112">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a><span data-ttu-id="2251e-113">Использование</span><span class="sxs-lookup"><span data-stu-id="2251e-113">Usage</span></span>

<span data-ttu-id="2251e-114">В примере ниже предполагается, что вы также установили библиотеку [адаптивекардс](https://www.npmjs.com/package/adaptivecards) , чтобы подготовить карту.</span><span class="sxs-lookup"><span data-stu-id="2251e-114">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="2251e-115">Если вы не планируете отрисовку карты, то можете удалить `parse` код и. `render`</span><span class="sxs-lookup"><span data-stu-id="2251e-115">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net-coming-soon"></a><span data-ttu-id="2251e-116">.NET (*ожидается в ближайшее время*)</span><span class="sxs-lookup"><span data-stu-id="2251e-116">.NET (*coming soon*)</span></span>

<span data-ttu-id="2251e-117">ЕЩЕ НЕ РАБОТАЕТ:</span><span class="sxs-lookup"><span data-stu-id="2251e-117">NOT WORKING YET:</span></span> 

```console
nuget install AdaptiveCards.Templating
```
