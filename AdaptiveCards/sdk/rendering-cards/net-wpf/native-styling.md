---
title: Собственный стиль — пакет SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 204845f942be4e7d04e20e9cd64d826daef26e93
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454027"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="983f6-102">Собственный стиль — .NET WPF</span><span class="sxs-lookup"><span data-stu-id="983f6-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="983f6-103">Несмотря на то, что конфигурация узла будет наиболее актуальна на каждой платформе, вполне вероятно, что на каждой платформе придется выполнять некоторые собственные стили.</span><span class="sxs-lookup"><span data-stu-id="983f6-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="983f6-104">WPF упрощает эту задачу, позволяя передавать ResourceDictionary для детализированного стиля, поведения, анимации и т. д.</span><span class="sxs-lookup"><span data-stu-id="983f6-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="983f6-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="983f6-105">Element</span></span> | <span data-ttu-id="983f6-106">Имена стилей</span><span class="sxs-lookup"><span data-stu-id="983f6-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="983f6-107">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="983f6-107">AdaptiveCard</span></span> | <span data-ttu-id="983f6-108">Адаптивный адаптер</span><span class="sxs-lookup"><span data-stu-id="983f6-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="983f6-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="983f6-109">Action.OpenUrl</span></span>  | <span data-ttu-id="983f6-110">Адаптивный. Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="983f6-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="983f6-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="983f6-111">Action.ShowCard</span></span> | <span data-ttu-id="983f6-112">Адаптивный. Action. Шовкард</span><span class="sxs-lookup"><span data-stu-id="983f6-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="983f6-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="983f6-113">Action.Submit</span></span>  | <span data-ttu-id="983f6-114">Адаптивный. Action. Submit</span><span class="sxs-lookup"><span data-stu-id="983f6-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="983f6-115">Column</span><span class="sxs-lookup"><span data-stu-id="983f6-115">Column</span></span> | <span data-ttu-id="983f6-116">Адаптивный. столбец, адаптивный. действие. TAP</span><span class="sxs-lookup"><span data-stu-id="983f6-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="983f6-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="983f6-117">ColumnSet</span></span> | <span data-ttu-id="983f6-118">Адаптивный. столбец, адаптивный. Вертикалсепаратор</span><span class="sxs-lookup"><span data-stu-id="983f6-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="983f6-119">Контейнер</span><span class="sxs-lookup"><span data-stu-id="983f6-119">Container</span></span> | <span data-ttu-id="983f6-120">Адаптивный контейнер</span><span class="sxs-lookup"><span data-stu-id="983f6-120">Adaptive.Container</span></span>|
| <span data-ttu-id="983f6-121">Input. Choice</span><span class="sxs-lookup"><span data-stu-id="983f6-121">Input.ChoiceSet</span></span> | <span data-ttu-id="983f6-122">Адаптивный. input. Choice, адаптивный вход. Choice. ComboBox, адаптивный вход. Choice. CheckBox, адаптивный. input. Choice. Radio, адаптивный. input. Choice. Комбобокситем</span><span class="sxs-lookup"><span data-stu-id="983f6-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="983f6-123">Input. Date</span><span class="sxs-lookup"><span data-stu-id="983f6-123">Input.Date</span></span> | <span data-ttu-id="983f6-124">Адаптивный. input. Text. Date</span><span class="sxs-lookup"><span data-stu-id="983f6-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="983f6-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="983f6-125">Input.Number</span></span> | <span data-ttu-id="983f6-126">Адаптивный. input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="983f6-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="983f6-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="983f6-127">Input.Text</span></span> | <span data-ttu-id="983f6-128">Адаптивный. input. Text</span><span class="sxs-lookup"><span data-stu-id="983f6-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="983f6-129">Входной. время</span><span class="sxs-lookup"><span data-stu-id="983f6-129">Input.Time</span></span> | <span data-ttu-id="983f6-130">Адаптивный. input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="983f6-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="983f6-131">Input. toggle</span><span class="sxs-lookup"><span data-stu-id="983f6-131">Input.Toggle</span></span>| <span data-ttu-id="983f6-132">Адаптивный. input. toggle</span><span class="sxs-lookup"><span data-stu-id="983f6-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="983f6-133">Изображение</span><span class="sxs-lookup"><span data-stu-id="983f6-133">Image</span></span>  | <span data-ttu-id="983f6-134">Адаптивное изображение</span><span class="sxs-lookup"><span data-stu-id="983f6-134">Adaptive.Image</span></span> |
| <span data-ttu-id="983f6-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="983f6-135">ImageSet</span></span>  | <span data-ttu-id="983f6-136">Адаптивный. Imageing</span><span class="sxs-lookup"><span data-stu-id="983f6-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="983f6-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="983f6-137">FactSet</span></span> | <span data-ttu-id="983f6-138">Адаптивный факт, адаптивный факт. Title, адаптивный. факт. Value</span><span class="sxs-lookup"><span data-stu-id="983f6-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="983f6-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="983f6-139">TextBlock</span></span>  | <span data-ttu-id="983f6-140">Адаптивный. TextBlock</span><span class="sxs-lookup"><span data-stu-id="983f6-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="983f6-141">Этот пример словаря ресурсов XAML, который задает для фона всех элементов TextBlock значение голубого языка.</span><span class="sxs-lookup"><span data-stu-id="983f6-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="983f6-142">Вам, возможно, потребуется нечто более сложное, чем это 😁</span><span class="sxs-lookup"><span data-stu-id="983f6-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
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
> <span data-ttu-id="983f6-143">**Примечание о создании образа на стороне сервера** Модуль подготовки отчетов WPF предоставляет `RenderCardToImageAsync` метод, который можно использовать для создания образа на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="983f6-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="983f6-144">При использовании в этой среде необходимо использовать только свойство `ResourcesPath`.</span><span class="sxs-lookup"><span data-stu-id="983f6-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="983f6-145">Дополнительные сведения см. в документации по [рендерингу изображений](../net-image/getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="983f6-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>