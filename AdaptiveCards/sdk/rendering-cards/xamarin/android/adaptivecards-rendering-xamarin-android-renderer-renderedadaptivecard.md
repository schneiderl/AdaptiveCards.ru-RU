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
# <a name="renderedadaptivecard"></a><span data-ttu-id="6176c-102">рендередадаптивекард</span><span class="sxs-lookup"><span data-stu-id="6176c-102">RenderedAdaptiveCard</span></span>

```csharp
public class RenderedAdaptiveCard : Java.Lang.Object
```

<span data-ttu-id="6176c-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="6176c-103">**Namespace**</span></span>

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a><span data-ttu-id="6176c-104">Сводка</span><span class="sxs-lookup"><span data-stu-id="6176c-104">Summary</span></span>

| <span data-ttu-id="6176c-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="6176c-105">Attributes</span></span> | |
| ---- | --- |
| <span data-ttu-id="6176c-106">AdaptiveCard (адаптивная карточка)</span><span class="sxs-lookup"><span data-stu-id="6176c-106">AdaptiveCard</span></span> | <span data-ttu-id="6176c-107">Логическое представление визуализированной адаптивной карты.</span><span class="sxs-lookup"><span data-stu-id="6176c-107">Logical representation of the rendered adaptive card.</span></span> |
| <span data-ttu-id="6176c-108">Элементы ввода данных</span><span class="sxs-lookup"><span data-stu-id="6176c-108">Inputs</span></span> | <span data-ttu-id="6176c-109">Словарь элемента ввода и сведения, добавленные пользователем.</span><span class="sxs-lookup"><span data-stu-id="6176c-109">Dictionary of input element and information added by the user.</span></span> |
| <span data-ttu-id="6176c-110">"Вид"</span><span class="sxs-lookup"><span data-stu-id="6176c-110">View</span></span> | <span data-ttu-id="6176c-111">Визуальный результат из процесса отрисовки.</span><span class="sxs-lookup"><span data-stu-id="6176c-111">Visual result from the rendering process.</span></span> |
| <span data-ttu-id="6176c-112">предупреждения;</span><span class="sxs-lookup"><span data-stu-id="6176c-112">Warnings</span></span> | <span data-ttu-id="6176c-113">Список предупреждений, полученных в процессе отрисовки.</span><span class="sxs-lookup"><span data-stu-id="6176c-113">List of warnings produced from the rendering process.</span></span> |

&nbsp;

| <span data-ttu-id="6176c-114">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="6176c-114">Public methods</span></span> | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](#addwarning) |

## <a name="public-methods"></a><span data-ttu-id="6176c-115">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="6176c-115">Public Methods</span></span>

---

### <a id="addwarning"></a><span data-ttu-id="6176c-116">аддварнинг</span><span class="sxs-lookup"><span data-stu-id="6176c-116">AddWarning</span></span>
<p style='text-align:right'><span data-ttu-id="6176c-117">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="6176c-117">Added in version 0.1</span></span></p>

```csharp
public void AddWarning (AdaptiveWarning warning)

```

<span data-ttu-id="6176c-118">Добавляет предупреждение в список предупреждений.</span><span class="sxs-lookup"><span data-stu-id="6176c-118">Adds a warning to the warning list.</span></span>

| <span data-ttu-id="6176c-119">Параметры</span><span class="sxs-lookup"><span data-stu-id="6176c-119">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="6176c-120">предупреждение</span><span class="sxs-lookup"><span data-stu-id="6176c-120">warning</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning``` |
