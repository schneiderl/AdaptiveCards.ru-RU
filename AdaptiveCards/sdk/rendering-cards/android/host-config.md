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
# <a name="host-config---android"></a><span data-ttu-id="561d0-102">Конфигурации узла - Android</span><span class="sxs-lookup"><span data-stu-id="561d0-102">Host config - Android</span></span>

<span data-ttu-id="561d0-103">Чтобы настроить модуль подготовки отчетов предоставления экземпляра объекта HostConfig.</span><span class="sxs-lookup"><span data-stu-id="561d0-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="561d0-104">(См. в разделе [схема Config узла](../../../rendering-cards/host-config.md) для полного описания.)</span><span class="sxs-lookup"><span data-stu-id="561d0-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="561d0-105">Чтобы создать объект HostConfig из строки, используйте метод DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="561d0-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```