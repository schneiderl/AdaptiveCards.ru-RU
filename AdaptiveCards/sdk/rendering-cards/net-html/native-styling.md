---
title: Собственный стиль — пакет SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454497"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="4f8fe-102">Собственный стиль — HTML-код .NET</span><span class="sxs-lookup"><span data-stu-id="4f8fe-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="4f8fe-103">Несмотря на то, что конфигурация узла будет наиболее актуальна на каждой платформе, вполне вероятно, что на каждой платформе придется выполнять некоторые собственные стили.</span><span class="sxs-lookup"><span data-stu-id="4f8fe-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="4f8fe-104">HTML упрощает эту задачу, добавляя классы CSS к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="4f8fe-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="4f8fe-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="4f8fe-105">Element</span></span> | <span data-ttu-id="4f8fe-106">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="4f8fe-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="4f8fe-107">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="4f8fe-107">AdaptiveCard</span></span> | <span data-ttu-id="4f8fe-108">AC-адаптивекард</span><span class="sxs-lookup"><span data-stu-id="4f8fe-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="4f8fe-109">Все действия</span><span class="sxs-lookup"><span data-stu-id="4f8fe-109">All Actions</span></span> | <span data-ttu-id="4f8fe-110">Кнопка AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-110">ac-pushButton</span></span> | 
| <span data-ttu-id="4f8fe-111">Выбор действий</span><span class="sxs-lookup"><span data-stu-id="4f8fe-111">Select Actions</span></span> | <span data-ttu-id="4f8fe-112">Выбираемый AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-112">ac-selectable</span></span> |
| <span data-ttu-id="4f8fe-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="4f8fe-113">Action.OpenUrl</span></span>  | <span data-ttu-id="4f8fe-114">AC-Action-openUrl</span><span class="sxs-lookup"><span data-stu-id="4f8fe-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="4f8fe-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="4f8fe-115">Action.ShowCard</span></span> | <span data-ttu-id="4f8fe-116">AC-Action-Шовкард</span><span class="sxs-lookup"><span data-stu-id="4f8fe-116">ac-action-showCard</span></span> |
| <span data-ttu-id="4f8fe-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="4f8fe-117">Action.Submit</span></span>  | <span data-ttu-id="4f8fe-118">AC-действие — отправка</span><span class="sxs-lookup"><span data-stu-id="4f8fe-118">ac-action-submit</span></span>  |
| <span data-ttu-id="4f8fe-119">Действие</span><span class="sxs-lookup"><span data-stu-id="4f8fe-119">ActionSet</span></span> | <span data-ttu-id="4f8fe-120">AC-действие</span><span class="sxs-lookup"><span data-stu-id="4f8fe-120">ac-actionset</span></span> |
| <span data-ttu-id="4f8fe-121">Column</span><span class="sxs-lookup"><span data-stu-id="4f8fe-121">Column</span></span> | <span data-ttu-id="4f8fe-122">столбец "AC"</span><span class="sxs-lookup"><span data-stu-id="4f8fe-122">ac-column</span></span> |
| <span data-ttu-id="4f8fe-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="4f8fe-123">ColumnSet</span></span> | <span data-ttu-id="4f8fe-124">блок-гистограмма</span><span class="sxs-lookup"><span data-stu-id="4f8fe-124">ac-columnset</span></span> |
| <span data-ttu-id="4f8fe-125">Контейнер</span><span class="sxs-lookup"><span data-stu-id="4f8fe-125">Container</span></span> | <span data-ttu-id="4f8fe-126">контейнер AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-126">ac-container</span></span> |
| <span data-ttu-id="4f8fe-127">Все входные данные</span><span class="sxs-lookup"><span data-stu-id="4f8fe-127">All Inputs</span></span> | <span data-ttu-id="4f8fe-128">входные данные AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-128">ac-input</span></span> |
| <span data-ttu-id="4f8fe-129">Input. Choice</span><span class="sxs-lookup"><span data-stu-id="4f8fe-129">Input.ChoiceSet</span></span> | <span data-ttu-id="4f8fe-130">AC-Мултичоицеинпут</span><span class="sxs-lookup"><span data-stu-id="4f8fe-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="4f8fe-131">Input. Date</span><span class="sxs-lookup"><span data-stu-id="4f8fe-131">Input.Date</span></span> | <span data-ttu-id="4f8fe-132">AC-Датеинпут</span><span class="sxs-lookup"><span data-stu-id="4f8fe-132">ac-dateInput</span></span> |
| <span data-ttu-id="4f8fe-133">Input. Number</span><span class="sxs-lookup"><span data-stu-id="4f8fe-133">Input.Number</span></span> | <span data-ttu-id="4f8fe-134">AC-Нумберинпут</span><span class="sxs-lookup"><span data-stu-id="4f8fe-134">ac-numberInput</span></span> |
| <span data-ttu-id="4f8fe-135">Input. Text</span><span class="sxs-lookup"><span data-stu-id="4f8fe-135">Input.Text</span></span> | <span data-ttu-id="4f8fe-136">AC-textInput</span><span class="sxs-lookup"><span data-stu-id="4f8fe-136">ac-textInput</span></span> |
| <span data-ttu-id="4f8fe-137">Входной. время</span><span class="sxs-lookup"><span data-stu-id="4f8fe-137">Input.Time</span></span> | <span data-ttu-id="4f8fe-138">AC-Тимеинпут</span><span class="sxs-lookup"><span data-stu-id="4f8fe-138">ac-timeInput</span></span> |
| <span data-ttu-id="4f8fe-139">Input. toggle</span><span class="sxs-lookup"><span data-stu-id="4f8fe-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="4f8fe-140">Изображение</span><span class="sxs-lookup"><span data-stu-id="4f8fe-140">Image</span></span>  | <span data-ttu-id="4f8fe-141">образ AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-141">ac-image</span></span> |
| <span data-ttu-id="4f8fe-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="4f8fe-142">ImageSet</span></span>  | <span data-ttu-id="4f8fe-143">блок-образ AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-143">ac-imageset</span></span> |
| <span data-ttu-id="4f8fe-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="4f8fe-144">FactSet</span></span> | <span data-ttu-id="4f8fe-145">блок-фактор AC</span><span class="sxs-lookup"><span data-stu-id="4f8fe-145">ac-factset</span></span> |
| <span data-ttu-id="4f8fe-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="4f8fe-146">TextBlock</span></span>  | <span data-ttu-id="4f8fe-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="4f8fe-147">ac-textblock</span></span> |