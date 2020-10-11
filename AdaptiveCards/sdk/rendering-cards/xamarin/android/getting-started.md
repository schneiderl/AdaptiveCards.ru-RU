---
title: Пакет SDK Xamarin.Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: cd8dccd2aece23dd67ee8d601e8efaa2a1bcd4f2
ms.sourcegitcommit: 588f3e97ed3de96dfff54906ac666ce42ef1e7f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928834"
---
# <a name="getting-started---xamarinandroid"></a>Начало работы — Xamarin. Android

Это библиотека модуля подготовки отчетов, предназначенная для собственных приложений Xamarin Android и основанная на модуле подготовки Android, который можно найти [здесь](../../android/getting-started.md). 

## <a name="nuget-install"></a>Установка NuGet

[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)

Опубликованные пакеты можно найти [здесь](http://nuget.org) .

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## <a name="namespace"></a>Пространство имен

Необходимые пространства имен для использования этой библиотеки
```csharp
// To import the base object model classes as AdaptiveCard, TextBlock, Column, ShowCardAction, ...
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;

// To import the AdaptiveCardRenderer class
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;

// To import the ICardActionHandler interface
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;

// To use feature registration and register custom behaviour 
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration;
```

## <a name="xamarinandroid-visualizer-sample"></a>Пример визуализатора Xamarin. Android

[Пример визуализатора Xamarin. Android](https://github.com/Microsoft/AdaptiveCards/tree/main/source/xamarin/Xamarin.Droid.Sample) позволяет визуализировать карты с помощью Xamarin. Android. Если вы когда-либо использовали пример приложения для Android, вы увидите, что он действительно похож.

## <a name="next-steps"></a>Дальнейшие шаги

Для быстрого начала проверьте [Отображение карты](render-a-card.md) для следующих шагов.

Чтобы получить более подробные сведения о классах, привязанных к библиотеке модуля подготовки отчетов Xamarin. Android, можно проверить некоторые связываемые классы, щелкнув их ниже:
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)
