---
title: Состояние отрисовщика
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 1042fd862990a79c77110ebdf5d804eadcc606ea
ms.sourcegitcommit: 19c08b1370305fb2965de0140c5e632356e78513
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879148"
---
# <a name="renderer-status"></a><span data-ttu-id="5b215-102">Состояние отрисовщика</span><span class="sxs-lookup"><span data-stu-id="5b215-102">Renderer Status</span></span>
<span data-ttu-id="5b215-103">В таблицах ниже показан текущий статус отрисовщиков в соответствии с их опубликованными общедоступными версиями.</span><span class="sxs-lookup"><span data-stu-id="5b215-103">The tables below show the current status of each renderer, based on their public published versions.</span></span>

### <a name="parsing"></a><span data-ttu-id="5b215-104">Анализ</span><span class="sxs-lookup"><span data-stu-id="5b215-104">Parsing</span></span>

|<span data-ttu-id="5b215-105">Функции</span><span class="sxs-lookup"><span data-stu-id="5b215-105">Functionality</span></span> | <span data-ttu-id="5b215-106">HTML</span><span class="sxs-lookup"><span data-stu-id="5b215-106">HTML</span></span> | <span data-ttu-id="5b215-107">.NET</span><span class="sxs-lookup"><span data-stu-id="5b215-107">.NET</span></span> | <span data-ttu-id="5b215-108">UWP</span><span class="sxs-lookup"><span data-stu-id="5b215-108">UWP</span></span> | <span data-ttu-id="5b215-109">iOS</span><span class="sxs-lookup"><span data-stu-id="5b215-109">iOS</span></span> | <span data-ttu-id="5b215-110">Android</span><span class="sxs-lookup"><span data-stu-id="5b215-110">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="5b215-111">Возврат ошибок при проверке</span><span class="sxs-lookup"><span data-stu-id="5b215-111">Return validation failures</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-112">Анализ неизвестных свойств</span><span class="sxs-lookup"><span data-stu-id="5b215-112">Parse unknown properties</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a><span data-ttu-id="5b215-113">Отображение карточек</span><span class="sxs-lookup"><span data-stu-id="5b215-113">Card Rendering</span></span>

|<span data-ttu-id="5b215-114">Функции</span><span class="sxs-lookup"><span data-stu-id="5b215-114">Functionality</span></span> | <span data-ttu-id="5b215-115">HTML</span><span class="sxs-lookup"><span data-stu-id="5b215-115">HTML</span></span> | <span data-ttu-id="5b215-116">.NET</span><span class="sxs-lookup"><span data-stu-id="5b215-116">.NET</span></span> | <span data-ttu-id="5b215-117">UWP</span><span class="sxs-lookup"><span data-stu-id="5b215-117">UWP</span></span> | <span data-ttu-id="5b215-118">iOS</span><span class="sxs-lookup"><span data-stu-id="5b215-118">iOS</span></span> | <span data-ttu-id="5b215-119">Android</span><span class="sxs-lookup"><span data-stu-id="5b215-119">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="5b215-120">Проверка поддерживаемой версии</span><span class="sxs-lookup"><span data-stu-id="5b215-120">Check for supported version</span></span> | ✅ | ✅ | ✅ | ✅ | ✅  |
|<span data-ttu-id="5b215-121">Отображение полной схемы</span><span class="sxs-lookup"><span data-stu-id="5b215-121">Render full schema</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-122">Отображение панели действий</span><span class="sxs-lookup"><span data-stu-id="5b215-122">Render actions bar</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-123">Игнорирование неизвестных элементов</span><span class="sxs-lookup"><span data-stu-id="5b215-123">Ignore unknown Elements</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-124">Поддержка HostConfig</span><span class="sxs-lookup"><span data-stu-id="5b215-124">Host Config support</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-125">Стиль собственной платформы</span><span class="sxs-lookup"><span data-stu-id="5b215-125">Native platform styling</span></span> | ✅ | ✅ | ✅ | ✅ | ❌ |

### <a name="element-rendering"></a><span data-ttu-id="5b215-126">Отображение элементов</span><span class="sxs-lookup"><span data-stu-id="5b215-126">Element Rendering</span></span>

|<span data-ttu-id="5b215-127">Функции</span><span class="sxs-lookup"><span data-stu-id="5b215-127">Functionality</span></span> | <span data-ttu-id="5b215-128">HTML</span><span class="sxs-lookup"><span data-stu-id="5b215-128">HTML</span></span> | <span data-ttu-id="5b215-129">.NET</span><span class="sxs-lookup"><span data-stu-id="5b215-129">.NET</span></span> | <span data-ttu-id="5b215-130">UWP</span><span class="sxs-lookup"><span data-stu-id="5b215-130">UWP</span></span> | <span data-ttu-id="5b215-131">iOS</span><span class="sxs-lookup"><span data-stu-id="5b215-131">iOS</span></span> | <span data-ttu-id="5b215-132">Android</span><span class="sxs-lookup"><span data-stu-id="5b215-132">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="5b215-133">Интервалы и разделители</span><span class="sxs-lookup"><span data-stu-id="5b215-133">Spacing and Separator</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|[<span data-ttu-id="5b215-134">Форматирование даты и времени в TextBlock</span><span class="sxs-lookup"><span data-stu-id="5b215-134">TextBlock DATE/TIME formatting</span></span>](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[<span data-ttu-id="5b215-135">Поддержка Markdown в TextBlock</span><span class="sxs-lookup"><span data-stu-id="5b215-135">TextBlock Markdown support</span></span>](../authoring-cards/text-features.md#markdown-commonmark-subset) | ✅* | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-136">Проверка входных данных и метки</span><span class="sxs-lookup"><span data-stu-id="5b215-136">Input Validation and Labels</span></span> | ❌ | ✅ | ✅ | ✅ | ✅ |


<span data-ttu-id="5b215-137">\* Отрисовщик HTML не включает в себя встроенную поддержку Markdown, чтобы свести к минимуму размер библиотеки и позволить приложениям использовать предпочтительный обработчик Markdown.</span><span class="sxs-lookup"><span data-stu-id="5b215-137">\* The HTML renderer doesn’t include built-in Markdown support in order to minimize the size of the library and to let consuming applications use their preferred Markdown processor.</span></span> <span data-ttu-id="5b215-138">Однако отрисовщик HTML автоматически использует анализатор Markdown-It, если он загружен.</span><span class="sxs-lookup"><span data-stu-id="5b215-138">The HTML renderer will however automatically use Markdown-It if it is loaded.</span></span>

### <a name="extensibility"></a><span data-ttu-id="5b215-139">Расширяемость</span><span class="sxs-lookup"><span data-stu-id="5b215-139">Extensibility</span></span>

|<span data-ttu-id="5b215-140">Функции</span><span class="sxs-lookup"><span data-stu-id="5b215-140">Functionality</span></span> | <span data-ttu-id="5b215-141">HTML</span><span class="sxs-lookup"><span data-stu-id="5b215-141">HTML</span></span> | <span data-ttu-id="5b215-142">.NET</span><span class="sxs-lookup"><span data-stu-id="5b215-142">.NET</span></span> | <span data-ttu-id="5b215-143">UWP</span><span class="sxs-lookup"><span data-stu-id="5b215-143">UWP</span></span> | <span data-ttu-id="5b215-144">iOS</span><span class="sxs-lookup"><span data-stu-id="5b215-144">iOS</span></span> | <span data-ttu-id="5b215-145">Android</span><span class="sxs-lookup"><span data-stu-id="5b215-145">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="5b215-146">Переопределение отрисовщика элементов</span><span class="sxs-lookup"><span data-stu-id="5b215-146">Override Element Renderer</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-147">Добавление нового отрисовщика элементов</span><span class="sxs-lookup"><span data-stu-id="5b215-147">Add new Element Renderer</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="5b215-148">Удаление отрисовщика элементов</span><span class="sxs-lookup"><span data-stu-id="5b215-148">Remove Element Renderer</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|[<span data-ttu-id="5b215-149">Переопределение, добавление или удаление отрисовщика действий</span><span class="sxs-lookup"><span data-stu-id="5b215-149">Override/add/remove Action Renderer</span></span>](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a><span data-ttu-id="5b215-150">Действия</span><span class="sxs-lookup"><span data-stu-id="5b215-150">Actions</span></span>

| <span data-ttu-id="5b215-151">Функции</span><span class="sxs-lookup"><span data-stu-id="5b215-151">Functionality</span></span> | <span data-ttu-id="5b215-152">HTML</span><span class="sxs-lookup"><span data-stu-id="5b215-152">HTML</span></span> | <span data-ttu-id="5b215-153">.NET</span><span class="sxs-lookup"><span data-stu-id="5b215-153">.NET</span></span> | <span data-ttu-id="5b215-154">UWP</span><span class="sxs-lookup"><span data-stu-id="5b215-154">UWP</span></span> | <span data-ttu-id="5b215-155">iOS</span><span class="sxs-lookup"><span data-stu-id="5b215-155">iOS</span></span> | <span data-ttu-id="5b215-156">Android</span><span class="sxs-lookup"><span data-stu-id="5b215-156">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="5b215-157">Поддержка Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="5b215-157">Action.OpenUrl support</span></span> | ✅ | ✅ | ✅ | ✅ | ✅  |
| <span data-ttu-id="5b215-158">Поддержка Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="5b215-158">Action.ShowCard support</span></span>  | ✅ | ✅ | ✅ | ✅ | ✅ |
| <span data-ttu-id="5b215-159">Поддержка Action.Submit</span><span class="sxs-lookup"><span data-stu-id="5b215-159">Action.Submit support</span></span>  | ✅ | ✅ | ✅ | ✅ | ✅  |
| <span data-ttu-id="5b215-160">Поддержка selectAction</span><span class="sxs-lookup"><span data-stu-id="5b215-160">selectAction support</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a><span data-ttu-id="5b215-161">События</span><span class="sxs-lookup"><span data-stu-id="5b215-161">Events</span></span>

|       <span data-ttu-id="5b215-162">Функции</span><span class="sxs-lookup"><span data-stu-id="5b215-162">Functionality</span></span>        | <span data-ttu-id="5b215-163">HTML</span><span class="sxs-lookup"><span data-stu-id="5b215-163">HTML</span></span> | <span data-ttu-id="5b215-164">.NET</span><span class="sxs-lookup"><span data-stu-id="5b215-164">.NET</span></span> | <span data-ttu-id="5b215-165">UWP</span><span class="sxs-lookup"><span data-stu-id="5b215-165">UWP</span></span> | <span data-ttu-id="5b215-166">iOS</span><span class="sxs-lookup"><span data-stu-id="5b215-166">iOS</span></span> | <span data-ttu-id="5b215-167">Android</span><span class="sxs-lookup"><span data-stu-id="5b215-167">Android</span></span> | 
|----------------------------|------|------|-----|-----|---------|
| <span data-ttu-id="5b215-168">Изменение видимости элемента</span><span class="sxs-lookup"><span data-stu-id="5b215-168">Element visibility changed</span></span> |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

