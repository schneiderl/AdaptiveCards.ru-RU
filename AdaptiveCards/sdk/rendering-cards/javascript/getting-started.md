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
# <a name="getting-started---javascript"></a>Приступая к работе — JavaScript

Как описано в [Начало работы](../../../authoring-cards/getting-started.md) странице, адаптивная карта является объектной моделью сериализованной карточки JSON. Это пакет SDK для JavaScript для создания HTML-кода на стороне клиента в браузере.

## <a name="install"></a>Установка

### <a name="node"></a>Узел

[![Установка NPM](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards
```

### <a name="cdn"></a>СЕТЬ

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Использование

### <a name="import-the-module"></a>Импорт модуля

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>Следующие шаги

См. подробнее о [визуализации карточек](render-a-card.md).
