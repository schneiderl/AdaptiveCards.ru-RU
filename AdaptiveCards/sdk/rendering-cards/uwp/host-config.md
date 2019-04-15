---
title: Размещение config - пакета SDK для универсальной платформы Windows
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
# <a name="host-config---uwp"></a>Конфигурации узла - универсальной платформы Windows

Чтобы настроить модуль подготовки отчетов предоставления экземпляра объекта HostConfig. (См. в разделе [схема Config узла](../../../rendering-cards/host-config.md) для полного описания.)

> Создается экземпляр объекта HostConfig со значениями по умолчанию, можно задавать только те свойства, которые вы хотите изменить.

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

> Кроме того можно загрузить HostConfig из строки JSON.

Пример.

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

При передаче его в UWPRenderer, устанавливаемое по умолчанию HostConfig для каждой карты, которые готовятся к просмотру.