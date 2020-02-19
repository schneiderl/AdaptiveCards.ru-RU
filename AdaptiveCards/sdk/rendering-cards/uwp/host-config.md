---
title: Конфигурация узла — пакет SDK для UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6f14830a643b064c6169cf3143bbc7cd4ce45937
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454977"
---
# <a name="host-config---uwp"></a>Конфигурация узла — UWP

Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг. (Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)

> Экземпляр объекта Хостконфиг будет создан с использованием значений по умолчанию, поэтому можно задать только те свойства, которые необходимо изменить.

Пример.

```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```

> Кроме того, можно загрузить Хостконфиг из строки JSON.

Пример.

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

При передаче в Увпрендерер вы настраиваете Хостконфиг по умолчанию для использования для каждой отображаемой карты.