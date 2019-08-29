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
# <a name="host-config---android"></a><span data-ttu-id="30b2c-102">Конфигурация узла — Android</span><span class="sxs-lookup"><span data-stu-id="30b2c-102">Host config - Android</span></span>

<span data-ttu-id="30b2c-103">Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг.</span><span class="sxs-lookup"><span data-stu-id="30b2c-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="30b2c-104">(Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)</span><span class="sxs-lookup"><span data-stu-id="30b2c-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="30b2c-105">Чтобы создать объект Хостконфиг из строки, используйте метод Десериализефромстринг</span><span class="sxs-lookup"><span data-stu-id="30b2c-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```