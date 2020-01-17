---
title: Конфигурация узла — пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 091e2093c380affc8c895d069a2f52061b991d2f
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145494"
---
# <a name="host-config---android"></a>Конфигурация узла — Android

Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг. (Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)

Чтобы создать объект Хостконфиг из строки, используйте метод Десериализефромстринг

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```