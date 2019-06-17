---
title: Подготовка к просмотру карты внутри приложения
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 0a5f99268ce483fddd99f4493b386db796c3e9d2
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138097"
---
# <a name="rendering-cards-inside-your-application"></a>Подготовка к просмотру карты внутри приложения

Это просто для отрисовки карты адаптивной внутри приложения. Мы предоставляем пакеты SDK для всех распространенных платформ, а также предоставляют [подробные спецификации](implement-a-renderer.md) для создания собственных инструмент Adaptive Cards модуля подготовки отчетов.

1. **Установка пакета SDK для модуля подготовки отчетов** — для целевой платформы.
2. **Создать экземпляр модуля подготовки отчетов** — настроенное с обработчиками событий стиль, правила и действия приложения.
3. **Отображать карту собственного пользовательского интерфейса** — автоматически со стилем в приложение.

## <a name="adaptive-cards-sdks"></a>Пакеты SDK адаптивной карты

|Платформа|Установка|Сборка|Документы|Состояние|
|---|---|---|---|---|
| JavaScript | [![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Документация](../sdk/rendering-cards/javascript/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Документация](../sdk/rendering-cards/net-wpf/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Документация](../sdk/rendering-cards/net-html/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Документация](../sdk/rendering-cards/uwp/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Документация](../sdk/rendering-cards/android/getting-started.md) | ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Документация](../sdk/rendering-cards/ios/getting-started.md) |  ![Состояние сборки](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Создайте экземпляр модуля подготовки отчетов

Следующим шагом является создание экземпляра `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Подключить события действия

По умолчанию действия будет отображаться в виде кнопок на карте, но он работает в приложение, чтобы сделать их ожиданиям. Каждый пакет SDK входит эквивалент `OnAction` событие, которое необходимо обработать.

* **Action.OpenUrl** -открыть указанный `url`.  
* **Action.Submit** - принимающей результат отправки с последующей отправкой к источнику. Как можно отправлять в источник карты — полностью на ваше усмотрение.
* **Action.ShowCard** — вызывает диалоговое окно и отображает карточке вложенные в этот диалог. Обратите внимание, что достаточно для обработки этого, если `ShowCardActionMode` присваивается `popup`.

## <a name="render-a-card"></a>Визуализации карт

После получения полезных данных карты, просто вызовите модуль подготовки отчетов и передайте в карточке. Вам потребуется получить собственный объект пользовательского интерфейса, состоящий из содержимого карты. Теперь просто поместите этот пользовательский Интерфейс где-то в приложении.

## <a name="customization"></a>Настройка

Существует несколько способов, которые можно настроить, что нужно отобразить. 

### <a name="hostconfig"></a>HostConfig

Объект [HostConfig](host-config.md) является объектом общего, кросс платформенных конфигурации, управляющий базовый стиль оформления и поведения карт в вашем приложении. Он определяет таких вещей, как размеры шрифтов, интервалы между элементами, цвета, число поддерживаемые действия и т. д. 

### <a name="native-platform-styling"></a>Стилизация собственной платформы

Большинство инфраструктур пользовательского интерфейса позволяют с помощью стилей framework собственного пользовательского интерфейса в стиле готовый для просмотра карты. Например в формате HTML можно указать классы CSS для HTML, или в XAML можно передать в пользовательских ResourceDictionary для точного управления выходных данных.

### <a name="customize-per-element-rendering"></a>Настройки отображения каждого элемента

Каждый пакет SDK позволяет переопределять способ отрисовки любого элемента, или даже добавить поддержку совершенно новых элементов, определенных вами.  Например, можно изменить `Input.Date` модуля подготовки отчетов, создавать собственный пользовательский элемент управления не теряя остальной части выходных данных модуля подготовки отчетов. Или можно добавить поддержку для пользовательской `Rating` элемент, который определяется.



