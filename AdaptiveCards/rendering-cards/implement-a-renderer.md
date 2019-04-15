---
title: Реализация модуля подготовки отчетов
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: 3c79d768d5c979626b66614a1856ad6c2e390805
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552556"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="f83e5-102">Инструмент Adaptive Cards спецификации модуля подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="f83e5-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="f83e5-103">В следующей спецификации описываются как реализовать инструмент Adaptive Cards модуля подготовки отчетов на любой платформе пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f83e5-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="f83e5-104">Это содержимое еще не завершена.</span><span class="sxs-lookup"><span data-stu-id="f83e5-104">This content is not finished yet.</span></span> <span data-ttu-id="f83e5-105">Повторите попытку позже.</span><span class="sxs-lookup"><span data-stu-id="f83e5-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="f83e5-106">Управление версиями пакетов SDK</span><span class="sxs-lookup"><span data-stu-id="f83e5-106">SDK Versioning</span></span>

1. <span data-ttu-id="f83e5-107">Пакет SDK для основной и вспомогательной версии **следует** соответствует `schema` версии.</span><span class="sxs-lookup"><span data-stu-id="f83e5-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="f83e5-108">Patch/build **следует** использоваться для обновления модуля подготовки отчетов, у которых нет изменений схемы.</span><span class="sxs-lookup"><span data-stu-id="f83e5-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="f83e5-109">Синтаксический анализ JSON</span><span class="sxs-lookup"><span data-stu-id="f83e5-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="f83e5-110">Условия ошибок</span><span class="sxs-lookup"><span data-stu-id="f83e5-110">Error conditions</span></span>
1. <span data-ttu-id="f83e5-111">Средство синтаксического анализа **необходимо** проверьте, что это допустимое содержимое JSON</span><span class="sxs-lookup"><span data-stu-id="f83e5-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="f83e5-112">Средство синтаксического анализа **необходимо** проверку на соответствие схеме (обязательные свойства, и т.д.)</span><span class="sxs-lookup"><span data-stu-id="f83e5-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="f83e5-113">Ошибок, упомянутых выше **необходимо** будут передаваться ведущее приложение (исключение или эквивалент)</span><span class="sxs-lookup"><span data-stu-id="f83e5-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="f83e5-114">Неизвестные типы</span><span class="sxs-lookup"><span data-stu-id="f83e5-114">Unknown types</span></span>
1. <span data-ttu-id="f83e5-115">При обнаружении неизвестного «типы» они **должны УДАЛЯТЬСЯ** из результата</span><span class="sxs-lookup"><span data-stu-id="f83e5-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="f83e5-116">Любых изменений в полезных данных (как и выше) **следует** поступать предупреждения для узла приложения</span><span class="sxs-lookup"><span data-stu-id="f83e5-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="f83e5-117">Неизвестные свойства</span><span class="sxs-lookup"><span data-stu-id="f83e5-117">Unknown properties</span></span>
1. <span data-ttu-id="f83e5-118">Средство синтаксического анализа **необходимо** включают **дополнительных** свойства элементов</span><span class="sxs-lookup"><span data-stu-id="f83e5-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="f83e5-119">Дополнительные рекомендации</span><span class="sxs-lookup"><span data-stu-id="f83e5-119">Additional considerations</span></span>
1. <span data-ttu-id="f83e5-120">`speak` Свойство может содержать разметку SSML и **необходимо** возвращаться к приложению узла, как заданному</span><span class="sxs-lookup"><span data-stu-id="f83e5-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="f83e5-121">Синтаксический анализ конфигурации узла</span><span class="sxs-lookup"><span data-stu-id="f83e5-121">Parsing Host Config</span></span>
1. <span data-ttu-id="f83e5-122">Список действий</span><span class="sxs-lookup"><span data-stu-id="f83e5-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="f83e5-123">Управление версиями</span><span class="sxs-lookup"><span data-stu-id="f83e5-123">Versioning</span></span>

1. <span data-ttu-id="f83e5-124">Модуль подготовки отчетов **необходимо** реализации определенной версии схемы.</span><span class="sxs-lookup"><span data-stu-id="f83e5-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="f83e5-125">`AdaptiveCard` Конструктор **необходимо** предоставить `version` свойство, значение по умолчанию, основанное на текущей версии схемы</span><span class="sxs-lookup"><span data-stu-id="f83e5-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="f83e5-126">Если модуль подготовки отчетов обнаруживает `version` свойства в `AdaptiveCard` , больше, чем поддерживаемая версия, его **необходимо** возвращают `fallbackText` вместо этого.</span><span class="sxs-lookup"><span data-stu-id="f83e5-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="f83e5-127">Подготовка к просмотру</span><span class="sxs-lookup"><span data-stu-id="f83e5-127">Rendering</span></span>

<span data-ttu-id="f83e5-128">`AdaptiveCard` Состоит из `body` и `actions`.</span><span class="sxs-lookup"><span data-stu-id="f83e5-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="f83e5-129">`body` — Это коллекция `CardElement`, там будет перечислять и отображаются в порядке.</span><span class="sxs-lookup"><span data-stu-id="f83e5-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="f83e5-130">Каждый элемент **необходимо** stretch на ширину его родительского элемента (представить `display: block` в формате HTML).</span><span class="sxs-lookup"><span data-stu-id="f83e5-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="f83e5-131">Модуль подготовки отчетов **необходимо** игнорировать неизвестный элемент типы и продолжения обработки остальной части полезных данных.</span><span class="sxs-lookup"><span data-stu-id="f83e5-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="f83e5-132">Интервал и разделители</span><span class="sxs-lookup"><span data-stu-id="f83e5-132">Spacing and Separators</span></span>

1. <span data-ttu-id="f83e5-133">`spacing` Свойство для каждого элемента влияет на объем пространства между **текущей** элемент и элемент управления **до** его.</span><span class="sxs-lookup"><span data-stu-id="f83e5-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="f83e5-134">Интервал между **необходимо только** применялись при появлении фактически элемент предшествует ей.</span><span class="sxs-lookup"><span data-stu-id="f83e5-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="f83e5-135">(Например, нельзя применить к первому элементу в массиве)</span><span class="sxs-lookup"><span data-stu-id="f83e5-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="f83e5-136">Модуль подготовки отчетов **необходимо** поиск пространства из `hostConfig` пробелы для перечисления значение, применяемое для текущего элемента.</span><span class="sxs-lookup"><span data-stu-id="f83e5-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="f83e5-137">Если элемент имеет `separator` значение `true`, затем видимой строки **необходимо** рисоваться между текущего элемента и до его.</span><span class="sxs-lookup"><span data-stu-id="f83e5-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="f83e5-138">Разделительной линии **необходимо** быть нарисован с использованием `container.style.default.foregroundColor`.</span><span class="sxs-lookup"><span data-stu-id="f83e5-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="f83e5-139">Разделитель **необходимо только** рисуется, если элемент **IS NOT** в массиве первыми.</span><span class="sxs-lookup"><span data-stu-id="f83e5-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="f83e5-140">Столбцы</span><span class="sxs-lookup"><span data-stu-id="f83e5-140">Columns</span></span>

1. <span data-ttu-id="f83e5-141">`Column` `width` **НЕОБХОДИМО** интерпретироваться по «auto», «stretch» или взвешенных отношение.</span><span class="sxs-lookup"><span data-stu-id="f83e5-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="f83e5-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="f83e5-142">TextBlock</span></span>

1. <span data-ttu-id="f83e5-143">TextBlock **необходимо** занимают одну строку, если `wrap` свойство `true`.</span><span class="sxs-lookup"><span data-stu-id="f83e5-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="f83e5-144">Текстовый блок **следует** все лишние текст с многоточием (...)</span><span class="sxs-lookup"><span data-stu-id="f83e5-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="f83e5-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="f83e5-145">Markdown</span></span>

1. <span data-ttu-id="f83e5-146">Разрешить адаптивной карты для подмножества Markdown и **следует** будут поддерживаться в `TextBlock`.</span><span class="sxs-lookup"><span data-stu-id="f83e5-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="f83e5-147">См. полный [требования markdown](../authoring-cards/text-features.md)</span><span class="sxs-lookup"><span data-stu-id="f83e5-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="f83e5-148">Функции форматирования</span><span class="sxs-lookup"><span data-stu-id="f83e5-148">Formatting functions</span></span>

1. <span data-ttu-id="f83e5-149">`TextBlock` позволяет [функций форматирования даты и времени](../authoring-cards/text-features.md) , **необходимо** поддерживаться на каждый модуль подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="f83e5-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="f83e5-150">**ВСЕ СБОИ необходимо** отображения необработанную строку в карточке.</span><span class="sxs-lookup"><span data-stu-id="f83e5-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="f83e5-151">Понятное сообщение попытки.</span><span class="sxs-lookup"><span data-stu-id="f83e5-151">No friendly message attempted.</span></span> <span data-ttu-id="f83e5-152">(Целью для информировании разработчика немедленно существует проблема связана с)</span><span class="sxs-lookup"><span data-stu-id="f83e5-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="f83e5-153">TODO: Включить регулярных выражений</span><span class="sxs-lookup"><span data-stu-id="f83e5-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="f83e5-154">Изображений</span><span class="sxs-lookup"><span data-stu-id="f83e5-154">Images</span></span>

1. <span data-ttu-id="f83e5-155">Модуль подготовки отчетов **следует** позволяют размещать приложения знать, когда были загружены все образы HTTP, и она «полностью rendererd»</span><span class="sxs-lookup"><span data-stu-id="f83e5-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendererd"</span></span>
1. <span data-ttu-id="f83e5-156">Модуль подготовки отчетов **необходимо** проверить файл конфигурации узла `maxImageSize` param при загрузке по протоколу HTTP изображений</span><span class="sxs-lookup"><span data-stu-id="f83e5-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="f83e5-157">Модуль подготовки отчетов **необходимо** поддержки `.png` и `.jpeg`</span><span class="sxs-lookup"><span data-stu-id="f83e5-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="f83e5-158">Модуль подготовки отчетов **следует** поддержки `.gif` образов</span><span class="sxs-lookup"><span data-stu-id="f83e5-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="f83e5-159">Конфигурации узла</span><span class="sxs-lookup"><span data-stu-id="f83e5-159">Host Config</span></span>

* <span data-ttu-id="f83e5-160">TODO: Какой должна быть значения по умолчанию?</span><span class="sxs-lookup"><span data-stu-id="f83e5-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="f83e5-161">Должны ли они все имеют его?</span><span class="sxs-lookup"><span data-stu-id="f83e5-161">Should they all share it?</span></span> <span data-ttu-id="f83e5-162">Общий файл hostConfig.json следует внедрить в двоичные файлы?</span><span class="sxs-lookup"><span data-stu-id="f83e5-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="f83e5-163">TODO: Я думаю, что HostConfig должен быть с версией, а также для анализа?</span><span class="sxs-lookup"><span data-stu-id="f83e5-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="f83e5-164">[`HostConfig`](host-config.md) является объектом общей конфигурации, который указывает, как адаптивной модуля подготовки отчетов карты создает пользовательский Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f83e5-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="f83e5-165">Благодаря этому свойства, которые зависят от платформы для использования несколькими модулями подготовки отчетов на разных платформах и устройствах.</span><span class="sxs-lookup"><span data-stu-id="f83e5-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="f83e5-166">Он также позволяет набор инструментов, чтобы создать, который дает представление о внешнего вида и поведения в карточке, будет иметь для данной среды.</span><span class="sxs-lookup"><span data-stu-id="f83e5-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="f83e5-167">Модули подготовки отчетов **необходимо** предоставлять **Host Config** параметр для размещения приложений</span><span class="sxs-lookup"><span data-stu-id="f83e5-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="f83e5-168">Все элементы **необходимо** применить различные стили в соответствии с их соответствующие параметры конфигурации узла</span><span class="sxs-lookup"><span data-stu-id="f83e5-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="f83e5-169">Стилизация собственной платформы</span><span class="sxs-lookup"><span data-stu-id="f83e5-169">Native platform styling</span></span>

1. <span data-ttu-id="f83e5-170">Каждый тип элемента **следует** присоединить стиля собственной платформы с помощью созданного элемента пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f83e5-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="f83e5-171">Например в формате HTML, мы добавили класс CSS в типы элементов, а в XAML нам назначить определенный стиль.</span><span class="sxs-lookup"><span data-stu-id="f83e5-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="f83e5-172">Расширение среды</span><span class="sxs-lookup"><span data-stu-id="f83e5-172">Extensibility</span></span> 

1. <span data-ttu-id="f83e5-173">Модуль подготовки отчетов **необходимо** позволяют размещать приложения в переопределите модулей подготовки отчетов по умолчанию элемент.</span><span class="sxs-lookup"><span data-stu-id="f83e5-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="f83e5-174">Например, замените `TextBlock` отрисовка с помощью собственную логику.</span><span class="sxs-lookup"><span data-stu-id="f83e5-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="f83e5-175">Модуль подготовки отчетов **необходимо** позволяют размещать приложения зарегистрировать типы настраиваемых элементов.</span><span class="sxs-lookup"><span data-stu-id="f83e5-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="f83e5-176">Например, добавить поддержку для пользовательской `Rating` элемент</span><span class="sxs-lookup"><span data-stu-id="f83e5-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="f83e5-177">Модуль подготовки отчетов **необходимо** позволяют размещать приложения удалить поддержку элемент по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f83e5-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="f83e5-178">Например, удалите `Action.Submit` по желанию не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f83e5-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="f83e5-179">Действия</span><span class="sxs-lookup"><span data-stu-id="f83e5-179">Actions</span></span>

1. <span data-ttu-id="f83e5-180">Если HostConfig `supportsInteractivity` — `false`, модуль подготовки отчетов **не должна** отрисовки каких-либо действий.</span><span class="sxs-lookup"><span data-stu-id="f83e5-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="f83e5-181">`actions` Свойство **необходимо** отображены в виде кнопок в панели действий, обычно в нижней части карты какого-либо рода.</span><span class="sxs-lookup"><span data-stu-id="f83e5-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="f83e5-182">При нажатии кнопки его **необходимо** разрешить ведущее приложение для обработки события.</span><span class="sxs-lookup"><span data-stu-id="f83e5-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="f83e5-183">Событие **необходимо** pass вместе все связанные свойства с действием</span><span class="sxs-lookup"><span data-stu-id="f83e5-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="f83e5-184">Событие **необходимо** передавать `AdaptiveCard` которого была выполнена</span><span class="sxs-lookup"><span data-stu-id="f83e5-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="f83e5-185">Действие</span><span class="sxs-lookup"><span data-stu-id="f83e5-185">Action</span></span> | <span data-ttu-id="f83e5-186">Поведение</span><span class="sxs-lookup"><span data-stu-id="f83e5-186">Behavior</span></span>
--- | ---
<span data-ttu-id="f83e5-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="f83e5-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="f83e5-188">Открыть внешний URL-адрес для просмотра</span><span class="sxs-lookup"><span data-stu-id="f83e5-188">Open an external URL for viewing</span></span>
<span data-ttu-id="f83e5-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="f83e5-189">**Action.ShowCard**</span></span> | <span data-ttu-id="f83e5-190">Запрашивает вложенных карту для отображения пользователю.</span><span class="sxs-lookup"><span data-stu-id="f83e5-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="f83e5-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="f83e5-191">**Action.Submit**</span></span> | <span data-ttu-id="f83e5-192">Задайте для всех элементов ввода необходимо собирать в объект, который затем отправляется пользователю через определенные ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="f83e5-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="f83e5-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="f83e5-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="f83e5-194">`Action.OpenUrl` **СЛЕДУЕТ** откройте URL-адрес, с помощью механизма собственной платформы</span><span class="sxs-lookup"><span data-stu-id="f83e5-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="f83e5-195">Если вы не сможете настроить его **необходимо** вызывают событие, чтобы ведущее приложение для обработки, открыв URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="f83e5-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="f83e5-196">Это событие **необходимо** разрешить приложению узла переопределить поведение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f83e5-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="f83e5-197">Например сообщите им, откройте URL-адрес в собственные приложения.</span><span class="sxs-lookup"><span data-stu-id="f83e5-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="f83e5-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="f83e5-198">Action.ShowCard</span></span>

1. <span data-ttu-id="f83e5-199">`Action.ShowCard` **НЕОБХОДИМО** поддерживаться определенным образом, на основе параметра hostConfig.</span><span class="sxs-lookup"><span data-stu-id="f83e5-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="f83e5-200">Существует два режима: встроенные и всплывающее окно.</span><span class="sxs-lookup"><span data-stu-id="f83e5-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="f83e5-201">Встроенные карты **следует** переключения видимости карты автоматически.</span><span class="sxs-lookup"><span data-stu-id="f83e5-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="f83e5-202">В режиме всплывающее окно, событие **следует** вызывать их срабатывание ведущее приложение для отображения карты каким-либо образом.</span><span class="sxs-lookup"><span data-stu-id="f83e5-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="f83e5-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="f83e5-203">Action.Submit</span></span>

<span data-ttu-id="f83e5-204">Отправить действие ведет себя как отправку формы HTML, за исключением того, что где HTML обычно запускает запрос HTTP post, адаптивной карты остается до каждого узла приложения, чтобы определить, что «submit» означает, что к ним.</span><span class="sxs-lookup"><span data-stu-id="f83e5-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="f83e5-205">При этом **необходимо** порождения события пользователь касается invokved действие.</span><span class="sxs-lookup"><span data-stu-id="f83e5-205">When this **MUST** raise an event the user taps the action invokved.</span></span>  
1. <span data-ttu-id="f83e5-206">`data` Свойство **необходимо** включаться в полезных данных обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="f83e5-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="f83e5-207">Для `Action.Submit`, модуль подготовки отчетов **необходимо** сбор всех входных данных на карте и извлечь их значения.</span><span class="sxs-lookup"><span data-stu-id="f83e5-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="f83e5-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="f83e5-208">selectAction</span></span>

1. <span data-ttu-id="f83e5-209">Если конфигурация узла `supportedInteractivity` — `false` то `selectAction` **не должна** отображаются в виде цель касания.</span><span class="sxs-lookup"><span data-stu-id="f83e5-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="f83e5-210">`Image`, `ColumnSet`, и `Column` предлагают `selectAction` свойства, который **следует** выполняться при вызове пользователем, например, коснувшись элемента.</span><span class="sxs-lookup"><span data-stu-id="f83e5-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="f83e5-211">Ввод данных</span><span class="sxs-lookup"><span data-stu-id="f83e5-211">Inputs</span></span>

1. <span data-ttu-id="f83e5-212">Если HostConfig `supportsInteractivity` — `false` там **не должна** отрисовки никаких входных данных.</span><span class="sxs-lookup"><span data-stu-id="f83e5-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="f83e5-213">Входные данные **следует** визуализация с помощью наивысшего качества возможных.</span><span class="sxs-lookup"><span data-stu-id="f83e5-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="f83e5-214">Например `Input.Date` в идеале предлагало управляющий элемент выбора даты в отношении пользователя, но если это невозможно в стеке пользовательского интерфейса, то модуль подготовки отчетов **необходимо** откат подготовки отчетов к просмотру обычное текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="f83e5-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="f83e5-215">Модуль подготовки отчетов **следует** отображения `placeholderText` по возможности</span><span class="sxs-lookup"><span data-stu-id="f83e5-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="f83e5-216">Модуль подготовки отчетов **не** , придется реализовать проверку входных данных.</span><span class="sxs-lookup"><span data-stu-id="f83e5-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="f83e5-217">Адаптивная карт необходимо планировать для проверки любых полученных данных с их стороны.</span><span class="sxs-lookup"><span data-stu-id="f83e5-217">Users of Adaptive Cards must plan to validate any receieved data on their end.</span></span>
5. <span data-ttu-id="f83e5-218">Входная привязка значение **необходимо** должным образом экранировать</span><span class="sxs-lookup"><span data-stu-id="f83e5-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="f83e5-219">Объект **необходимо** возвращаться в приложение узла следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f83e5-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="f83e5-220">Мы не даем любой обещания проверки входных данных в адаптивной карт, поэтому ответственность за сторона, для правильного синтаксического анализа ответа.</span><span class="sxs-lookup"><span data-stu-id="f83e5-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="f83e5-221">Например Input.Number может вернуть «hello», и они должны быть разработаны для этого.</span><span class="sxs-lookup"><span data-stu-id="f83e5-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="f83e5-222">События</span><span class="sxs-lookup"><span data-stu-id="f83e5-222">Events</span></span>

1. <span data-ttu-id="f83e5-223">Модуль подготовки отчетов **следует** инициировать событие при изменении видимости элемента, что позволяет приложению узла для прокрутки карточки в позицию.</span><span class="sxs-lookup"><span data-stu-id="f83e5-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
