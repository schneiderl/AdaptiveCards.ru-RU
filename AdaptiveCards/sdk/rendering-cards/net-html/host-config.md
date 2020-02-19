---
title: Конфигурация узла — пакет SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a51b64f5f9783a187d7c3eb56c563a1d4497d3e2
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454997"
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