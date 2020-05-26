---
title: Язык шаблонов адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 1b5a7df25eedb96ec6edfe02912d328ab59d2801
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631347"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="b23e2-102">Язык шаблонов адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="b23e2-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="b23e2-103">При работе с шаблонами можно отделить **данные** от **макета** в адаптивной карточке.</span><span class="sxs-lookup"><span data-stu-id="b23e2-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="b23e2-104">Язык шаблонов — это синтаксис, используемый для создания такого шаблона.</span><span class="sxs-lookup"><span data-stu-id="b23e2-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="b23e2-105">Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).</span><span class="sxs-lookup"><span data-stu-id="b23e2-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="b23e2-106">**Критические изменения** в **версии-кандидате за май 2020 г.**</span><span class="sxs-lookup"><span data-stu-id="b23e2-106">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="b23e2-107">Мы приложили немало усилий, чтобы этот выпуск увидел свет, и уже находимся на финишной прямой.</span><span class="sxs-lookup"><span data-stu-id="b23e2-107">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="b23e2-108">В окончательную версию нам пришлось внести небольшие критические изменения.</span><span class="sxs-lookup"><span data-stu-id="b23e2-108">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="b23e2-109">Критические изменения в версии за май 2020 г.</span><span class="sxs-lookup"><span data-stu-id="b23e2-109">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="b23e2-110">Синтаксис привязки изменен с `{...}` на `${...}`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-110">The binding syntax changed from `{...}` to `${...}`</span></span>
    * <span data-ttu-id="b23e2-111">Например, вместо `"text": "Hello {name}"` теперь используется `"text": "Hello ${name}"`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-111">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
    
## <a name="binding-to-data"></a><span data-ttu-id="b23e2-112">Привязка к данным</span><span class="sxs-lookup"><span data-stu-id="b23e2-112">Binding to data</span></span>

<span data-ttu-id="b23e2-113">Создать шаблон так же просто, как заменить нестатическое содержимое карточки на выражения привязки.</span><span class="sxs-lookup"><span data-stu-id="b23e2-113">Writing a template is as simple as replacing the "non-static" content of your card with "binding expressions".</span></span>

### <a name="static-card-payload"></a><span data-ttu-id="b23e2-114">Полезные данные статической карточки</span><span class="sxs-lookup"><span data-stu-id="b23e2-114">Static card payload</span></span>

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### <a name="template-payload"></a><span data-ttu-id="b23e2-115">Полезные данные шаблона</span><span class="sxs-lookup"><span data-stu-id="b23e2-115">Template payload</span></span>

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* <span data-ttu-id="b23e2-116">Выражения привязки можно размещать везде, где может находиться статическое содержимое.</span><span class="sxs-lookup"><span data-stu-id="b23e2-116">Binding expressions can be placed just about anywhere that static content can be</span></span>
* <span data-ttu-id="b23e2-117">Синтаксис привязки начинается с `${` и заканчивается на `}`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-117">The binding syntax starts with `${` and ends with `}`.</span></span> <span data-ttu-id="b23e2-118">Например, так: `${myProperty}`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-118">E.g., `${myProperty}`</span></span>
* <span data-ttu-id="b23e2-119">Используйте *запись через точку* для доступа к вложенным объектам в иерархии объектов.</span><span class="sxs-lookup"><span data-stu-id="b23e2-119">Use *Dot-notation* to access sub-objects of an object hierarchy.</span></span> <span data-ttu-id="b23e2-120">Например, так: `${myParent.myChild}`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-120">E.g., `${myParent.myChild}`</span></span>
* <span data-ttu-id="b23e2-121">Правильная обработка значений NULL гарантирует отсутствие исключений при доступе к свойству NULL в графе объектов.</span><span class="sxs-lookup"><span data-stu-id="b23e2-121">Graceful null handling ensures you won't get exceptions if you access a null property in an object graph</span></span>
* <span data-ttu-id="b23e2-122">Используйте *синтаксис индексатора* для получения свойств по ключу или элементам в массиве.</span><span class="sxs-lookup"><span data-stu-id="b23e2-122">Use *Indexer syntax* to retrieve properties by key or items in an array.</span></span> <span data-ttu-id="b23e2-123">Например, так: `${myArray[0]}`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-123">E.g., `${myArray[0]}`</span></span>

## <a name="providing-the-data"></a><span data-ttu-id="b23e2-124">Предоставление данных</span><span class="sxs-lookup"><span data-stu-id="b23e2-124">Providing the data</span></span>

<span data-ttu-id="b23e2-125">Теперь, когда у вас есть шаблон, можно внести в него данные.</span><span class="sxs-lookup"><span data-stu-id="b23e2-125">Now that you have a template, you'll want to provide the data that makes it complete.</span></span> <span data-ttu-id="b23e2-126">Это можно сделать одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="b23e2-126">You have two options to do this:</span></span>

1. <span data-ttu-id="b23e2-127">**Вариант A — встроив данные в полезные данные шаблона**.</span><span class="sxs-lookup"><span data-stu-id="b23e2-127">**Option A: Inline within the template payload**.</span></span> <span data-ttu-id="b23e2-128">Данные можно встроить в полезные данные шаблона `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-128">You can provide the data inline within the `AdaptiveCard` template payload.</span></span> <span data-ttu-id="b23e2-129">Для этого просто добавьте атрибут `$data` в корневой объект `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-129">To do so, simply add a `$data` attribute to the root `AdaptiveCard` object.</span></span>
2. <span data-ttu-id="b23e2-130">**Вариант Б — внеся данные в качестве отдельного объекта данных**.</span><span class="sxs-lookup"><span data-stu-id="b23e2-130">**Option B: As a separate data object**.</span></span> <span data-ttu-id="b23e2-131">В этом случае вы предоставляете два отдельных объекта [пакету SDK для создания шаблонов](sdk.md) во время его выполнения: `template` и `data`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-131">With this option you provide two separate objects to the [Templating SDK](sdk.md) at runtime: the `template` and the `data`.</span></span> <span data-ttu-id="b23e2-132">Такой подход более популярен, так как обычно создается шаблон, динамические данные в который добавляются позже.</span><span class="sxs-lookup"><span data-stu-id="b23e2-132">This will be the more common approach, since typically you will create a template and want to provide dynamic data later.</span></span>

### <a name="option-a-inline-data"></a><span data-ttu-id="b23e2-133">Вариант A — встроенные данные</span><span class="sxs-lookup"><span data-stu-id="b23e2-133">Option A: Inline data</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    },
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

### <a name="option-b-separating-the-template-from-the-data"></a><span data-ttu-id="b23e2-134">Вариант Б — Отделение шаблона от данных</span><span class="sxs-lookup"><span data-stu-id="b23e2-134">Option B: Separating the template from the data</span></span>

<span data-ttu-id="b23e2-135">Вы можете выбрать другой, более распространенный подход: создать многократно используемый шаблон адаптивной карточки, не включая в него данные.</span><span class="sxs-lookup"><span data-stu-id="b23e2-135">Alternatively (and more likely), you'll create a re-usable card template without including the data.</span></span> <span data-ttu-id="b23e2-136">Такой шаблон можно сохранить в файле и добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="b23e2-136">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="b23e2-137">**Файл EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="b23e2-137">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

<span data-ttu-id="b23e2-138">Затем вы загружаете его и предоставляете данные во время выполнения с помощью [пакетов SDK для работы с шаблонами](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b23e2-138">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="b23e2-139">**Пример JavaScript**</span><span class="sxs-lookup"><span data-stu-id="b23e2-139">**JavaScript example**</span></span>

<span data-ttu-id="b23e2-140">Использование пакета [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).</span><span class="sxs-lookup"><span data-stu-id="b23e2-140">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var card = template.expand({
    $root: {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    }
});

// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a><span data-ttu-id="b23e2-141">Поддержка конструктора</span><span class="sxs-lookup"><span data-stu-id="b23e2-141">Designer Support</span></span>

<span data-ttu-id="b23e2-142">Конструктор адаптивных карт теперь включает поддержку шаблонов.</span><span class="sxs-lookup"><span data-stu-id="b23e2-142">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="b23e2-143">Чтобы поработать с конструктором, перейдите по адресу **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .</span><span class="sxs-lookup"><span data-stu-id="b23e2-143">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="b23e2-144">[![Образ](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="b23e2-144">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="b23e2-145">**Sample Data Editor** (Редактор примера данных) — введите здесь пример данных, чтобы оценить карту с привязкой к данным в режиме предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="b23e2-145">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="b23e2-146">На этой панели есть небольшая кнопка для заполнения структуры данных из существующего примера данных.</span><span class="sxs-lookup"><span data-stu-id="b23e2-146">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="b23e2-147">**Preview Mode** (Режим предварительного просмотра) — нажмите кнопку на панели инструментов, чтобы переключиться между режимами редактирования и предварительного просмотра данных.</span><span class="sxs-lookup"><span data-stu-id="b23e2-147">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="b23e2-148">**Open Sample** (Открыть пример) — нажмите эту кнопку, чтобы открыть примеры полезных данных.</span><span class="sxs-lookup"><span data-stu-id="b23e2-148">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="b23e2-149">Расширенная привязка</span><span class="sxs-lookup"><span data-stu-id="b23e2-149">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="b23e2-150">Области привязки</span><span class="sxs-lookup"><span data-stu-id="b23e2-150">Binding scopes</span></span>

<span data-ttu-id="b23e2-151">Есть несколько зарезервированных ключевых слов для доступа к разным областям привязки.</span><span class="sxs-lookup"><span data-stu-id="b23e2-151">There are a few reserved keywords to access various binding scopes.</span></span> 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="b23e2-152">Назначение элементам контекста данных</span><span class="sxs-lookup"><span data-stu-id="b23e2-152">Assigning a data context to elements</span></span>

<span data-ttu-id="b23e2-153">Чтобы назначить любому элементу "контекст данных", добавьте к нужному элементу атрибут `$data`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-153">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

```json
{
    "type": "Container",
    "$data": "${mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': ${mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: ${$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="b23e2-154">Повторяющиеся элементы в массиве</span><span class="sxs-lookup"><span data-stu-id="b23e2-154">Repeating items in an array</span></span>

* <span data-ttu-id="b23e2-155">Если свойство `$data` в элементе адаптивной карточки привязано к **массиву**, то такой элемент **будет повторяться для каждого элемента массива**.</span><span class="sxs-lookup"><span data-stu-id="b23e2-155">If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="b23e2-156">Любые выражения привязки (`${myProperty}`) в значениях свойств будут относиться к **отдельному элементу** в массиве.</span><span class="sxs-lookup"><span data-stu-id="b23e2-156">Any binding expressions (`${myProperty}`) used in property values will be scoped to the **individual item** within the array.</span></span>
* <span data-ttu-id="b23e2-157">Если выполнена привязка к массиву строк, для доступа к отдельному строковому элементу используйте `${$data}`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-157">If binding to an array of strings, use `${$data}` to access the individual string element.</span></span> <span data-ttu-id="b23e2-158">Например, так: `"text": "${$data}"`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-158">E.g., `"text": "${$data}"`</span></span>

<span data-ttu-id="b23e2-159">Например, элемент `TextBlock` в приведенном ниже примере будет повторяться три раза, так как `$data` является массивом.</span><span class="sxs-lookup"><span data-stu-id="b23e2-159">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="b23e2-160">Обратите внимание, что свойство `text` привязано к свойству `name` отдельного объекта в этом массиве.</span><span class="sxs-lookup"><span data-stu-id="b23e2-160">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

```json
{
    "type": "Container",
    "items": [
        {
            "type": "TextBlock",
            "$data": [
                { "name": "Matt" }, 
                { "name": "David" }, 
                { "name": "Thomas" }
            ],
            "text": "${name}"
        }
    ]
}
```

<span data-ttu-id="b23e2-161">**Результат:**</span><span class="sxs-lookup"><span data-stu-id="b23e2-161">**Resulting in:**</span></span>

```json
{
    "type": "Container",
    "items": [ 
        {
            "type": "TextBlock",
            "text": "Matt"
        },
        {
            "type": "TextBlock",
            "text": "David"
        }
        {
            "type": "TextBlock",
            "text": "Thomas"
        }
    ]
}
```

## <a name="built-in-functions"></a><span data-ttu-id="b23e2-162">Встроенные функции</span><span class="sxs-lookup"><span data-stu-id="b23e2-162">Built-in functions</span></span>

<span data-ttu-id="b23e2-163">Язык шаблонов нельзя считать полноценным без разнообразных вспомогательных функций.</span><span class="sxs-lookup"><span data-stu-id="b23e2-163">No templating language is complete without a rich suite of helper functions.</span></span> <span data-ttu-id="b23e2-164">Решение для создания шаблонов адаптивных карточек основано на [языке адаптивных выражений](https://aka.ms/adaptive-expressions) (AEL), который является открытым стандартом для объявления выражений с возможностью их оценки на разных платформах.</span><span class="sxs-lookup"><span data-stu-id="b23e2-164">Adaptive Card Templating is built on top of the [Adaptive Expression Language](https://aka.ms/adaptive-expressions) (AEL), which is an open standard for declaring expressions that can be evaluated on many different platforms.</span></span> <span data-ttu-id="b23e2-165">Это — расширенный набор Logic Apps, поэтому вы можете использовать такой же синтаксис, как, например, в Power Automate.</span><span class="sxs-lookup"><span data-stu-id="b23e2-165">And it's a proper superset of "Logic Apps", so you can use similar syntax as Power Automate, etc.</span></span>

<span data-ttu-id="b23e2-166">**Мы рассмотрели лишь небольшую часть встроенных функций.**</span><span class="sxs-lookup"><span data-stu-id="b23e2-166">**This is just a small sampling of the built-in functions.**</span></span>

<span data-ttu-id="b23e2-167">Ознакомьтесь с полным списком [предварительно созданных функций для языка адаптивных выражений](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="b23e2-167">Check out the full list of [Adaptive Expression Language Pre-built functions](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).</span></span>

### <a name="conditional-evaluation"></a><span data-ttu-id="b23e2-168">Условная оценка:</span><span class="sxs-lookup"><span data-stu-id="b23e2-168">Conditional evaluation</span></span>

* <span data-ttu-id="b23e2-169">if(*выражение*, *если_истина*, *если_ложь*).</span><span class="sxs-lookup"><span data-stu-id="b23e2-169">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="b23e2-170">**Пример для `if`**</span><span class="sxs-lookup"><span data-stu-id="b23e2-170">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="parsing-json"></a><span data-ttu-id="b23e2-171">Анализ JSON</span><span class="sxs-lookup"><span data-stu-id="b23e2-171">Parsing JSON</span></span>

* <span data-ttu-id="b23e2-172">json(*jsonString*) — анализ строки JSON</span><span class="sxs-lookup"><span data-stu-id="b23e2-172">json(*jsonString*) - Parse a JSON string</span></span>

<span data-ttu-id="b23e2-173">**Пример для `json`**</span><span class="sxs-lookup"><span data-stu-id="b23e2-173">**`json` example**</span></span>

<span data-ttu-id="b23e2-174">Это ответ Azure DevOps для ситуации, когда свойство `message` содержит сериализованную строку в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="b23e2-174">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="b23e2-175">Для обращения к значениям в этой строке следует использовать в шаблоне функцию `json`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-175">In order to access values within the string, we need to use the `json` function in our template.</span></span>

<span data-ttu-id="b23e2-176">**Данные**</span><span class="sxs-lookup"><span data-stu-id="b23e2-176">**Data**</span></span> 

```json
{
    "id": "1291525457129548",
    "status": 4,
    "author": "Matt Hidinger",
    "message": "{\"type\":\"Deployment\",\"buildId\":\"9542982\",\"releaseId\":\"129\",\"buildNumber\":\"20180504.3\",\"releaseName\":\"Release-104\",\"repoProvider\":\"GitHub\"}",
    "start_time": "2018-05-04T18:05:33.3087147Z",
    "end_time": "2018-05-04T18:05:33.3087147Z"
}
```

<span data-ttu-id="b23e2-177">**Использование**</span><span class="sxs-lookup"><span data-stu-id="b23e2-177">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "${json(message).releaseName}"
}
```

<span data-ttu-id="b23e2-178">**Результат**</span><span class="sxs-lookup"><span data-stu-id="b23e2-178">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="b23e2-179">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="b23e2-179">Custom functions</span></span>

<span data-ttu-id="b23e2-180">Пользовательские функции поддерживаются через API в [пакетах SDK для создания шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b23e2-180">Custom functions are supported via APIs in the [Templating SDKs](sdk.md).</span></span> 

## <a name="conditional-layout-with-when"></a><span data-ttu-id="b23e2-181">Условный макет с `$when`</span><span class="sxs-lookup"><span data-stu-id="b23e2-181">Conditional layout with `$when`</span></span>

<span data-ttu-id="b23e2-182">Чтобы игнорировать элемент целиком при выполнении определенного условия, используйте свойство `$when`.</span><span class="sxs-lookup"><span data-stu-id="b23e2-182">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="b23e2-183">Если `$when` имеет значение `false`, такой элемент не будет отображаться для пользователя.</span><span class="sxs-lookup"><span data-stu-id="b23e2-183">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "${price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "${price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a><span data-ttu-id="b23e2-184">Компоновка шаблонов</span><span class="sxs-lookup"><span data-stu-id="b23e2-184">Composing templates</span></span>

<span data-ttu-id="b23e2-185">Сейчас не поддерживается компоновка шаблона из отдельных частей.</span><span class="sxs-lookup"><span data-stu-id="b23e2-185">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="b23e2-186">Но мы рассматриваем варианты такого механизма и скоро сообщим вам о результатах.</span><span class="sxs-lookup"><span data-stu-id="b23e2-186">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="b23e2-187">Мы будем рады любым вашим идеям!</span><span class="sxs-lookup"><span data-stu-id="b23e2-187">Any thoughts here welcome!</span></span>

## <a name="examples"></a><span data-ttu-id="b23e2-188">Примеры</span><span class="sxs-lookup"><span data-stu-id="b23e2-188">Examples</span></span>

<span data-ttu-id="b23e2-189">Изучите обновленную [страницу примеров](https://adaptivecards.io/samples), где представлены новые виды шаблонов карточек.</span><span class="sxs-lookup"><span data-stu-id="b23e2-189">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
