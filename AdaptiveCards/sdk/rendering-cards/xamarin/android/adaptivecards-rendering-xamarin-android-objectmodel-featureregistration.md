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
# <a name="feature-registration"></a>Регистрация компонентов

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a>Сводка

| Открытые методы | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## <a name="public-methods"></a>Открытые методы

---

### <a id="addfeature"></a>аддфеатуре
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

Добавляет компонент, содержащий имя и версию, в регистрацию функции модуля подготовки отчетов.

| Параметры | |
| --- | --- |
| featureName | ```string``` |
| феатуреверсион | ```string``` |

#### <a name="sample"></a>Пример

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a>жетфеатуреверсион
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public string GetFeatureVersion (string featureName)
```

Извлекает версию для данного компонента. 

| Параметры | |
| --- | --- |
| featureName | ```string``` |

| Возвращает | |
| --- | --- |
| ```string``` | Версия функции для данного компонента |

#### <a name="sample"></a>Пример

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a>ремовефеатуре
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public void RemoveFeature (string featureName)
```

Удаляет заданную функцию из словаря функций.

| Параметры | |
| --- | --- |
| featureName | ```string``` |

#### <a name="sample"></a>Пример

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```