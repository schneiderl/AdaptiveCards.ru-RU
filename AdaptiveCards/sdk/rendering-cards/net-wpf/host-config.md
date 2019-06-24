---
title: HostConfig — пакет SDK .NET для WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 9ca540cbbb445f306f073f1936af46f8c2def99b
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134306"
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
