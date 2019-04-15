---
title: Собственные стили - пакета SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ee5bec1a11f39ad69d40e57410c105b50ba45981
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552726"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="2602b-102">Собственные стили - .NET WPF</span><span class="sxs-lookup"><span data-stu-id="2602b-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="2602b-103">Во время конфигурации узла можно получить большинство определенным способом существует на каждой платформе, вполне вероятно, что необходимо сделать некоторые собственные стили на каждой платформе.</span><span class="sxs-lookup"><span data-stu-id="2602b-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="2602b-104">WPF упрощает это, позволяя передавать ResourceDictionary для точного стилей, поведение, анимации, и т.д.</span><span class="sxs-lookup"><span data-stu-id="2602b-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="2602b-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="2602b-105">Element</span></span> | <span data-ttu-id="2602b-106">Имена стилей</span><span class="sxs-lookup"><span data-stu-id="2602b-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="2602b-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="2602b-107">AdaptiveCard</span></span> | <span data-ttu-id="2602b-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="2602b-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="2602b-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="2602b-109">Action.OpenUrl</span></span>  | <span data-ttu-id="2602b-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="2602b-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="2602b-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="2602b-111">Action.ShowCard</span></span> | <span data-ttu-id="2602b-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="2602b-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="2602b-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="2602b-113">Action.Submit</span></span>  | <span data-ttu-id="2602b-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="2602b-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="2602b-115">Column</span><span class="sxs-lookup"><span data-stu-id="2602b-115">Column</span></span> | <span data-ttu-id="2602b-116">Adaptive.Column Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="2602b-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="2602b-117">Набор столбцов</span><span class="sxs-lookup"><span data-stu-id="2602b-117">ColumnSet</span></span> | <span data-ttu-id="2602b-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="2602b-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="2602b-119">Контейнер</span><span class="sxs-lookup"><span data-stu-id="2602b-119">Container</span></span> | <span data-ttu-id="2602b-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="2602b-120">Adaptive.Container</span></span>|
| <span data-ttu-id="2602b-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="2602b-121">Input.ChoiceSet</span></span> | <span data-ttu-id="2602b-122">Adaptive.Input.ChoiceSet, Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox, Adaptive.Input.ChoiceSet.Radio, Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="2602b-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="2602b-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="2602b-123">Input.Date</span></span> | <span data-ttu-id="2602b-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="2602b-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="2602b-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="2602b-125">Input.Number</span></span> | <span data-ttu-id="2602b-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="2602b-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="2602b-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="2602b-127">Input.Text</span></span> | <span data-ttu-id="2602b-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="2602b-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="2602b-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="2602b-129">Input.Time</span></span> | <span data-ttu-id="2602b-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="2602b-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="2602b-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="2602b-131">Input.Toggle</span></span>| <span data-ttu-id="2602b-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="2602b-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="2602b-133">Изображение</span><span class="sxs-lookup"><span data-stu-id="2602b-133">Image</span></span>  | <span data-ttu-id="2602b-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="2602b-134">Adaptive.Image</span></span> |
| <span data-ttu-id="2602b-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="2602b-135">ImageSet</span></span>  | <span data-ttu-id="2602b-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="2602b-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="2602b-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="2602b-137">FactSet</span></span> | <span data-ttu-id="2602b-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="2602b-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="2602b-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="2602b-139">TextBlock</span></span>  | <span data-ttu-id="2602b-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="2602b-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="2602b-141">Словарь ресурсов XAML, задает голубой фон все блоки TextBlock.</span><span class="sxs-lookup"><span data-stu-id="2602b-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="2602b-142">Возможно, вы захотите, что что-то более сложные превышает это 😁</span><span class="sxs-lookup"><span data-stu-id="2602b-142">You will probably want something more advanced than this 😁</span></span>

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
> <span data-ttu-id="2602b-143">**Примечание о создании образов на сервере** визуализатор WPF предоставляет `RenderCardToImageAsync` метод, который может использоваться для создания изображений на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="2602b-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="2602b-144">Необходимо использовать только `ResourcesPath` свойства, если используется в этой среде.</span><span class="sxs-lookup"><span data-stu-id="2602b-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="2602b-145">См. в разделе [визуализация изображений](../net-image/getting-started.md) документы для получения дополнительных сведений</span><span class="sxs-lookup"><span data-stu-id="2602b-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>