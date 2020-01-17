---
title: Класс Рендередадаптивекард — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 608b28638ce6ed0a218cfc8dbbe73f22de1ab8cb
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145998"
---
# <a name="renderedadaptivecard"></a>рендередадаптивекард

```csharp
public class RenderedAdaptiveCard : Java.Lang.Object
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a>Сводка

| Атрибуты | |
| ---- | --- |
| AdaptiveCard (адаптивная карточка) | Логическое представление визуализированной адаптивной карты. |
| Элементы ввода данных | Словарь элемента ввода и сведения, добавленные пользователем. |
| "Вид" | Визуальный результат из процесса отрисовки. |
| предупреждения; | Список предупреждений, полученных в процессе отрисовки. |

&nbsp;

| Открытые методы | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](#addwarning) |

## <a name="public-methods"></a>Открытые методы

---

### <a id="addwarning"></a>аддварнинг
<p style='text-align:right'>Добавлено в версии 0,1</p>

```csharp
public void AddWarning (AdaptiveWarning warning)

```

Добавляет предупреждение в список предупреждений.

| Параметры | |
| --- | --- |
| предупреждение | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning``` |
