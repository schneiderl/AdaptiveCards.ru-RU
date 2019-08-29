---
title: Конфигурация узла — пакет SDK для Android
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
# <a name="host-config---android"></a>Конфигурация узла — Android

Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг. (Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)

Чтобы создать объект Хостконфиг из строки, используйте метод Десериализефромстринг

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```