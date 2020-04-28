---
title: Реализация отрисовщика
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 607ce40e70e0e54e61a572853a521d2dd70a5c23
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454917"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="e398b-102">Спецификация отрисовщика адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="e398b-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="e398b-103">Следующая спецификация описывает, как реализовать отрисовщик адаптивных карточек на любой платформе пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e398b-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="e398b-104">Содержимое статьи еще не завершено.</span><span class="sxs-lookup"><span data-stu-id="e398b-104">This content is not finished yet.</span></span> <span data-ttu-id="e398b-105">Проверьте его в скором времени.</span><span class="sxs-lookup"><span data-stu-id="e398b-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="e398b-106">Управление версиями пакетов SDK</span><span class="sxs-lookup"><span data-stu-id="e398b-106">SDK Versioning</span></span>

1. <span data-ttu-id="e398b-107">Основной и дополнительный номера версий пакета SDK **должны** соответствовать номеру версии `schema`.</span><span class="sxs-lookup"><span data-stu-id="e398b-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="e398b-108">Для обновлений отрисовщика, которые не включают в себя изменения схемы, **обязательно** следует выполнить установку исправлений или сборку.</span><span class="sxs-lookup"><span data-stu-id="e398b-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="e398b-109">Анализ JSON</span><span class="sxs-lookup"><span data-stu-id="e398b-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="e398b-110">Условия ошибок</span><span class="sxs-lookup"><span data-stu-id="e398b-110">Error conditions</span></span>
1. <span data-ttu-id="e398b-111">Анализатор **должен** проверять допустимость содержимого JSON.</span><span class="sxs-lookup"><span data-stu-id="e398b-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="e398b-112">Анализатор **должен** проверять схему (обязательные свойства и т. д.).</span><span class="sxs-lookup"><span data-stu-id="e398b-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="e398b-113">Сведения об указанных выше ошибках **должны** передаваться ведущему приложению (исключение или аналог).</span><span class="sxs-lookup"><span data-stu-id="e398b-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="e398b-114">Неизвестные типы</span><span class="sxs-lookup"><span data-stu-id="e398b-114">Unknown types</span></span>
1. <span data-ttu-id="e398b-115">Если обнаружены неизвестные "типы", они **должны быть удалены** из полученного результата.</span><span class="sxs-lookup"><span data-stu-id="e398b-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="e398b-116">Любые изменения полезных данных (как показано выше) **должны** быть переданы в виде предупреждений в ведущее приложение.</span><span class="sxs-lookup"><span data-stu-id="e398b-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="e398b-117">Неизвестные свойства</span><span class="sxs-lookup"><span data-stu-id="e398b-117">Unknown properties</span></span>
1. <span data-ttu-id="e398b-118">Анализатор **должен** добавить **дополнительные** свойства элементов.</span><span class="sxs-lookup"><span data-stu-id="e398b-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="e398b-119">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="e398b-119">Additional considerations</span></span>
1. <span data-ttu-id="e398b-120">Свойство `speak` может содержать разметку SSML и **должно** возвращаться в ведущее приложение, как указано.</span><span class="sxs-lookup"><span data-stu-id="e398b-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="e398b-121">Анализ HostConfig</span><span class="sxs-lookup"><span data-stu-id="e398b-121">Parsing Host Config</span></span>
1. <span data-ttu-id="e398b-122">Список действий</span><span class="sxs-lookup"><span data-stu-id="e398b-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="e398b-123">Управление версиями</span><span class="sxs-lookup"><span data-stu-id="e398b-123">Versioning</span></span>

1. <span data-ttu-id="e398b-124">Отрисовщик **должен** реализовывать определенную версию схемы.</span><span class="sxs-lookup"><span data-stu-id="e398b-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="e398b-125">Конструктор `AdaptiveCard`**должен** присвоить свойству `version` значение по умолчанию, основанное на текущей версии схемы.</span><span class="sxs-lookup"><span data-stu-id="e398b-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="e398b-126">Если отрисовщик обнаруживает свойство `version` в `AdaptiveCard`, значение которого больше номера текущей поддерживаемой версии, то он **должен** возвращать `fallbackText`.</span><span class="sxs-lookup"><span data-stu-id="e398b-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="e398b-127">Отрисовка</span><span class="sxs-lookup"><span data-stu-id="e398b-127">Rendering</span></span>

<span data-ttu-id="e398b-128">Объект `AdaptiveCard` состоит из элементов `body` и `actions`.</span><span class="sxs-lookup"><span data-stu-id="e398b-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="e398b-129">Элемент `body` представляет собой коллекцию элементов `CardElement`, которые отрисовщик будет перечислять и отображать по порядку.</span><span class="sxs-lookup"><span data-stu-id="e398b-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="e398b-130">Каждый элемент **должен** быть растянут до ширины его родительского элемента (вспомните о `display: block` в HTML).</span><span class="sxs-lookup"><span data-stu-id="e398b-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="e398b-131">Отрисовщик **должен** игнорировать неизвестные типы элементов и продолжить отрисовку оставшейся части полезных данных.</span><span class="sxs-lookup"><span data-stu-id="e398b-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="e398b-132">Интервалы и разделители</span><span class="sxs-lookup"><span data-stu-id="e398b-132">Spacing and Separators</span></span>

1. <span data-ttu-id="e398b-133">Свойство `spacing` каждого элемента влияет на расстояние между **текущим** элементом и элементом, находящимся **перед** ним.</span><span class="sxs-lookup"><span data-stu-id="e398b-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="e398b-134">Интервал должен применяться **только** в том случае, если перед элементом есть другой элемент.</span><span class="sxs-lookup"><span data-stu-id="e398b-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="e398b-135">(Например, он не должен применяться к первому элементу в массиве.)</span><span class="sxs-lookup"><span data-stu-id="e398b-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="e398b-136">Отрисовщик **должен** определить, сколько нужно использовать пространства, с помощью интервала в `hostConfig`, указанного для значения перечисления, примененного к текущему элементу.</span><span class="sxs-lookup"><span data-stu-id="e398b-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="e398b-137">Если для элемента задан параметр `separator` со значением `true`, то между текущим и предыдущим элементами **должна** быть нарисована видимая линия.</span><span class="sxs-lookup"><span data-stu-id="e398b-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="e398b-138">Разделительная линия **должна** быть нарисована с помощью `container.style.default.foregroundColor`.</span><span class="sxs-lookup"><span data-stu-id="e398b-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="e398b-139">Разделитель должен быть нарисован **только** в том случае, если элемент **не является** первым в массиве.</span><span class="sxs-lookup"><span data-stu-id="e398b-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="e398b-140">Столбцы</span><span class="sxs-lookup"><span data-stu-id="e398b-140">Columns</span></span>

1. <span data-ttu-id="e398b-141">Параметры `Column` и `width` **ДОЛЖНЫ** интерпретироваться с учетом ключевых слов auto, stretch или с помощью взвешенного соотношения.</span><span class="sxs-lookup"><span data-stu-id="e398b-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="e398b-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="e398b-142">TextBlock</span></span>

1. <span data-ttu-id="e398b-143">Элемент TextBlock **должен** занимать одну строку, если только свойство `wrap` не имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="e398b-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="e398b-144">Текстовый блок **должен** обрезать любой лишний текст с помощью многоточия (…).</span><span class="sxs-lookup"><span data-stu-id="e398b-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="e398b-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="e398b-145">Markdown</span></span>

1. <span data-ttu-id="e398b-146">Адаптивные карточки поддерживают часть элементов Markdown, которые **должны** поддерживаться в объектах `TextBlock`.</span><span class="sxs-lookup"><span data-stu-id="e398b-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="e398b-147">Ознакомьтесь с [полными требованиями к Markdown](../authoring-cards/text-features.md).</span><span class="sxs-lookup"><span data-stu-id="e398b-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="e398b-148">Функции форматирования</span><span class="sxs-lookup"><span data-stu-id="e398b-148">Formatting functions</span></span>

1. <span data-ttu-id="e398b-149">`TextBlock` допускает использование [функций форматирования даты и времени](../authoring-cards/text-features.md), которые **должны** поддерживаться каждым отрисовщиком.</span><span class="sxs-lookup"><span data-stu-id="e398b-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="e398b-150">**Все сообщения об ошибке должны** отображать необработанную строку в карточке.</span><span class="sxs-lookup"><span data-stu-id="e398b-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="e398b-151">Понятное сообщение о попытке отображать не нужно.</span><span class="sxs-lookup"><span data-stu-id="e398b-151">No friendly message attempted.</span></span> <span data-ttu-id="e398b-152">(Это нужно для того, чтобы разработчик сразу узнал о проблеме.)</span><span class="sxs-lookup"><span data-stu-id="e398b-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="e398b-153">TODO: добавьте регулярное выражение.</span><span class="sxs-lookup"><span data-stu-id="e398b-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="e398b-154">образы,</span><span class="sxs-lookup"><span data-stu-id="e398b-154">Images</span></span>

1. <span data-ttu-id="e398b-155">Отрисовщик **должен** давать ведущим приложениям возможность определить, когда все изображения HTTP скачаны и карточка полностью отображена.</span><span class="sxs-lookup"><span data-stu-id="e398b-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="e398b-156">Отрисовщик **должен** проверять параметр `maxImageSize` HostConfig при скачивании изображений HTTP.</span><span class="sxs-lookup"><span data-stu-id="e398b-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="e398b-157">Отрисовщик **должен** поддерживать `.png` и `.jpeg`.</span><span class="sxs-lookup"><span data-stu-id="e398b-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="e398b-158">Отрисовщик **должен** поддерживать изображения с расширением `.gif`.</span><span class="sxs-lookup"><span data-stu-id="e398b-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="e398b-159">Конфигурация узла</span><span class="sxs-lookup"><span data-stu-id="e398b-159">Host Config</span></span>

* <span data-ttu-id="e398b-160">TODO: Какими должны быть значения по умолчанию?</span><span class="sxs-lookup"><span data-stu-id="e398b-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="e398b-161">Должны ли использоваться совместно?</span><span class="sxs-lookup"><span data-stu-id="e398b-161">Should they all share it?</span></span> <span data-ttu-id="e398b-162">Следует ли внедрить в двоичные файлы общий файл hostConfig.JSON?</span><span class="sxs-lookup"><span data-stu-id="e398b-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="e398b-163">TODO: Требуется ли управление версиями HostConfig и для анализа?</span><span class="sxs-lookup"><span data-stu-id="e398b-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="e398b-164">[`HostConfig`](host-config.md) — это общий объект конфигурации, указывающий, как отрисовщик адаптивных карточек создает пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e398b-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="e398b-165">Это позволяет отрисовщикам на разных платформах и устройствах использовать свойства, которые независимы от платформы.</span><span class="sxs-lookup"><span data-stu-id="e398b-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="e398b-166">Кроме того, это позволяет создавать наборы инструментов, которые дают представление о внешнем виде и функциях карточки в конкретной среде.</span><span class="sxs-lookup"><span data-stu-id="e398b-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="e398b-167">Отрисовщики **должны** предоставлять параметр **HostConfig** ведущим приложениям.</span><span class="sxs-lookup"><span data-stu-id="e398b-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="e398b-168">Все элементы **должны** быть стилизованы согласно соответствующим параметрам HostConfig.</span><span class="sxs-lookup"><span data-stu-id="e398b-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="e398b-169">Стиль собственной платформы</span><span class="sxs-lookup"><span data-stu-id="e398b-169">Native platform styling</span></span>

1. <span data-ttu-id="e398b-170">Каждый тип элемента **должен** привязывать стиль собственной платформы к созданному элементу пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e398b-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="e398b-171">Например, в HTML мы добавили класс CSS к типам элементов, а в XAML мы присваиваем конкретный стиль.</span><span class="sxs-lookup"><span data-stu-id="e398b-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="e398b-172">Расширяемость</span><span class="sxs-lookup"><span data-stu-id="e398b-172">Extensibility</span></span> 

1. <span data-ttu-id="e398b-173">Отрисовщик **должен** позволять ведущим приложениям переопределять отрисовщики элементов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e398b-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="e398b-174">Например, заменить отрисовку `TextBlock` собственной логикой.</span><span class="sxs-lookup"><span data-stu-id="e398b-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="e398b-175">Отрисовщик **должен** позволять ведущим приложениям регистрировать пользовательские типы элементов.</span><span class="sxs-lookup"><span data-stu-id="e398b-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="e398b-176">Например, добавить поддержку пользовательского элемента `Rating`.</span><span class="sxs-lookup"><span data-stu-id="e398b-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="e398b-177">Отрисовщик **должен** позволять ведущим приложениям удалять поддержку элемента по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e398b-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="e398b-178">Например, удалить элемент `Action.Submit`, если его поддержка не нужна.</span><span class="sxs-lookup"><span data-stu-id="e398b-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="e398b-179">Действия</span><span class="sxs-lookup"><span data-stu-id="e398b-179">Actions</span></span>

1. <span data-ttu-id="e398b-180">Если параметр `supportsInteractivity` HostConfig имеет значение `false`, то отрисовщик **не должен** отображать какие-либо действия.</span><span class="sxs-lookup"><span data-stu-id="e398b-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="e398b-181">Свойство `actions`**должно** быть отображено в виде кнопок на панели действий, как правило, в нижней части карточки.</span><span class="sxs-lookup"><span data-stu-id="e398b-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="e398b-182">При нажатии кнопка **должна** позволить ведущему приложению обработать событие.</span><span class="sxs-lookup"><span data-stu-id="e398b-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="e398b-183">Событие **должно** передавать все связанные свойства с действием.</span><span class="sxs-lookup"><span data-stu-id="e398b-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="e398b-184">Событие **должно** передавать объект `AdaptiveCard`, который был выполнен.</span><span class="sxs-lookup"><span data-stu-id="e398b-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="e398b-185">Действие</span><span class="sxs-lookup"><span data-stu-id="e398b-185">Action</span></span> | <span data-ttu-id="e398b-186">Поведение</span><span class="sxs-lookup"><span data-stu-id="e398b-186">Behavior</span></span>
--- | ---
<span data-ttu-id="e398b-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="e398b-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="e398b-188">Открытие внешнего URL-адреса для просмотра.</span><span class="sxs-lookup"><span data-stu-id="e398b-188">Open an external URL for viewing</span></span>
<span data-ttu-id="e398b-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="e398b-189">**Action.ShowCard**</span></span> | <span data-ttu-id="e398b-190">Запрашивает вложенную карточку для отображения пользователю.</span><span class="sxs-lookup"><span data-stu-id="e398b-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="e398b-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="e398b-191">**Action.Submit**</span></span> | <span data-ttu-id="e398b-192">Запрашивает сбор данных от всех элементов в один объект и его отправку способом, определяемым ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="e398b-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="e398b-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="e398b-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="e398b-194">Действие `Action.OpenUrl` **ДОЛЖНО** открывать URL-адрес с помощью механизма собственной платформы.</span><span class="sxs-lookup"><span data-stu-id="e398b-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="e398b-195">Если это невозможно, оно **должно** породить событие в ведущем приложении для обработки открытия этого URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="e398b-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="e398b-196">Это событие **должно** позволить ведущему приложению переопределить поведение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e398b-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="e398b-197">Например, разрешить ему открыть этот URL-адрес в собственном приложении.</span><span class="sxs-lookup"><span data-stu-id="e398b-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="e398b-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="e398b-198">Action.ShowCard</span></span>

1. <span data-ttu-id="e398b-199">Поддержка `Action.ShowCard` **ДОЛЖНА** обеспечиваться каким-либо из способов с учетом параметра hostConfig.</span><span class="sxs-lookup"><span data-stu-id="e398b-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="e398b-200">Существуют два режима: встроенные карточки и всплывающие окна.</span><span class="sxs-lookup"><span data-stu-id="e398b-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="e398b-201">Встроенные карточки **должны** автоматически переключать видимость карточки.</span><span class="sxs-lookup"><span data-stu-id="e398b-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="e398b-202">В режиме всплывающего окна событие **должно** быть передано в ведущее приложение, чтобы оно отобразило карточку каким-либо способом.</span><span class="sxs-lookup"><span data-stu-id="e398b-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="e398b-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="e398b-203">Action.Submit</span></span>

<span data-ttu-id="e398b-204">Действие отправки выполняется, как и отправка данных в форме HTML, за исключением того, что если HTML обычно запускает HTTP-запрос POST, то адаптивные карточки в определении смысла отправки полагаются на само ведущее приложение.</span><span class="sxs-lookup"><span data-stu-id="e398b-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="e398b-205">В этом случае **должно** вызываться событие, когда пользователь касается вызванного действия.</span><span class="sxs-lookup"><span data-stu-id="e398b-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="e398b-206">Свойство `data`**должно** быть включено в полезные данные обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="e398b-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="e398b-207">Для `Action.Submit` отрисовщик **должен** собрать все входные данные в карточке и получить их значения.</span><span class="sxs-lookup"><span data-stu-id="e398b-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="e398b-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="e398b-208">selectAction</span></span>

1. <span data-ttu-id="e398b-209">Если параметр `supportedInteractivity` hostConfig имеет значение `false`, действие `selectAction` **НЕ ДОЛЖНО** отображаться как объект, доступный для касания.</span><span class="sxs-lookup"><span data-stu-id="e398b-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="e398b-210">Элементы `Image`, `ColumnSet` и `Column` предлагают свойство `selectAction`, которое **должно** выполняться, когда пользователь вызывает его, например, коснувшись элемента.</span><span class="sxs-lookup"><span data-stu-id="e398b-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="e398b-211">Входные данные</span><span class="sxs-lookup"><span data-stu-id="e398b-211">Inputs</span></span>

1. <span data-ttu-id="e398b-212">Если параметр `supportsInteractivity` HostConfig имеет значение `false`, то отрисовщик **не должен** отображать какие-либо управляющие элементы ввода.</span><span class="sxs-lookup"><span data-stu-id="e398b-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="e398b-213">Управляющие элементы ввода **должны** отображаться с максимально допустимой точностью.</span><span class="sxs-lookup"><span data-stu-id="e398b-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="e398b-214">Например, `Input.Date` в идеале представит пользователю управляющий элемент выбора даты, но если это невозможно в стеке пользовательского интерфейса, то отрисовщик **должен** вернуться к отображению стандартного текстового поля.</span><span class="sxs-lookup"><span data-stu-id="e398b-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="e398b-215">Отрисовщик **должен** отображать `placeholderText`, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="e398b-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="e398b-216">В отрисовщике **не обязательно** реализовывать проверку входных данных.</span><span class="sxs-lookup"><span data-stu-id="e398b-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="e398b-217">Пользователи адаптивных карточек должны запланировать проверку всех полученных данных на своей стороне.</span><span class="sxs-lookup"><span data-stu-id="e398b-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="e398b-218">Привязка входного значения **должна** быть правильно экранирована.</span><span class="sxs-lookup"><span data-stu-id="e398b-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="e398b-219">Объект **должен** быть возвращен в ведущее приложение следующим образом.</span><span class="sxs-lookup"><span data-stu-id="e398b-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="e398b-220">Мы не обещаем проверку входных данных в адаптивных карточках, поэтому именно принимающая сторона должна соответствующим образом проанализировать ответ.</span><span class="sxs-lookup"><span data-stu-id="e398b-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="e398b-221">Например, Input.Number может вернуть "hello", и они должны быть готовы к этому.</span><span class="sxs-lookup"><span data-stu-id="e398b-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="e398b-222">События</span><span class="sxs-lookup"><span data-stu-id="e398b-222">Events</span></span>

1. <span data-ttu-id="e398b-223">Отрисовщик **должен** запускать событие при изменении видимости элемента, позволяя ведущему приложению прокрутить карточку до нужного места.</span><span class="sxs-lookup"><span data-stu-id="e398b-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
