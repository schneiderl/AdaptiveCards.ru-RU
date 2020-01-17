---
title: Пакет SDK Xamarin.Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: a7fd40ac7f026e2a325e7dc52e10defe550fd43a
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146008"
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

[Пример визуализатора Xamarin. Android](https://github.com/Microsoft/AdaptiveCards/tree/master/source/xamarin/Xamarin.Droid.Sample) позволяет визуализировать карты с помощью Xamarin. Android. Если вы когда-либо использовали пример приложения для Android, вы увидите, что он действительно похож.

## <a name="next-steps"></a>Дальнейшие действия

Для быстрого начала проверьте [Отображение карты](render-a-card.md) для следующих шагов.

Чтобы получить более подробные сведения о классах, привязанных к библиотеке модуля подготовки отчетов Xamarin. Android, можно проверить некоторые связываемые классы, щелкнув их ниже:
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)