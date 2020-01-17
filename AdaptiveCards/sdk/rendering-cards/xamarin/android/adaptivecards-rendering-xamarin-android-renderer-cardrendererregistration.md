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
# <a name="cardrendererregistration"></a><span data-ttu-id="ebf76-102">кардрендереррегистратион</span><span class="sxs-lookup"><span data-stu-id="ebf76-102">CardRendererRegistration</span></span>

```csharp
public class CardRendererRegistration : Java.Lang.Object
```

<span data-ttu-id="ebf76-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="ebf76-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration
```

### <a name="summary"></a><span data-ttu-id="ebf76-104">Сводка</span><span class="sxs-lookup"><span data-stu-id="ebf76-104">Summary</span></span>

| <span data-ttu-id="ebf76-105">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="ebf76-105">Public methods</span></span> | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](#registerfeatureregistration) |

## <a name="public-methods"></a><span data-ttu-id="ebf76-106">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="ebf76-106">Public Methods</span></span>

--- 

### <a id="registerfeatureregistration"></a><span data-ttu-id="ebf76-107">регистерфеатуререгистратион</span><span class="sxs-lookup"><span data-stu-id="ebf76-107">RegisterFeatureRegistration</span></span>
<p style='text-align:right'><span data-ttu-id="ebf76-108">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="ebf76-108">Added in version 0.1.0</span></span></p>

```csharp
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

<span data-ttu-id="ebf76-109">Регистрирует объект [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) для использования модулем подготовки карт.</span><span class="sxs-lookup"><span data-stu-id="ebf76-109">Registers a [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) object for the card renderer to use.</span></span>

| <span data-ttu-id="ebf76-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="ebf76-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="ebf76-111">феатуререгистратион</span><span class="sxs-lookup"><span data-stu-id="ebf76-111">featureRegistration</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) |

#### <a name="sample"></a><span data-ttu-id="ebf76-112">Пример</span><span class="sxs-lookup"><span data-stu-id="ebf76-112">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```