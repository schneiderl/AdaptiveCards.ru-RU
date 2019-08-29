---
title: Конфигурация узла — пакет SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: dc5b6767d5f8611111b56f30f05a7b5fc8d1cbf4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552416"
---
# <a name="host-config---net-html"></a>Конфигурация узла — HTML-код .NET

[HostConfig](../../../rendering-cards/host-config.md) — это объект общей конфигурации, распознаваемый разными средствами визуализации. Он позволяет определять общие стили (семейство шрифтов, размеры шрифтов, интервалы) и функции (например максимальное количество действий), которые автоматически интерпретируются средством визуализации той или иной платформы. 

Он используется для того, чтобы собственный пользовательский интерфейс, создаваемый средствами визуализации различных платформ, выглядел как можно более похожим на этих платформах при минимальных усилиях разработчика.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig() 
{
    FontFamily = "Comic Sans",
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
renderer.HostConfig  = AdaptiveHostConfig.FromJson(@"{
    ""fontFamily"": ""Comic Sans"",
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");
```