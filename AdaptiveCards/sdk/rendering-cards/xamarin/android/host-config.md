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
# <a name="host-config---android"></a>Конфигурация узла — Android

Чтобы настроить модуль подготовки отчетов, укажите экземпляр объекта Хостконфиг. (Полное описание см. в [схеме конфигурации узла](../../../../rendering-cards/host-config.md) .)

Чтобы создать объект ```HostConfig``` из строки, используйте метод ```DeserializeFromString``` следующим образом:

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

HostConfig Config = HostConfig.DeserializeFromString(configJson);
```