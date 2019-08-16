---
title: Пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 4a6030dda12ab8d9a1e5c387cec63d45e84660d8
ms.sourcegitcommit: aa044167fd0b32b485ea2ce014afcf0b332bf1a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69529842"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="99b4a-102">Приступая к работе — JavaScript</span><span class="sxs-lookup"><span data-stu-id="99b4a-102">Getting started - JavaScript</span></span>

<span data-ttu-id="99b4a-103">Как описано в [Начало работы](../../../authoring-cards/getting-started.md) странице, адаптивная карта является объектной моделью сериализованной карточки JSON.</span><span class="sxs-lookup"><span data-stu-id="99b4a-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="99b4a-104">Это пакет SDK для JavaScript для создания HTML-кода на стороне клиента в браузере.</span><span class="sxs-lookup"><span data-stu-id="99b4a-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

## <a name="install"></a><span data-ttu-id="99b4a-105">Установка</span><span class="sxs-lookup"><span data-stu-id="99b4a-105">Install</span></span>

### <a name="node"></a><span data-ttu-id="99b4a-106">Узел</span><span class="sxs-lookup"><span data-stu-id="99b4a-106">Node</span></span>

<span data-ttu-id="99b4a-107">[![Установка NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="99b4a-107">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards
```

### <a name="cdn"></a><span data-ttu-id="99b4a-108">СЕТЬ</span><span class="sxs-lookup"><span data-stu-id="99b4a-108">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="99b4a-109">Использование</span><span class="sxs-lookup"><span data-stu-id="99b4a-109">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="99b4a-110">Импорт модуля</span><span class="sxs-lookup"><span data-stu-id="99b4a-110">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="99b4a-111">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="99b4a-111">Next steps</span></span>

<span data-ttu-id="99b4a-112">См. подробнее о [визуализации карточек](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="99b4a-112">See [Render a card](render-a-card.md) for the next steps!</span></span>
