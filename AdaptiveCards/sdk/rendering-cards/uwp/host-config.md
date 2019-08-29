---
title: Конфигурация узла — пакет SDK для UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 85c8807d2a368e00b414b427fae8a9f0253873c8
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553676"
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