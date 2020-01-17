---
title: Конфигурация узла — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 554b32d9d088e82fb0fd48bec4b94340e843abeb
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146128"
---
# <a name="host-config---android"></a><span data-ttu-id="41cd2-102">Конфигурация узла — Android</span><span class="sxs-lookup"><span data-stu-id="41cd2-102">Host config - Android</span></span>

<span data-ttu-id="41cd2-103">Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг.</span><span class="sxs-lookup"><span data-stu-id="41cd2-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="41cd2-104">(Полное описание см. в [схеме конфигурации узла](../../../../rendering-cards/host-config.md) .)</span><span class="sxs-lookup"><span data-stu-id="41cd2-104">(See [Host Config Schema](../../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="41cd2-105">Чтобы создать объект ```HostConfig``` из строки, используйте метод ```DeserializeFromString``` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="41cd2-105">To create a ```HostConfig``` object from a string, use the ```DeserializeFromString``` method like this:</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

HostConfig Config = HostConfig.DeserializeFromString(configJson);
```