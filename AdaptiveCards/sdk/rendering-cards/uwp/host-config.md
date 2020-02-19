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
# <a name="host-config---uwp"></a><span data-ttu-id="450f3-102">Конфигурация узла — UWP</span><span class="sxs-lookup"><span data-stu-id="450f3-102">Host config - UWP</span></span>

<span data-ttu-id="450f3-103">Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг.</span><span class="sxs-lookup"><span data-stu-id="450f3-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="450f3-104">(Полное описание см. в [схеме конфигурации узла](../../../rendering-cards/host-config.md) .)</span><span class="sxs-lookup"><span data-stu-id="450f3-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

> <span data-ttu-id="450f3-105">Экземпляр объекта Хостконфиг будет создан с использованием значений по умолчанию, поэтому можно задать только те свойства, которые необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="450f3-105">The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.</span></span>

<span data-ttu-id="450f3-106">Пример.</span><span class="sxs-lookup"><span data-stu-id="450f3-106">Example:</span></span>

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

> <span data-ttu-id="450f3-107">Кроме того, можно загрузить Хостконфиг из строки JSON.</span><span class="sxs-lookup"><span data-stu-id="450f3-107">Alternatively, you can load the HostConfig from a JSON string.</span></span>

<span data-ttu-id="450f3-108">Пример.</span><span class="sxs-lookup"><span data-stu-id="450f3-108">Example:</span></span>

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

<span data-ttu-id="450f3-109">При передаче в Увпрендерер вы настраиваете Хостконфиг по умолчанию для использования для каждой отображаемой карты.</span><span class="sxs-lookup"><span data-stu-id="450f3-109">When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.</span></span>