---
title: Собственный стиль — пакет SDK для .NET HTML
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
# <a name="native-styling---net-html"></a><span data-ttu-id="d8771-102">Собственный стиль — HTML-код .NET</span><span class="sxs-lookup"><span data-stu-id="d8771-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="d8771-103">Несмотря на то, что конфигурация узла будет наиболее актуальна на каждой платформе, вполне вероятно, что на каждой платформе придется выполнять некоторые собственные стили.</span><span class="sxs-lookup"><span data-stu-id="d8771-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="d8771-104">HTML упрощает эту задачу, добавляя классы CSS к каждому элементу.</span><span class="sxs-lookup"><span data-stu-id="d8771-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="d8771-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="d8771-105">Element</span></span> | <span data-ttu-id="d8771-106">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="d8771-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="d8771-107">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="d8771-107">AdaptiveCard</span></span> | <span data-ttu-id="d8771-108">AC-адаптивекард</span><span class="sxs-lookup"><span data-stu-id="d8771-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="d8771-109">Все действия</span><span class="sxs-lookup"><span data-stu-id="d8771-109">All Actions</span></span> | <span data-ttu-id="d8771-110">Кнопка AC</span><span class="sxs-lookup"><span data-stu-id="d8771-110">ac-pushButton</span></span> | 
| <span data-ttu-id="d8771-111">Выбор действий</span><span class="sxs-lookup"><span data-stu-id="d8771-111">Select Actions</span></span> | <span data-ttu-id="d8771-112">Выбираемый AC</span><span class="sxs-lookup"><span data-stu-id="d8771-112">ac-selectable</span></span> |
| <span data-ttu-id="d8771-113">Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="d8771-113">Action.OpenUrl</span></span>  | <span data-ttu-id="d8771-114">AC-Action-openUrl</span><span class="sxs-lookup"><span data-stu-id="d8771-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="d8771-115">Action. Шовкард</span><span class="sxs-lookup"><span data-stu-id="d8771-115">Action.ShowCard</span></span> | <span data-ttu-id="d8771-116">AC-Action-Шовкард</span><span class="sxs-lookup"><span data-stu-id="d8771-116">ac-action-showCard</span></span> |
| <span data-ttu-id="d8771-117">Действие. Отправка</span><span class="sxs-lookup"><span data-stu-id="d8771-117">Action.Submit</span></span>  | <span data-ttu-id="d8771-118">AC-действие — отправка</span><span class="sxs-lookup"><span data-stu-id="d8771-118">ac-action-submit</span></span>  |
| <span data-ttu-id="d8771-119">Действие</span><span class="sxs-lookup"><span data-stu-id="d8771-119">ActionSet</span></span> | <span data-ttu-id="d8771-120">AC-действие</span><span class="sxs-lookup"><span data-stu-id="d8771-120">ac-actionset</span></span> |
| <span data-ttu-id="d8771-121">Column</span><span class="sxs-lookup"><span data-stu-id="d8771-121">Column</span></span> | <span data-ttu-id="d8771-122">столбец "AC"</span><span class="sxs-lookup"><span data-stu-id="d8771-122">ac-column</span></span> |
| <span data-ttu-id="d8771-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="d8771-123">ColumnSet</span></span> | <span data-ttu-id="d8771-124">блок-гистограмма</span><span class="sxs-lookup"><span data-stu-id="d8771-124">ac-columnset</span></span> |
| <span data-ttu-id="d8771-125">Контейнер</span><span class="sxs-lookup"><span data-stu-id="d8771-125">Container</span></span> | <span data-ttu-id="d8771-126">контейнер AC</span><span class="sxs-lookup"><span data-stu-id="d8771-126">ac-container</span></span> |
| <span data-ttu-id="d8771-127">Все входные данные</span><span class="sxs-lookup"><span data-stu-id="d8771-127">All Inputs</span></span> | <span data-ttu-id="d8771-128">входные данные AC</span><span class="sxs-lookup"><span data-stu-id="d8771-128">ac-input</span></span> |
| <span data-ttu-id="d8771-129">Input. Choice</span><span class="sxs-lookup"><span data-stu-id="d8771-129">Input.ChoiceSet</span></span> | <span data-ttu-id="d8771-130">AC-Мултичоицеинпут</span><span class="sxs-lookup"><span data-stu-id="d8771-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="d8771-131">Input. Date</span><span class="sxs-lookup"><span data-stu-id="d8771-131">Input.Date</span></span> | <span data-ttu-id="d8771-132">AC-Датеинпут</span><span class="sxs-lookup"><span data-stu-id="d8771-132">ac-dateInput</span></span> |
| <span data-ttu-id="d8771-133">Input. Number</span><span class="sxs-lookup"><span data-stu-id="d8771-133">Input.Number</span></span> | <span data-ttu-id="d8771-134">AC-Нумберинпут</span><span class="sxs-lookup"><span data-stu-id="d8771-134">ac-numberInput</span></span> |
| <span data-ttu-id="d8771-135">Input. Text</span><span class="sxs-lookup"><span data-stu-id="d8771-135">Input.Text</span></span> | <span data-ttu-id="d8771-136">AC-textInput</span><span class="sxs-lookup"><span data-stu-id="d8771-136">ac-textInput</span></span> |
| <span data-ttu-id="d8771-137">Входной. время</span><span class="sxs-lookup"><span data-stu-id="d8771-137">Input.Time</span></span> | <span data-ttu-id="d8771-138">AC-Тимеинпут</span><span class="sxs-lookup"><span data-stu-id="d8771-138">ac-timeInput</span></span> |
| <span data-ttu-id="d8771-139">Input. toggle</span><span class="sxs-lookup"><span data-stu-id="d8771-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="d8771-140">Image</span><span class="sxs-lookup"><span data-stu-id="d8771-140">Image</span></span>  | <span data-ttu-id="d8771-141">образ AC</span><span class="sxs-lookup"><span data-stu-id="d8771-141">ac-image</span></span> |
| <span data-ttu-id="d8771-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="d8771-142">ImageSet</span></span>  | <span data-ttu-id="d8771-143">блок-образ AC</span><span class="sxs-lookup"><span data-stu-id="d8771-143">ac-imageset</span></span> |
| <span data-ttu-id="d8771-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="d8771-144">FactSet</span></span> | <span data-ttu-id="d8771-145">блок-фактор AC</span><span class="sxs-lookup"><span data-stu-id="d8771-145">ac-factset</span></span> |
| <span data-ttu-id="d8771-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="d8771-146">TextBlock</span></span>  | <span data-ttu-id="d8771-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="d8771-147">ac-textblock</span></span> |