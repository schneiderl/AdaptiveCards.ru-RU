---
title: Собственные стили - пакета SDK для универсальной платформы Windows
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3b95dc53c55c81fbbbbed6ee7605f86eb427a9
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552526"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="4cef0-102">Собственные стили - универсальной платформы Windows</span><span class="sxs-lookup"><span data-stu-id="4cef0-102">Native styling - UWP</span></span>

<span data-ttu-id="4cef0-103">Во время конфигурации узла можно получить большинство определенным способом существует на каждой платформе, вполне вероятно, что необходимо сделать некоторые собственные стили на каждой платформе.</span><span class="sxs-lookup"><span data-stu-id="4cef0-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="4cef0-104">UWP упрощает это, позволяя передавать ResourceDictionary для точного стилей, поведение, анимации, и т.д.</span><span class="sxs-lookup"><span data-stu-id="4cef0-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="4cef0-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="4cef0-105">Element</span></span> | <span data-ttu-id="4cef0-106">Имена стилей</span><span class="sxs-lookup"><span data-stu-id="4cef0-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="4cef0-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="4cef0-107">AdaptiveCard</span></span> | <span data-ttu-id="4cef0-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="4cef0-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="4cef0-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="4cef0-109">Action.OpenUrl</span></span>  | <span data-ttu-id="4cef0-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="4cef0-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="4cef0-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="4cef0-111">Action.ShowCard</span></span> | <span data-ttu-id="4cef0-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="4cef0-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="4cef0-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="4cef0-113">Action.Submit</span></span>  | <span data-ttu-id="4cef0-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="4cef0-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="4cef0-115">Column</span><span class="sxs-lookup"><span data-stu-id="4cef0-115">Column</span></span> | <span data-ttu-id="4cef0-116">Adaptive.Column Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="4cef0-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="4cef0-117">Набор столбцов</span><span class="sxs-lookup"><span data-stu-id="4cef0-117">ColumnSet</span></span> | <span data-ttu-id="4cef0-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="4cef0-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="4cef0-119">Контейнер</span><span class="sxs-lookup"><span data-stu-id="4cef0-119">Container</span></span> | <span data-ttu-id="4cef0-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="4cef0-120">Adaptive.Container</span></span>|
| <span data-ttu-id="4cef0-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="4cef0-121">Input.ChoiceSet</span></span> | <span data-ttu-id="4cef0-122">Adaptive.Input.ChoiceSet, Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox, Adaptive.Input.ChoiceSet.Radio, Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="4cef0-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="4cef0-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="4cef0-123">Input.Date</span></span> | <span data-ttu-id="4cef0-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="4cef0-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="4cef0-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="4cef0-125">Input.Number</span></span> | <span data-ttu-id="4cef0-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="4cef0-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="4cef0-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="4cef0-127">Input.Text</span></span> | <span data-ttu-id="4cef0-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="4cef0-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="4cef0-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="4cef0-129">Input.Time</span></span> | <span data-ttu-id="4cef0-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="4cef0-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="4cef0-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="4cef0-131">Input.Toggle</span></span>| <span data-ttu-id="4cef0-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="4cef0-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="4cef0-133">Изображение</span><span class="sxs-lookup"><span data-stu-id="4cef0-133">Image</span></span>  | <span data-ttu-id="4cef0-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="4cef0-134">Adaptive.Image</span></span> |
| <span data-ttu-id="4cef0-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="4cef0-135">ImageSet</span></span>  | <span data-ttu-id="4cef0-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="4cef0-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="4cef0-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="4cef0-137">FactSet</span></span> | <span data-ttu-id="4cef0-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="4cef0-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="4cef0-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="4cef0-139">TextBlock</span></span>  | <span data-ttu-id="4cef0-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="4cef0-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="4cef0-141">Словарь ресурсов XAML, задает голубой фон все блоки TextBlock.</span><span class="sxs-lookup"><span data-stu-id="4cef0-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="4cef0-142">Возможно, вы захотите, что что-то более сложные превышает это 😁</span><span class="sxs-lookup"><span data-stu-id="4cef0-142">You will probably want something more advanced than this 😁</span></span>

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
```
