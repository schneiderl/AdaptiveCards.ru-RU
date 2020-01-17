---
title: Класс Кардрендереррегистратион — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 4254c1c3c0f275434fae2a92e20679b6fa136b16
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145988"
---
# <a name="cardrendererregistration"></a>кардрендереррегистратион

```csharp
public class CardRendererRegistration : Java.Lang.Object
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration
```

### <a name="summary"></a>Сводка

| Открытые методы | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](#registerfeatureregistration) |

## <a name="public-methods"></a>Открытые методы

--- 

### <a id="registerfeatureregistration"></a>регистерфеатуререгистратион
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

Регистрирует объект [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) для использования модулем подготовки карт.

| Параметры | |
| --- | --- |
| феатуререгистратион | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) |

#### <a name="sample"></a>Пример

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```