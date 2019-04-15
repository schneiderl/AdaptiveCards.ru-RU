---
title: Визуализации карт - пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 6e20e19d9b72c034675abc8e37f2493986127c20
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553126"
---
# <a name="render-a-card---javascript"></a><span data-ttu-id="03b93-102">Визуализации карт — JavaScript</span><span class="sxs-lookup"><span data-stu-id="03b93-102">Render a card - JavaScript</span></span>

<span data-ttu-id="03b93-103">Вот способ визуализации карт, с помощью пакета SDK для JavaScript.</span><span class="sxs-lookup"><span data-stu-id="03b93-103">Here's how to render a card using the JavaScript SDK.</span></span>

## <a name="usage"></a><span data-ttu-id="03b93-104">Использование</span><span class="sxs-lookup"><span data-stu-id="03b93-104">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="03b93-105">Импорт модуля</span><span class="sxs-lookup"><span data-stu-id="03b93-105">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="render-a-card"></a><span data-ttu-id="03b93-106">Визуализации карт</span><span class="sxs-lookup"><span data-stu-id="03b93-106">Render a card</span></span>

```js
// Author a card
// In practice you'll probably get this from a service
// see http://adaptivecards.io/samples/ for inspiration
var card = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/adaptive-card-50.png"
        },
        {
            "type": "TextBlock",
            "text": "Hello **Adaptive Cards!**"
        }
    ],
    "actions": [
        {
            "type": "Action.OpenUrl",
            "title": "Learn more",
            "url": "http://adaptivecards.io"
        },
        {
            "type": "Action.OpenUrl",
            "title": "GitHub",
            "url": "http://github.com/Microsoft/AdaptiveCards"
        }
    ]
};

// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Set the adaptive card's event handlers. onExecuteAction is invoked
// whenever an action is clicked in the card
adaptiveCard.onExecuteAction = function(action) { alert("Ow!"); }

// For markdown support you need a third-party library
// E.g., to use markdown-it, include in your HTML page:
//     <script type="text/javascript" src="https://unpkg.com/markdown-it/dist/markdown-it.js"></script>
// And add this code to replace the default markdown handler:
//     AdaptiveCards.processMarkdown = function(text) { return markdownit().render(text); }

// Parse the card payload
adaptiveCard.parse(card);

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();

// And finally insert it somewhere in your page:
document.body.appendChild(renderedCard);
```