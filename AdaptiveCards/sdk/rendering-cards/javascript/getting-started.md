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
# <a name="getting-started---javascript"></a>Приступая к работе — JavaScript

Как было описано в [Приступая к работе](../../../authoring-cards/getting-started.md) страницы, инструмент Adaptive Cards — это объектная модель сериализации JSON карты. Это пакет SDK JavaScript для создания клиентского HTML в браузере.

> [!IMPORTANT]
> **Критические изменения из v0.5**
> 
> 1. Пакет переименован из `microsoft-adaptivecards` для `adaptivecards`
> 1. Статический `AdaptiveCards.setHostConfig()` был перемещен в член экземпляра `AdaptiveCard`. Например, `myCard.hostConfig = {}` 
> 1. `HostConfig` вышла на то, что различные при переименовании и перемещении. См. в разделе [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) конфигурации узла для текущей структуры
> 1. Также были внесены некоторые изменения схемы из v0.5 предварительной версии, которые являются [описанную в этой статье](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. Статический `renderCard()` функция была удалена, так как она была избыточных с методами класса. Используйте `adaptiveCard.render()` как описано ниже. 


## <a name="install"></a>Установка

### <a name="node"></a>Узел

[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>CDN

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

См. в разделе [визуализации карточки](render-a-card.md) для получения дальнейших указаний.
