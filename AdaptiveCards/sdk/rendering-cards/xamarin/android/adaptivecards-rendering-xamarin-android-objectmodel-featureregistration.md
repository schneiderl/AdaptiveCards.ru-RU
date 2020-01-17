---
title: Класс Феатуререгистратион — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: c1975197996e54626b464abe9181f0b02895ee4d
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146148"
---
# <a name="feature-registration"></a><span data-ttu-id="16b75-102">Регистрация компонентов</span><span class="sxs-lookup"><span data-stu-id="16b75-102">Feature Registration</span></span>

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

<span data-ttu-id="16b75-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="16b75-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a><span data-ttu-id="16b75-104">Сводка</span><span class="sxs-lookup"><span data-stu-id="16b75-104">Summary</span></span>

| <span data-ttu-id="16b75-105">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="16b75-105">Public methods</span></span> | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## <a name="public-methods"></a><span data-ttu-id="16b75-106">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="16b75-106">Public Methods</span></span>

---

### <a id="addfeature"></a><span data-ttu-id="16b75-107">аддфеатуре</span><span class="sxs-lookup"><span data-stu-id="16b75-107">AddFeature</span></span>
<p style='text-align:right'><span data-ttu-id="16b75-108">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="16b75-108">Added in version 0.1.0</span></span></p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

<span data-ttu-id="16b75-109">Добавляет компонент, содержащий имя и версию, в регистрацию функции модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="16b75-109">Adds a feature containing its name and version to the renderer feature registration.</span></span>

| <span data-ttu-id="16b75-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="16b75-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="16b75-111">featureName</span><span class="sxs-lookup"><span data-stu-id="16b75-111">featureName</span></span> | ```string``` |
| <span data-ttu-id="16b75-112">феатуреверсион</span><span class="sxs-lookup"><span data-stu-id="16b75-112">featureVersion</span></span> | ```string``` |

#### <a name="sample"></a><span data-ttu-id="16b75-113">Пример</span><span class="sxs-lookup"><span data-stu-id="16b75-113">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a><span data-ttu-id="16b75-114">жетфеатуреверсион</span><span class="sxs-lookup"><span data-stu-id="16b75-114">GetFeatureVersion</span></span>
<p style='text-align:right'><span data-ttu-id="16b75-115">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="16b75-115">Added in version 0.1.0</span></span></p>

```csharp
public string GetFeatureVersion (string featureName)
```

<span data-ttu-id="16b75-116">Извлекает версию для данного компонента.</span><span class="sxs-lookup"><span data-stu-id="16b75-116">Retrieves the version for a given feature.</span></span> 

| <span data-ttu-id="16b75-117">Параметры</span><span class="sxs-lookup"><span data-stu-id="16b75-117">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="16b75-118">featureName</span><span class="sxs-lookup"><span data-stu-id="16b75-118">featureName</span></span> | ```string``` |

| <span data-ttu-id="16b75-119">Возвращает</span><span class="sxs-lookup"><span data-stu-id="16b75-119">Returns</span></span> | |
| --- | --- |
| ```string``` | <span data-ttu-id="16b75-120">Версия функции для данного компонента</span><span class="sxs-lookup"><span data-stu-id="16b75-120">Feature version for the given feature</span></span> |

#### <a name="sample"></a><span data-ttu-id="16b75-121">Пример</span><span class="sxs-lookup"><span data-stu-id="16b75-121">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a><span data-ttu-id="16b75-122">ремовефеатуре</span><span class="sxs-lookup"><span data-stu-id="16b75-122">RemoveFeature</span></span>
<p style='text-align:right'><span data-ttu-id="16b75-123">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="16b75-123">Added in version 0.1.0</span></span></p>

```csharp
public void RemoveFeature (string featureName)
```

<span data-ttu-id="16b75-124">Удаляет заданную функцию из словаря функций.</span><span class="sxs-lookup"><span data-stu-id="16b75-124">Removes the given feature from the feature dictionary.</span></span>

| <span data-ttu-id="16b75-125">Параметры</span><span class="sxs-lookup"><span data-stu-id="16b75-125">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="16b75-126">featureName</span><span class="sxs-lookup"><span data-stu-id="16b75-126">featureName</span></span> | ```string``` |

#### <a name="sample"></a><span data-ttu-id="16b75-127">Пример</span><span class="sxs-lookup"><span data-stu-id="16b75-127">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```