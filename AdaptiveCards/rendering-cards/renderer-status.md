---
title: Состояние отрисовщика
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 2b4f9d9ab376839a309a312e9846c45b0fc6cdff
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001801"
---
# <a name="renderer-status"></a><span data-ttu-id="66ec7-102">Состояние отрисовщика</span><span class="sxs-lookup"><span data-stu-id="66ec7-102">Renderer Status</span></span>
<span data-ttu-id="66ec7-103">В таблицах ниже показан текущий статус отрисовщиков в соответствии с их опубликованными общедоступными версиями.</span><span class="sxs-lookup"><span data-stu-id="66ec7-103">The tables below show the current status of each renderer, based on their public published versions.</span></span>

### <a name="parsing"></a><span data-ttu-id="66ec7-104">Анализ</span><span class="sxs-lookup"><span data-stu-id="66ec7-104">Parsing</span></span>

|<span data-ttu-id="66ec7-105">Функции</span><span class="sxs-lookup"><span data-stu-id="66ec7-105">Functionality</span></span> | <span data-ttu-id="66ec7-106">HTML</span><span class="sxs-lookup"><span data-stu-id="66ec7-106">HTML</span></span> | <span data-ttu-id="66ec7-107">.NET</span><span class="sxs-lookup"><span data-stu-id="66ec7-107">.NET</span></span> | <span data-ttu-id="66ec7-108">UWP</span><span class="sxs-lookup"><span data-stu-id="66ec7-108">UWP</span></span> | <span data-ttu-id="66ec7-109">iOS</span><span class="sxs-lookup"><span data-stu-id="66ec7-109">iOS</span></span> | <span data-ttu-id="66ec7-110">Android</span><span class="sxs-lookup"><span data-stu-id="66ec7-110">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="66ec7-111">Возврат ошибок при проверке</span><span class="sxs-lookup"><span data-stu-id="66ec7-111">Return validation failures</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-112">Анализ неизвестных свойств</span><span class="sxs-lookup"><span data-stu-id="66ec7-112">Parse unknown properties</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a><span data-ttu-id="66ec7-113">Отображение карточек</span><span class="sxs-lookup"><span data-stu-id="66ec7-113">Card Rendering</span></span>

|<span data-ttu-id="66ec7-114">Функции</span><span class="sxs-lookup"><span data-stu-id="66ec7-114">Functionality</span></span> | <span data-ttu-id="66ec7-115">HTML</span><span class="sxs-lookup"><span data-stu-id="66ec7-115">HTML</span></span> | <span data-ttu-id="66ec7-116">.NET</span><span class="sxs-lookup"><span data-stu-id="66ec7-116">.NET</span></span> | <span data-ttu-id="66ec7-117">UWP</span><span class="sxs-lookup"><span data-stu-id="66ec7-117">UWP</span></span> | <span data-ttu-id="66ec7-118">iOS</span><span class="sxs-lookup"><span data-stu-id="66ec7-118">iOS</span></span> | <span data-ttu-id="66ec7-119">Android</span><span class="sxs-lookup"><span data-stu-id="66ec7-119">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="66ec7-120">Проверка поддерживаемой версии</span><span class="sxs-lookup"><span data-stu-id="66ec7-120">Check for supported version</span></span> | ✅ | ✅ | ✅ | ✅ | ✅  |
|<span data-ttu-id="66ec7-121">Отображение полной схемы</span><span class="sxs-lookup"><span data-stu-id="66ec7-121">Render full schema</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-122">Отображение панели действий</span><span class="sxs-lookup"><span data-stu-id="66ec7-122">Render actions bar</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-123">Игнорирование неизвестных элементов</span><span class="sxs-lookup"><span data-stu-id="66ec7-123">Ignore unknown Elements</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-124">Поддержка HostConfig</span><span class="sxs-lookup"><span data-stu-id="66ec7-124">Host Config support</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-125">Стиль собственной платформы</span><span class="sxs-lookup"><span data-stu-id="66ec7-125">Native platform styling</span></span> | ✅ | ✅ | ✅ | ✅ | ❌ |

### <a name="element-rendering"></a><span data-ttu-id="66ec7-126">Отображение элементов</span><span class="sxs-lookup"><span data-stu-id="66ec7-126">Element Rendering</span></span>

|<span data-ttu-id="66ec7-127">Функции</span><span class="sxs-lookup"><span data-stu-id="66ec7-127">Functionality</span></span> | <span data-ttu-id="66ec7-128">HTML</span><span class="sxs-lookup"><span data-stu-id="66ec7-128">HTML</span></span> | <span data-ttu-id="66ec7-129">.NET</span><span class="sxs-lookup"><span data-stu-id="66ec7-129">.NET</span></span> | <span data-ttu-id="66ec7-130">UWP</span><span class="sxs-lookup"><span data-stu-id="66ec7-130">UWP</span></span> | <span data-ttu-id="66ec7-131">iOS</span><span class="sxs-lookup"><span data-stu-id="66ec7-131">iOS</span></span> | <span data-ttu-id="66ec7-132">Android</span><span class="sxs-lookup"><span data-stu-id="66ec7-132">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="66ec7-133">Интервалы и разделители</span><span class="sxs-lookup"><span data-stu-id="66ec7-133">Spacing and Separator</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|[<span data-ttu-id="66ec7-134">Форматирование даты и времени в TextBlock</span><span class="sxs-lookup"><span data-stu-id="66ec7-134">TextBlock DATE/TIME formatting</span></span>](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[<span data-ttu-id="66ec7-135">Поддержка Markdown в TextBlock</span><span class="sxs-lookup"><span data-stu-id="66ec7-135">TextBlock Markdown support</span></span>](../authoring-cards/text-features.md#markdown-commonmark-subset) | ✅* | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-136">Проверка входных данных и метки</span><span class="sxs-lookup"><span data-stu-id="66ec7-136">Input Validation and Labels</span></span> | ❌ | ✅ | ✅ | ✅ | ✅ |

<span data-ttu-id="66ec7-137">\* Отрисовщик HTML не включает в себя встроенную поддержку Markdown, чтобы свести к минимуму размер библиотеки и позволить приложениям использовать предпочтительный обработчик Markdown.</span><span class="sxs-lookup"><span data-stu-id="66ec7-137">\* The HTML renderer doesn’t include built-in Markdown support in order to minimize the size of the library and to let consuming applications use their preferred Markdown processor.</span></span> <span data-ttu-id="66ec7-138">Однако отрисовщик HTML автоматически использует анализатор Markdown-It, если он загружен.</span><span class="sxs-lookup"><span data-stu-id="66ec7-138">The HTML renderer will however automatically use Markdown-It if it is loaded.</span></span>

### <a name="extensibility"></a><span data-ttu-id="66ec7-139">Расширяемость</span><span class="sxs-lookup"><span data-stu-id="66ec7-139">Extensibility</span></span>

|<span data-ttu-id="66ec7-140">Функции</span><span class="sxs-lookup"><span data-stu-id="66ec7-140">Functionality</span></span> | <span data-ttu-id="66ec7-141">HTML</span><span class="sxs-lookup"><span data-stu-id="66ec7-141">HTML</span></span> | <span data-ttu-id="66ec7-142">.NET</span><span class="sxs-lookup"><span data-stu-id="66ec7-142">.NET</span></span> | <span data-ttu-id="66ec7-143">UWP</span><span class="sxs-lookup"><span data-stu-id="66ec7-143">UWP</span></span> | <span data-ttu-id="66ec7-144">iOS</span><span class="sxs-lookup"><span data-stu-id="66ec7-144">iOS</span></span> | <span data-ttu-id="66ec7-145">Android</span><span class="sxs-lookup"><span data-stu-id="66ec7-145">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
|<span data-ttu-id="66ec7-146">Переопределение отрисовщика элементов</span><span class="sxs-lookup"><span data-stu-id="66ec7-146">Override Element Renderer</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-147">Добавление нового отрисовщика элементов</span><span class="sxs-lookup"><span data-stu-id="66ec7-147">Add new Element Renderer</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|<span data-ttu-id="66ec7-148">Удаление отрисовщика элементов</span><span class="sxs-lookup"><span data-stu-id="66ec7-148">Remove Element Renderer</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |
|[<span data-ttu-id="66ec7-149">Переопределение, добавление или удаление отрисовщика действий</span><span class="sxs-lookup"><span data-stu-id="66ec7-149">Override/add/remove Action Renderer</span></span>](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="actions"></a><span data-ttu-id="66ec7-150">Действия</span><span class="sxs-lookup"><span data-stu-id="66ec7-150">Actions</span></span>

| <span data-ttu-id="66ec7-151">Функции</span><span class="sxs-lookup"><span data-stu-id="66ec7-151">Functionality</span></span> | <span data-ttu-id="66ec7-152">HTML</span><span class="sxs-lookup"><span data-stu-id="66ec7-152">HTML</span></span> | <span data-ttu-id="66ec7-153">.NET</span><span class="sxs-lookup"><span data-stu-id="66ec7-153">.NET</span></span> | <span data-ttu-id="66ec7-154">UWP</span><span class="sxs-lookup"><span data-stu-id="66ec7-154">UWP</span></span> | <span data-ttu-id="66ec7-155">iOS</span><span class="sxs-lookup"><span data-stu-id="66ec7-155">iOS</span></span> | <span data-ttu-id="66ec7-156">Android</span><span class="sxs-lookup"><span data-stu-id="66ec7-156">Android</span></span> |
|--- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="66ec7-157">Поддержка Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="66ec7-157">Action.OpenUrl support</span></span> | ✅ | ✅ | ✅ | ✅ | ✅  |
| <span data-ttu-id="66ec7-158">Поддержка Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="66ec7-158">Action.ShowCard support</span></span>  | ✅ | ✅ | ✅ | ✅ | ✅ |
| <span data-ttu-id="66ec7-159">Поддержка Action.Submit</span><span class="sxs-lookup"><span data-stu-id="66ec7-159">Action.Submit support</span></span>  | ✅ | ✅ | ✅ | ✅ | ✅  |
| <span data-ttu-id="66ec7-160">Поддержка selectAction</span><span class="sxs-lookup"><span data-stu-id="66ec7-160">selectAction support</span></span> | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a><span data-ttu-id="66ec7-161">События</span><span class="sxs-lookup"><span data-stu-id="66ec7-161">Events</span></span>

|       <span data-ttu-id="66ec7-162">Функции</span><span class="sxs-lookup"><span data-stu-id="66ec7-162">Functionality</span></span>        | <span data-ttu-id="66ec7-163">HTML</span><span class="sxs-lookup"><span data-stu-id="66ec7-163">HTML</span></span> | <span data-ttu-id="66ec7-164">.NET</span><span class="sxs-lookup"><span data-stu-id="66ec7-164">.NET</span></span> | <span data-ttu-id="66ec7-165">UWP</span><span class="sxs-lookup"><span data-stu-id="66ec7-165">UWP</span></span> | <span data-ttu-id="66ec7-166">iOS</span><span class="sxs-lookup"><span data-stu-id="66ec7-166">iOS</span></span> | <span data-ttu-id="66ec7-167">Android</span><span class="sxs-lookup"><span data-stu-id="66ec7-167">Android</span></span> | 
|----------------------------|------|------|-----|-----|---------|
| <span data-ttu-id="66ec7-168">Изменение видимости элемента</span><span class="sxs-lookup"><span data-stu-id="66ec7-168">Element visibility changed</span></span> |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

