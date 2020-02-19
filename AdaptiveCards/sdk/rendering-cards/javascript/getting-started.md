---
title: Пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 29786fe5e533e67558df88f58b1330aa6646b532
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454627"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="a85fe-102">Приступая к работе — JavaScript</span><span class="sxs-lookup"><span data-stu-id="a85fe-102">Getting started - JavaScript</span></span>

<span data-ttu-id="a85fe-103">Как описано в [Начало работы](../../../authoring-cards/getting-started.md) странице, адаптивная карта является объектной моделью сериализованной карточки JSON.</span><span class="sxs-lookup"><span data-stu-id="a85fe-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="a85fe-104">Это пакет SDK для JavaScript для создания HTML-кода на стороне клиента в браузере.</span><span class="sxs-lookup"><span data-stu-id="a85fe-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

## <a name="install"></a><span data-ttu-id="a85fe-105">Установка</span><span class="sxs-lookup"><span data-stu-id="a85fe-105">Install</span></span>

### <a name="node"></a><span data-ttu-id="a85fe-106">Узел</span><span class="sxs-lookup"><span data-stu-id="a85fe-106">Node</span></span>

<span data-ttu-id="a85fe-107">[![Установка с помощью npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="a85fe-107">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards
```

### <a name="cdn"></a><span data-ttu-id="a85fe-108">CDN</span><span class="sxs-lookup"><span data-stu-id="a85fe-108">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="a85fe-109">Использование</span><span class="sxs-lookup"><span data-stu-id="a85fe-109">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="a85fe-110">Импорт модуля</span><span class="sxs-lookup"><span data-stu-id="a85fe-110">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="a85fe-111">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="a85fe-111">Next steps</span></span>

<span data-ttu-id="a85fe-112">См. подробнее о [визуализации карточек](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="a85fe-112">See [Render a card](render-a-card.md) for the next steps!</span></span>
