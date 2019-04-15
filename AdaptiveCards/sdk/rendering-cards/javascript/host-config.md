---
title: Размещение config - пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 1809a022481e4fb28d2db454cfe90e07d09279ff
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553606"
---
# <a name="host-config---javascript"></a>Конфигурация узла — JavaScript

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a>Настройка

Чтобы изменить параметры отрисовки инструмент adaptive Cards 3 способами. 
1. Конфигурации узла
2. Дизайн CSS
3. Пользовательский элемент визуализации

### <a name="hostconfig"></a>HostConfig 

Объект [Host Config](../../../rendering-cards/host-config.md) является объектом общей конфигурации, понять все модули подготовки отчетов. Это позволяет определить общие стили, (например, семейство шрифтов, но размеры шрифтов, по умолчанию пробелы) и поведения (например, максимальное количество действий), которые будут интерпретироваться автоматически модулем подготовки каждой платформы. 

Целью является то, что собственного пользовательского интерфейса, создаваемых модулем подготовки каждой платформы, выглядят очень похоже, с минимумом усилий с вашей стороны.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```