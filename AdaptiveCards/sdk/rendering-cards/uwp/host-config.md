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
# <a name="host-config---uwp"></a><span data-ttu-id="92912-102">Конфигурация узла — UWP</span><span class="sxs-lookup"><span data-stu-id="92912-102">Host config - UWP</span></span>

<span data-ttu-id="92912-103">Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг.</span><span class="sxs-lookup"><span data-stu-id="92912-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="92912-104">(Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)</span><span class="sxs-lookup"><span data-stu-id="92912-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

> <span data-ttu-id="92912-105">Экземпляр объекта Хостконфиг будет создан с использованием значений по умолчанию, поэтому можно задать только те свойства, которые необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="92912-105">The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.</span></span>

<span data-ttu-id="92912-106">Пример.</span><span class="sxs-lookup"><span data-stu-id="92912-106">Example:</span></span>

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

> <span data-ttu-id="92912-107">Кроме того, можно загрузить Хостконфиг из строки JSON.</span><span class="sxs-lookup"><span data-stu-id="92912-107">Alternatively, you can load the HostConfig from a JSON string.</span></span>

<span data-ttu-id="92912-108">Пример.</span><span class="sxs-lookup"><span data-stu-id="92912-108">Example:</span></span>

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

<span data-ttu-id="92912-109">При передаче в Увпрендерер вы настраиваете Хостконфиг по умолчанию для использования для каждой отображаемой карты.</span><span class="sxs-lookup"><span data-stu-id="92912-109">When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.</span></span>