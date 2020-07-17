---
title: Собственный стиль — пакет SDK для UWP
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3c7616ce4fe307eda3073f7037842e3e3df81b
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417517"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="d3a82-102">Собственный стиль — UWP</span><span class="sxs-lookup"><span data-stu-id="d3a82-102">Native styling - UWP</span></span>

<span data-ttu-id="d3a82-103">Несмотря на то, что конфигурация узла будет наиболее актуальна на каждой платформе, вполне вероятно, что на каждой платформе придется выполнять некоторые собственные стили.</span><span class="sxs-lookup"><span data-stu-id="d3a82-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="d3a82-104">UWP делает это простым, позволяя передавать ResourceDictionary для детализированного стиля, поведения, анимации и т. д.</span><span class="sxs-lookup"><span data-stu-id="d3a82-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="d3a82-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="d3a82-105">Element</span></span> | <span data-ttu-id="d3a82-106">Имена стилей</span><span class="sxs-lookup"><span data-stu-id="d3a82-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="d3a82-107">AdaptiveCard (адаптивная карточка)</span><span class="sxs-lookup"><span data-stu-id="d3a82-107">AdaptiveCard</span></span> | <span data-ttu-id="d3a82-108">Адаптивный адаптер</span><span class="sxs-lookup"><span data-stu-id="d3a82-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="d3a82-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d3a82-109">Action.OpenUrl</span></span>  | <span data-ttu-id="d3a82-110">Адаптивный. Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d3a82-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="d3a82-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="d3a82-111">Action.ShowCard</span></span> | <span data-ttu-id="d3a82-112">Адаптивный. Action. Шовкард</span><span class="sxs-lookup"><span data-stu-id="d3a82-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="d3a82-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="d3a82-113">Action.Submit</span></span>  | <span data-ttu-id="d3a82-114">Адаптивный. Action. Submit</span><span class="sxs-lookup"><span data-stu-id="d3a82-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="d3a82-115">Столбец</span><span class="sxs-lookup"><span data-stu-id="d3a82-115">Column</span></span> | <span data-ttu-id="d3a82-116">Адаптивный. столбец, адаптивный. действие. TAP</span><span class="sxs-lookup"><span data-stu-id="d3a82-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="d3a82-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="d3a82-117">ColumnSet</span></span> | <span data-ttu-id="d3a82-118">Адаптивный. столбец, адаптивный. Вертикалсепаратор</span><span class="sxs-lookup"><span data-stu-id="d3a82-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="d3a82-119">Контейнер</span><span class="sxs-lookup"><span data-stu-id="d3a82-119">Container</span></span> | <span data-ttu-id="d3a82-120">Адаптивный контейнер</span><span class="sxs-lookup"><span data-stu-id="d3a82-120">Adaptive.Container</span></span>|
| <span data-ttu-id="d3a82-121">Input. Choice</span><span class="sxs-lookup"><span data-stu-id="d3a82-121">Input.ChoiceSet</span></span> | <span data-ttu-id="d3a82-122">Адаптивный. input. Choice, адаптивный вход. Choice. ComboBox, адаптивный вход. Choice. CheckBox, адаптивный. input. Choice. Radio, адаптивный. input. Choice. Комбобокситем</span><span class="sxs-lookup"><span data-stu-id="d3a82-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="d3a82-123">Input. Date</span><span class="sxs-lookup"><span data-stu-id="d3a82-123">Input.Date</span></span> | <span data-ttu-id="d3a82-124">Адаптивный. input. Text. Date</span><span class="sxs-lookup"><span data-stu-id="d3a82-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="d3a82-125">Input. Number</span><span class="sxs-lookup"><span data-stu-id="d3a82-125">Input.Number</span></span> | <span data-ttu-id="d3a82-126">Адаптивный. input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="d3a82-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="d3a82-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="d3a82-127">Input.Text</span></span> | <span data-ttu-id="d3a82-128">Адаптивный. input. Text</span><span class="sxs-lookup"><span data-stu-id="d3a82-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="d3a82-129">Входной. время</span><span class="sxs-lookup"><span data-stu-id="d3a82-129">Input.Time</span></span> | <span data-ttu-id="d3a82-130">Адаптивный. input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="d3a82-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="d3a82-131">Input. toggle</span><span class="sxs-lookup"><span data-stu-id="d3a82-131">Input.Toggle</span></span>| <span data-ttu-id="d3a82-132">Адаптивный. input. toggle</span><span class="sxs-lookup"><span data-stu-id="d3a82-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="d3a82-133">Образ —</span><span class="sxs-lookup"><span data-stu-id="d3a82-133">Image</span></span>  | <span data-ttu-id="d3a82-134">Адаптивное изображение</span><span class="sxs-lookup"><span data-stu-id="d3a82-134">Adaptive.Image</span></span> |
| <span data-ttu-id="d3a82-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="d3a82-135">ImageSet</span></span>  | <span data-ttu-id="d3a82-136">Адаптивный. Imageing</span><span class="sxs-lookup"><span data-stu-id="d3a82-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="d3a82-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="d3a82-137">FactSet</span></span> | <span data-ttu-id="d3a82-138">Адаптивный факт, адаптивный факт. Title, адаптивный. факт. Value</span><span class="sxs-lookup"><span data-stu-id="d3a82-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="d3a82-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d3a82-139">TextBlock</span></span>  | <span data-ttu-id="d3a82-140">Адаптивный. TextBlock</span><span class="sxs-lookup"><span data-stu-id="d3a82-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="d3a82-141">Этот пример словаря ресурсов XAML, который задает для фона всех элементов TextBlock значение голубого языка.</span><span class="sxs-lookup"><span data-stu-id="d3a82-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="d3a82-142">Вам, возможно, потребуется нечто более сложное, чем это😁</span><span class="sxs-lookup"><span data-stu-id="d3a82-142">You will probably want something more advanced than this 😁</span></span>

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
```
