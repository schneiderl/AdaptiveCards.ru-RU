---
title: ПАКЕТ SDK ДЛЯ .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 999f8ac3cd6a18fbbfc8b8bbdcf47465d8bb314f
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454287"
---
# <a name="getting-started---net-wpf"></a>Приступая к работе — .NET WPF

Как описано в [Начало работы](../../../authoring-cards/getting-started.md) странице, адаптивная карта является объектной моделью сериализованной карточки JSON. Эта библиотека упрощает визуализацию JSON в пользовательском интерфейсе WPF, который можно использовать в приложении.

## <a name="nuget-install"></a>Установка NuGet

[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Расширенный входной пакет ксцеед

Этот необязательный пакет расширяет возможности управления входными данными адаптивных карт, помимо того, что WPF предоставляет по своему желанию. Он зависит от `Extended.Wpf.Toolkit`

[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Пример визуализатора WPF

![Снимок экрана визуализатора](../../../resources/media/tools/wpfvisualizer.png)

[Пример визуализатора WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карты с помощью WPF.  Доступен встроенный редактор `Host Config`, в котором можно редактировать и просматривать параметры HostConfig. Сохраните эти параметры в JSON-файл, чтобы использовать их для отрисовки в своем приложении.

## <a name="next-steps"></a>Следующие шаги

См. подробнее о [визуализации карточек](render-a-card.md).
