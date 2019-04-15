---
title: Пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 9684b96bba5168a1f07549468274ce5d74c01820
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553466"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="0172b-102">Приступая к работе — JavaScript</span><span class="sxs-lookup"><span data-stu-id="0172b-102">Getting started - JavaScript</span></span>

<span data-ttu-id="0172b-103">Как было описано в [Приступая к работе](../../../authoring-cards/getting-started.md) страницы, инструмент Adaptive Cards — это объектная модель сериализации JSON карты.</span><span class="sxs-lookup"><span data-stu-id="0172b-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="0172b-104">Это пакет SDK JavaScript для создания клиентского HTML в браузере.</span><span class="sxs-lookup"><span data-stu-id="0172b-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0172b-105">**Критические изменения из v0.5**</span><span class="sxs-lookup"><span data-stu-id="0172b-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="0172b-106">Пакет переименован из `microsoft-adaptivecards` для `adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="0172b-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="0172b-107">Статический `AdaptiveCards.setHostConfig()` был перемещен в член экземпляра `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="0172b-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="0172b-108">Например, `myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="0172b-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="0172b-109">`HostConfig` вышла на то, что различные при переименовании и перемещении.</span><span class="sxs-lookup"><span data-stu-id="0172b-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="0172b-110">См. в разделе [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) конфигурации узла для текущей структуры</span><span class="sxs-lookup"><span data-stu-id="0172b-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="0172b-111">Также были внесены некоторые изменения схемы из v0.5 предварительной версии, которые являются [описанную в этой статье](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="0172b-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="0172b-112">Статический `renderCard()` функция была удалена, так как она была избыточных с методами класса.</span><span class="sxs-lookup"><span data-stu-id="0172b-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="0172b-113">Используйте `adaptiveCard.render()` как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="0172b-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="0172b-114">Установка</span><span class="sxs-lookup"><span data-stu-id="0172b-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="0172b-115">Узел</span><span class="sxs-lookup"><span data-stu-id="0172b-115">Node</span></span>

<span data-ttu-id="0172b-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="0172b-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="0172b-117">CDN</span><span class="sxs-lookup"><span data-stu-id="0172b-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="0172b-118">Использование</span><span class="sxs-lookup"><span data-stu-id="0172b-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="0172b-119">Импорт модуля</span><span class="sxs-lookup"><span data-stu-id="0172b-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="0172b-120">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="0172b-120">Next steps</span></span>

<span data-ttu-id="0172b-121">См. в разделе [визуализации карточки](render-a-card.md) для получения дальнейших указаний.</span><span class="sxs-lookup"><span data-stu-id="0172b-121">See [Render a card](render-a-card.md) for the next steps!</span></span>
