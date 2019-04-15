---
title: Размещение config - пакета SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c44cf609fd52423a1ca17988a875c6dc48550007
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553346"
---
# <a name="host-config---android"></a>Конфигурации узла - Android

Чтобы настроить модуль подготовки отчетов предоставления экземпляра объекта HostConfig. (См. в разделе [схема Config узла](../../../rendering-cards/host-config.md) для полного описания.)

Чтобы создать объект HostConfig из строки, используйте метод DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```