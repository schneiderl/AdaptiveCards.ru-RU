---
title: HostConfig — пакет SDK .NET для WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 65e68c2c3e7fa244ba790afc3749912937ea8470
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454037"
---
# <a name="host-config---net-wpf"></a>HostConfig — .NET WPF

[HostConfig](../../../rendering-cards/host-config.md) — это объект общей конфигурации, распознаваемый разными средствами визуализации. Он позволяет определять общие стили (семейство шрифтов, размеры шрифтов, интервалы) и функции (например максимальное количество действий), которые автоматически интерпретируются средством визуализации той или иной платформы. 

Он используется для того, чтобы собственный пользовательский интерфейс, создаваемый средствами визуализации различных платформ, выглядел как можно более похожим на этих платформах при минимальных усилиях разработчика.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig()
{
    FontStyles = new FontStylesConfig()
    {
        Default = new FontStyleConfig()
        {
            FontFamily = "Consolas",
            FontSizes = {
                Small = 15,
                Default = 20,
                Medium = 25,
                Large = 30,
                ExtraLarge= 40
            }
        },
    }
};

// Or parse from JSON
renderer.HostConfig = AdaptiveHostConfig.FromJson(@"{
    ""fontStyles"": {
        ""default"": {
            ""fontFamily"": ""Consolas"",
            ""fontSizes"": {
                ""small"": 15,
                ""default"": 20,
                ""medium"": 25,
                ""large"": 30,
                ""extraLarge"": 40
            }
        }
    }}");
```
