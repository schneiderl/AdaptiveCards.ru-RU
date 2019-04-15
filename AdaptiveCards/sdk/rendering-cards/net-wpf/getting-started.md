---
title: ПАКЕТ SDK ДЛЯ .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a3f63fc812c97014af06dd1a197b24c5d07361c2
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553626"
---
# <a name="getting-started---net-wpf"></a>Приступая к работе - .NET WPF

Как было описано в [Приступая к работе](../../../authoring-cards/getting-started.md) страницы, инструмент Adaptive Cards — это объектная модель сериализации JSON карты. Эта библиотека упрощает для подготовки к просмотру код JSON в пользовательский Интерфейс WPF, который можно использовать в приложении.

## <a name="nuget-install"></a>Программа установки NuGet

[![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Xceed расширенных входных пакетов

Этот дополнительный пакет улучшает адаптивной входные данные карты элементов управления WPF предоставляет без дополнительной настройки. Он имеет зависимость от `Extended.Wpf.Toolkit`

[![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Пример визуализатора WPF

![Снимок экрана визуализатора](../../../resources/media/tools/wpfvisualizer.png)

[Пример визуализатора WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карты, использующие WPF.  Объект `Host Config` встроенной в редактор для редактирования и просмотра параметров конфигурации узла. Сохраните эти параметры в формате JSON, чтобы использовать их при подготовке к просмотру в приложении.

## <a name="next-steps"></a>Следующие шаги

См. в разделе [визуализации карточки](render-a-card.md) для получения дальнейших указаний.
