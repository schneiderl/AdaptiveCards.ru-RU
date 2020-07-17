---
title: Собственный стиль — пакет SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f9243fc6880c926c04f80f74713e91d1e37cf3d5
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417602"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="2d14e-102">Собственный стиль — .NET WPF</span><span class="sxs-lookup"><span data-stu-id="2d14e-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="2d14e-103">Несмотря на то, что конфигурация узла будет наиболее актуальна на каждой платформе, вполне вероятно, что на каждой платформе придется выполнять некоторые собственные стили.</span><span class="sxs-lookup"><span data-stu-id="2d14e-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="2d14e-104">WPF упрощает эту задачу, позволяя передавать ResourceDictionary для детализированного стиля, поведения, анимации и т. д.</span><span class="sxs-lookup"><span data-stu-id="2d14e-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="2d14e-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="2d14e-105">Element</span></span> | <span data-ttu-id="2d14e-106">Имена стилей</span><span class="sxs-lookup"><span data-stu-id="2d14e-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="2d14e-107">AdaptiveCard (адаптивная карточка)</span><span class="sxs-lookup"><span data-stu-id="2d14e-107">AdaptiveCard</span></span> | <span data-ttu-id="2d14e-108">Адаптивный адаптер</span><span class="sxs-lookup"><span data-stu-id="2d14e-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="2d14e-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="2d14e-109">Action.OpenUrl</span></span>  | <span data-ttu-id="2d14e-110">Адаптивный. Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="2d14e-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="2d14e-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="2d14e-111">Action.ShowCard</span></span> | <span data-ttu-id="2d14e-112">Адаптивный. Action. Шовкард</span><span class="sxs-lookup"><span data-stu-id="2d14e-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="2d14e-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="2d14e-113">Action.Submit</span></span>  | <span data-ttu-id="2d14e-114">Адаптивный. Action. Submit</span><span class="sxs-lookup"><span data-stu-id="2d14e-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="2d14e-115">Столбец</span><span class="sxs-lookup"><span data-stu-id="2d14e-115">Column</span></span> | <span data-ttu-id="2d14e-116">Адаптивный. столбец, адаптивный. действие. TAP</span><span class="sxs-lookup"><span data-stu-id="2d14e-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="2d14e-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="2d14e-117">ColumnSet</span></span> | <span data-ttu-id="2d14e-118">Адаптивный. столбец, адаптивный. Вертикалсепаратор</span><span class="sxs-lookup"><span data-stu-id="2d14e-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="2d14e-119">Контейнер</span><span class="sxs-lookup"><span data-stu-id="2d14e-119">Container</span></span> | <span data-ttu-id="2d14e-120">Адаптивный контейнер</span><span class="sxs-lookup"><span data-stu-id="2d14e-120">Adaptive.Container</span></span>|
| <span data-ttu-id="2d14e-121">Input. Choice</span><span class="sxs-lookup"><span data-stu-id="2d14e-121">Input.ChoiceSet</span></span> | <span data-ttu-id="2d14e-122">Адаптивный. input. Choice, адаптивный вход. Choice. ComboBox, адаптивный вход. Choice. CheckBox, адаптивный. input. Choice. Radio, адаптивный. input. Choice. Комбобокситем</span><span class="sxs-lookup"><span data-stu-id="2d14e-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="2d14e-123">Input. Date</span><span class="sxs-lookup"><span data-stu-id="2d14e-123">Input.Date</span></span> | <span data-ttu-id="2d14e-124">Адаптивный. input. Text. Date</span><span class="sxs-lookup"><span data-stu-id="2d14e-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="2d14e-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="2d14e-125">Input.Number</span></span> | <span data-ttu-id="2d14e-126">Адаптивный. input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="2d14e-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="2d14e-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="2d14e-127">Input.Text</span></span> | <span data-ttu-id="2d14e-128">Адаптивный. input. Text</span><span class="sxs-lookup"><span data-stu-id="2d14e-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="2d14e-129">Входной. время</span><span class="sxs-lookup"><span data-stu-id="2d14e-129">Input.Time</span></span> | <span data-ttu-id="2d14e-130">Адаптивный. input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="2d14e-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="2d14e-131">Input. toggle</span><span class="sxs-lookup"><span data-stu-id="2d14e-131">Input.Toggle</span></span>| <span data-ttu-id="2d14e-132">Адаптивный. input. toggle</span><span class="sxs-lookup"><span data-stu-id="2d14e-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="2d14e-133">Образ —</span><span class="sxs-lookup"><span data-stu-id="2d14e-133">Image</span></span>  | <span data-ttu-id="2d14e-134">Адаптивное изображение</span><span class="sxs-lookup"><span data-stu-id="2d14e-134">Adaptive.Image</span></span> |
| <span data-ttu-id="2d14e-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="2d14e-135">ImageSet</span></span>  | <span data-ttu-id="2d14e-136">Адаптивный. Imageing</span><span class="sxs-lookup"><span data-stu-id="2d14e-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="2d14e-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="2d14e-137">FactSet</span></span> | <span data-ttu-id="2d14e-138">Адаптивный факт, адаптивный факт. Title, адаптивный. факт. Value</span><span class="sxs-lookup"><span data-stu-id="2d14e-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="2d14e-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="2d14e-139">TextBlock</span></span>  | <span data-ttu-id="2d14e-140">Адаптивный. TextBlock</span><span class="sxs-lookup"><span data-stu-id="2d14e-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="2d14e-141">Этот пример словаря ресурсов XAML, который задает для фона всех элементов TextBlock значение голубого языка.</span><span class="sxs-lookup"><span data-stu-id="2d14e-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="2d14e-142">Вам, возможно, потребуется нечто более сложное, чем это😁</span><span class="sxs-lookup"><span data-stu-id="2d14e-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="https://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="https://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> <span data-ttu-id="2d14e-143">**Примечание о создании образа на стороне сервера** Модуль подготовки отчетов WPF предоставляет `RenderCardToImageAsync` метод, который можно использовать для создания образа на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="2d14e-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="2d14e-144">Свойство следует использовать только `ResourcesPath` в том случае, если оно используется в этой среде.</span><span class="sxs-lookup"><span data-stu-id="2d14e-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="2d14e-145">Дополнительные сведения см. в документации по [рендерингу изображений](../net-image/getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="2d14e-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>