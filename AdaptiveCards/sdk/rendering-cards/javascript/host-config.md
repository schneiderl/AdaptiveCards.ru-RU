---
title: Конфигурация узла — пакет SDK для JavaScript
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

Существует три способа настройки адаптивной визуализации карт: 
1. Конфигурация узла
2. Стилизация CSS
3. Отрисовка пользовательского элемента

### <a name="hostconfig"></a>хостконфиг 

[HostConfig](../../../rendering-cards/host-config.md) — это объект общей конфигурации, распознаваемый разными средствами визуализации. Он позволяет определять общие стили (семейство шрифтов, размеры шрифтов, интервалы) и функции (например максимальное количество действий), которые автоматически интерпретируются средством визуализации той или иной платформы. 

Он используется для того, чтобы собственный пользовательский интерфейс, создаваемый средствами визуализации различных платформ, выглядел как можно более похожим на этих платформах при минимальных усилиях разработчика.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```