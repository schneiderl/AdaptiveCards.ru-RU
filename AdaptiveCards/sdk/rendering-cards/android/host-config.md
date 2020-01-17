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
# <a name="host-config---android"></a><span data-ttu-id="8a068-102">Конфигурация узла — Android</span><span class="sxs-lookup"><span data-stu-id="8a068-102">Host config - Android</span></span>

<span data-ttu-id="8a068-103">Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг.</span><span class="sxs-lookup"><span data-stu-id="8a068-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="8a068-104">(Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)</span><span class="sxs-lookup"><span data-stu-id="8a068-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="8a068-105">Чтобы создать объект Хостконфиг из строки, используйте метод Десериализефромстринг</span><span class="sxs-lookup"><span data-stu-id="8a068-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```