---
title: Собственные стили - пакета SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 620940dee873742898d58979c61827320bc3c202
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552566"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="819df-102">Собственные стили - .NET HTML</span><span class="sxs-lookup"><span data-stu-id="819df-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="819df-103">Во время конфигурации узла можно получить большинство определенным способом существует на каждой платформе, вполне вероятно, что необходимо сделать некоторые собственные стили на каждой платформе.</span><span class="sxs-lookup"><span data-stu-id="819df-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="819df-104">HTML упрощает это, добавив классы CSS к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="819df-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="819df-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="819df-105">Element</span></span> | <span data-ttu-id="819df-106">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="819df-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="819df-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="819df-107">AdaptiveCard</span></span> | <span data-ttu-id="819df-108">AC-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="819df-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="819df-109">Все действия</span><span class="sxs-lookup"><span data-stu-id="819df-109">All Actions</span></span> | <span data-ttu-id="819df-110">AC кнопка</span><span class="sxs-lookup"><span data-stu-id="819df-110">ac-pushButton</span></span> | 
| <span data-ttu-id="819df-111">Выбор действия</span><span class="sxs-lookup"><span data-stu-id="819df-111">Select Actions</span></span> | <span data-ttu-id="819df-112">можно выбрать AC</span><span class="sxs-lookup"><span data-stu-id="819df-112">ac-selectable</span></span> |
| <span data-ttu-id="819df-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="819df-113">Action.OpenUrl</span></span>  | <span data-ttu-id="819df-114">AC действие openUrl</span><span class="sxs-lookup"><span data-stu-id="819df-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="819df-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="819df-115">Action.ShowCard</span></span> | <span data-ttu-id="819df-116">AC действие showCard</span><span class="sxs-lookup"><span data-stu-id="819df-116">ac-action-showCard</span></span> |
| <span data-ttu-id="819df-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="819df-117">Action.Submit</span></span>  | <span data-ttu-id="819df-118">AC действие submit</span><span class="sxs-lookup"><span data-stu-id="819df-118">ac-action-submit</span></span>  |
| <span data-ttu-id="819df-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="819df-119">ActionSet</span></span> | <span data-ttu-id="819df-120">AC-actionset</span><span class="sxs-lookup"><span data-stu-id="819df-120">ac-actionset</span></span> |
| <span data-ttu-id="819df-121">Column</span><span class="sxs-lookup"><span data-stu-id="819df-121">Column</span></span> | <span data-ttu-id="819df-122">AC столбец</span><span class="sxs-lookup"><span data-stu-id="819df-122">ac-column</span></span> |
| <span data-ttu-id="819df-123">Набор столбцов</span><span class="sxs-lookup"><span data-stu-id="819df-123">ColumnSet</span></span> | <span data-ttu-id="819df-124">AC-набор столбцов</span><span class="sxs-lookup"><span data-stu-id="819df-124">ac-columnset</span></span> |
| <span data-ttu-id="819df-125">Контейнер</span><span class="sxs-lookup"><span data-stu-id="819df-125">Container</span></span> | <span data-ttu-id="819df-126">AC контейнера</span><span class="sxs-lookup"><span data-stu-id="819df-126">ac-container</span></span> |
| <span data-ttu-id="819df-127">Все входные данные</span><span class="sxs-lookup"><span data-stu-id="819df-127">All Inputs</span></span> | <span data-ttu-id="819df-128">AC-входных данных</span><span class="sxs-lookup"><span data-stu-id="819df-128">ac-input</span></span> |
| <span data-ttu-id="819df-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="819df-129">Input.ChoiceSet</span></span> | <span data-ttu-id="819df-130">AC-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="819df-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="819df-131">Input.Date</span><span class="sxs-lookup"><span data-stu-id="819df-131">Input.Date</span></span> | <span data-ttu-id="819df-132">AC-dateInput</span><span class="sxs-lookup"><span data-stu-id="819df-132">ac-dateInput</span></span> |
| <span data-ttu-id="819df-133">Input.Number</span><span class="sxs-lookup"><span data-stu-id="819df-133">Input.Number</span></span> | <span data-ttu-id="819df-134">AC-numberInput</span><span class="sxs-lookup"><span data-stu-id="819df-134">ac-numberInput</span></span> |
| <span data-ttu-id="819df-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="819df-135">Input.Text</span></span> | <span data-ttu-id="819df-136">AC-textInput</span><span class="sxs-lookup"><span data-stu-id="819df-136">ac-textInput</span></span> |
| <span data-ttu-id="819df-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="819df-137">Input.Time</span></span> | <span data-ttu-id="819df-138">AC-timeInput</span><span class="sxs-lookup"><span data-stu-id="819df-138">ac-timeInput</span></span> |
| <span data-ttu-id="819df-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="819df-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="819df-140">Изображение</span><span class="sxs-lookup"><span data-stu-id="819df-140">Image</span></span>  | <span data-ttu-id="819df-141">AC-image</span><span class="sxs-lookup"><span data-stu-id="819df-141">ac-image</span></span> |
| <span data-ttu-id="819df-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="819df-142">ImageSet</span></span>  | <span data-ttu-id="819df-143">AC-imageset</span><span class="sxs-lookup"><span data-stu-id="819df-143">ac-imageset</span></span> |
| <span data-ttu-id="819df-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="819df-144">FactSet</span></span> | <span data-ttu-id="819df-145">AC-factset</span><span class="sxs-lookup"><span data-stu-id="819df-145">ac-factset</span></span> |
| <span data-ttu-id="819df-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="819df-146">TextBlock</span></span>  | <span data-ttu-id="819df-147">AC-textblock</span><span class="sxs-lookup"><span data-stu-id="819df-147">ac-textblock</span></span> |