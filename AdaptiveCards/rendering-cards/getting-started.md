---
title: Отрисовка карточек в приложении
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: a562a05a91676dc5e6d8b51690acc4788802fb99
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454937"
---
# <a name="rendering-cards-inside-your-application"></a>Отрисовка карточек в приложении

Вы можете легко отображать адаптивные карточки внутри приложения. Мы предоставляем пакеты SDK для всех распространенных платформ, а также предлагаем [подробную спецификацию](implement-a-renderer.md) для создания собственного отрисовщика адаптивных карточек.

1. **Установите пакет SDK отрисовщика** для целевой платформы.
2. **Создайте экземпляр отрисовщика**, настроенный с учетом стиля, правил и обработчиков событий действий своего приложения.
3. **Отобразите карточку в собственном пользовательском интерфейсе**, автоматически оформленную в стиле своего приложения.

## <a name="adaptive-cards-sdks"></a>Пакеты SDK адаптивных карточек

|Платформа|Установить|Создание|Docs|Состояние|
|---|---|---|---|---|
| JavaScript | [![Установка с помощью npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Источник](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Документация](../sdk/rendering-cards/javascript/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Источник](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Документация](../sdk/rendering-cards/net-wpf/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Источник](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Документация](../sdk/rendering-cards/net-html/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Универсальная платформа Windows | [![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Источник](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Документация](../sdk/rendering-cards/uwp/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Источник](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Документация](../sdk/rendering-cards/android/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Источник](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Документация](../sdk/rendering-cards/ios/getting-started.md) |  ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Создание экземпляра отрисовщика

Следующий шаг — создание экземпляра `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Перехват событий действий

По умолчанию действия отображаются в виде кнопок на карточке, но приложение может сделать их поведение таким, каким вам требуется. Каждый пакет SDK содержит эквивалент события `OnAction`, которое необходимо обрабатывать.

* **Action.OpenUrl**: открытие указанного `url`.  
* **Action.Submit**: получение результата отправки и его пересылка в источник. Способ отправки в источник карточки полностью зависит от вас.
* **Action.ShowCard**: вызывает диалоговое окно и отображает в нем вложенную карточку. Обратите внимание на то, что это действие нужно обрабатывать, только если параметр `ShowCardActionMode` имеет значение `popup`.

## <a name="render-a-card"></a>Визуализация карточки

После получения полезных данных карточки просто вызовите отрисовщик и передайте в него карточку. Вы получите объект собственного пользовательского интерфейса, состоящий из содержимого карточки. После этого его можно будет поместить в приложение.

## <a name="customization"></a>Настройка

Есть несколько способов настройки отрисовки объектов. 

### <a name="hostconfig"></a>HostConfig

[HostConfig](host-config.md) — это общий кроссплатформенный объект конфигурации, управляющий базовым стилем и поведением карточек внутри приложения. Он определяет размеры шрифтов, расстояния между элементами, цвета, число поддерживаемых действий и т. д. 

### <a name="native-platform-styling"></a>Стиль собственной платформы

Большинство платформ пользовательского интерфейса позволяет оформить отображаемую карточку в стиле платформы собственного пользовательского интерфейса. Например, в HTML можно указать классы CSS для HTML, а в XAML можно передать пользовательский объект ResourceDictionary для точного управления выводом.

### <a name="customize-per-element-rendering"></a>Настройка отрисовки каждого элемента

Каждый пакет SDK позволяет переопределить отрисовку любого элемента или даже добавить поддержку совершенно новых определяемых вами элементов.  Например, можно изменить отрисовщик `Input.Date` таким образом, чтобы он выдавал ваш пользовательский элемент управления, сохранив остальные выходные данные отрисовщика. Или можно добавить поддержку настраиваемого элемента `Rating`, который вы определяете.



