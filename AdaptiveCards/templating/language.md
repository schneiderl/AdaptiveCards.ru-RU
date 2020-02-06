---
title: Язык шаблонов адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 2c583f774451e60f825cd8fd2c38f2ea34c2f8de
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145404"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="20351-102">Язык шаблонов адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="20351-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="20351-103">При работе с шаблонами можно отделить **данные** от **макета** в адаптивной карточке.</span><span class="sxs-lookup"><span data-stu-id="20351-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="20351-104">Язык шаблонов — это синтаксис, используемый для создания такого шаблона.</span><span class="sxs-lookup"><span data-stu-id="20351-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="20351-105">Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).</span><span class="sxs-lookup"><span data-stu-id="20351-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="20351-106">Эти функции предоставляются в **ознакомительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="20351-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="20351-107">Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.</span><span class="sxs-lookup"><span data-stu-id="20351-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="20351-108">При создании шаблона вы можете включить в него данные с помощью встроенной структуры `AdaptiveCard` или во время выполнения с помощью [пакетов SDK для работы с шаблонами](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="20351-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="20351-109">Включение данных в карточку</span><span class="sxs-lookup"><span data-stu-id="20351-109">Specify data within the card</span></span>

<span data-ttu-id="20351-110">Чтобы добавить полезные данные непосредственно в адаптивную карточку, добавьте атрибут `$data` в `AdaptiveCard`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="20351-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="20351-111">Привязка к данным</span><span class="sxs-lookup"><span data-stu-id="20351-111">Binding to the data</span></span>

<span data-ttu-id="20351-112">Можно выполнить привязку к данным в `body` или `actions` карточки.</span><span class="sxs-lookup"><span data-stu-id="20351-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="20351-113">Синтаксис привязки начинается с `{` и заканчивается `}`.</span><span class="sxs-lookup"><span data-stu-id="20351-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="20351-114">Например, так: `{myProperty}`.</span><span class="sxs-lookup"><span data-stu-id="20351-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="20351-115">Запись через точку для доступа к вложенным объектам</span><span class="sxs-lookup"><span data-stu-id="20351-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="20351-116">Синтаксис индексатора для получения свойств по ключу или элементов массива</span><span class="sxs-lookup"><span data-stu-id="20351-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="20351-117">Корректная обработка значений NULL для глубоких иерархий</span><span class="sxs-lookup"><span data-stu-id="20351-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="20351-118">*Скоро появится документация по синтаксису экранирования*</span><span class="sxs-lookup"><span data-stu-id="20351-118">*Escape syntax documentation to come soon*</span></span>

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
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="20351-119">Отделение шаблона от данных</span><span class="sxs-lookup"><span data-stu-id="20351-119">Separating the template from the data</span></span>

<span data-ttu-id="20351-120">Вы можете выбрать другой, более распространенный подход: создать многократно используемый "шаблон" адаптивной карточки, не включая в него данные.</span><span class="sxs-lookup"><span data-stu-id="20351-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="20351-121">Такой шаблон можно сохранить в файле и добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="20351-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="20351-122">**Файл EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="20351-122">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptivCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

<span data-ttu-id="20351-123">Затем вы загружаете его и предоставляете данные во время выполнения с помощью [пакетов SDK для работы с шаблонами](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="20351-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="20351-124">**Пример JavaScript**</span><span class="sxs-lookup"><span data-stu-id="20351-124">**JavaScript example**</span></span>

<span data-ttu-id="20351-125">Использование пакета [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).</span><span class="sxs-lookup"><span data-stu-id="20351-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
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
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a><span data-ttu-id="20351-126">Поддержка конструктора</span><span class="sxs-lookup"><span data-stu-id="20351-126">Designer Support</span></span>

<span data-ttu-id="20351-127">Конструктор адаптивных карт теперь включает поддержку шаблонов.</span><span class="sxs-lookup"><span data-stu-id="20351-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="20351-128">Чтобы поработать с конструктором, перейдите по адресу **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .</span><span class="sxs-lookup"><span data-stu-id="20351-128">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="20351-129">[![Образ](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="20351-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="20351-130">**Sample Data Editor** (Редактор примера данных) — введите здесь пример данных, чтобы оценить карту с привязкой к данным в режиме предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="20351-130">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="20351-131">На этой панели есть небольшая кнопка для заполнения структуры данных из существующего примера данных.</span><span class="sxs-lookup"><span data-stu-id="20351-131">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="20351-132">**Data Structure** (Структура данных) — структура, которая определяет архитектуру примера данных.</span><span class="sxs-lookup"><span data-stu-id="20351-132">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="20351-133">Поля можно перетащить в область конструктора, чтобы создать привязку к ним.</span><span class="sxs-lookup"><span data-stu-id="20351-133">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="20351-134">**Preview Mode** (Режим предварительного просмотра) — нажмите кнопку на панели инструментов, чтобы переключиться между режимами редактирования и предварительного просмотра данных.</span><span class="sxs-lookup"><span data-stu-id="20351-134">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="20351-135">**Open Sample** (Открыть пример) — нажмите эту кнопку, чтобы открыть примеры полезных данных.</span><span class="sxs-lookup"><span data-stu-id="20351-135">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="20351-136">Расширенная привязка</span><span class="sxs-lookup"><span data-stu-id="20351-136">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="20351-137">Области привязки</span><span class="sxs-lookup"><span data-stu-id="20351-137">Binding scopes</span></span>

<span data-ttu-id="20351-138">Есть несколько зарезервированных ключевых слов для доступа к разным областям привязки.</span><span class="sxs-lookup"><span data-stu-id="20351-138">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="20351-139">*Примечание.* В режиме ознакомительной версии реализованы не все варианты.</span><span class="sxs-lookup"><span data-stu-id="20351-139">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="20351-140">Назначение элементам контекста данных</span><span class="sxs-lookup"><span data-stu-id="20351-140">Assigning a data context to elements</span></span>

<span data-ttu-id="20351-141">Чтобы назначить любому элементу "контекст данных", добавьте к нужному элементу атрибут `$data`.</span><span class="sxs-lookup"><span data-stu-id="20351-141">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

```json
{
    "type": "Container",
    "$data": "{mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': {mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: {$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="20351-142">Повторяющиеся элементы в массиве</span><span class="sxs-lookup"><span data-stu-id="20351-142">Repeating items in an array</span></span>

<span data-ttu-id="20351-143">Мы и сами не в полной мере представляем себе, как это работает.</span><span class="sxs-lookup"><span data-stu-id="20351-143">This part is a bit of "dark magic".</span></span> <span data-ttu-id="20351-144">Будем рады вашим отзывам.</span><span class="sxs-lookup"><span data-stu-id="20351-144">Feedback welcome.</span></span>

* <span data-ttu-id="20351-145">Если свойство `$data` в элементе адаптивной карточки привязано к **массиву**, то такой элемент **будет повторяться для каждого элемента массива**.</span><span class="sxs-lookup"><span data-stu-id="20351-145">If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="20351-146">Любые выражения привязки (`{myProperty}`) в значениях свойств будут относиться к **отдельному элементу** в массиве.</span><span class="sxs-lookup"><span data-stu-id="20351-146">Any binding expressions (`{myProperty}`) used in property values will be scoped to the **individual item** within the array.</span></span>
* <span data-ttu-id="20351-147">Если выполнена привязка к массиву строк, для доступа к отдельному строковому элементу используйте `{$data}`.</span><span class="sxs-lookup"><span data-stu-id="20351-147">If binding to an array of strings, use `{$data}` to access the individual string element.</span></span> <span data-ttu-id="20351-148">Например, так: `"text": "{$data}"`.</span><span class="sxs-lookup"><span data-stu-id="20351-148">E.g., `"text": "{$data}"`</span></span>

<span data-ttu-id="20351-149">Например, элемент `TextBlock` в приведенном ниже примере будет повторяться три раза, так как `$data` является массивом.</span><span class="sxs-lookup"><span data-stu-id="20351-149">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="20351-150">Обратите внимание, что свойство `text` привязано к свойству `name` отдельного объекта в этом массиве.</span><span class="sxs-lookup"><span data-stu-id="20351-150">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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
            "text": "{name}"
        }
    ]
}
```

<span data-ttu-id="20351-151">**Результат:**</span><span class="sxs-lookup"><span data-stu-id="20351-151">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="20351-152">Функции</span><span class="sxs-lookup"><span data-stu-id="20351-152">Functions</span></span>

<span data-ttu-id="20351-153">Язык шаблонов нельзя считать полным без вспомогательных функций.</span><span class="sxs-lookup"><span data-stu-id="20351-153">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="20351-154">Мы предоставляем стандартный набор функций, которые работают с любым пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="20351-154">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="20351-155">Приведенный здесь синтаксис еще не считается окончательным. Рекомендуем регулярно просматривать сведения об обновлениях. Но здесь мы в общих чертах опишем наши планы.</span><span class="sxs-lookup"><span data-stu-id="20351-155">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="20351-156">Строковые функции:</span><span class="sxs-lookup"><span data-stu-id="20351-156">String functions</span></span>

* <span data-ttu-id="20351-157">substr;</span><span class="sxs-lookup"><span data-stu-id="20351-157">substr</span></span>
* <span data-ttu-id="20351-158">indexOf *(пока не работает)* ;</span><span class="sxs-lookup"><span data-stu-id="20351-158">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="20351-159">toUpper *(пока не работает)* ;</span><span class="sxs-lookup"><span data-stu-id="20351-159">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="20351-160">toLower *(пока не работает)* .</span><span class="sxs-lookup"><span data-stu-id="20351-160">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="20351-161">Численные функции:</span><span class="sxs-lookup"><span data-stu-id="20351-161">Number functions</span></span>

* <span data-ttu-id="20351-162">форматирование (валюта, десятичные числа и т. д.) *(пока не работает)* .</span><span class="sxs-lookup"><span data-stu-id="20351-162">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="20351-163">Функции даты:</span><span class="sxs-lookup"><span data-stu-id="20351-163">Date functions</span></span>

* <span data-ttu-id="20351-164">анализ хорошо известных строковых форматов даты *(пока не работает)* ;</span><span class="sxs-lookup"><span data-stu-id="20351-164">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="20351-165">анализ хорошо известных представлений даты и времени *(пока не работает)* .</span><span class="sxs-lookup"><span data-stu-id="20351-165">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="20351-166">Условные функции:</span><span class="sxs-lookup"><span data-stu-id="20351-166">Conditional functions</span></span>

* <span data-ttu-id="20351-167">if(*выражение*, *если_истина*, *если_ложь*).</span><span class="sxs-lookup"><span data-stu-id="20351-167">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="20351-168">**Пример для `if`**</span><span class="sxs-lookup"><span data-stu-id="20351-168">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="20351-169">Обработка данных</span><span class="sxs-lookup"><span data-stu-id="20351-169">Data manipulation</span></span>

* <span data-ttu-id="20351-170">JSON.parse — возможность анализа строки в формате JSON</span><span class="sxs-lookup"><span data-stu-id="20351-170">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="20351-171">**Пример для `JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="20351-171">**`JSON.parse` example**</span></span>

<span data-ttu-id="20351-172">Это ответ Azure DevOps для ситуации, когда свойство `message` содержит сериализованную строку в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="20351-172">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="20351-173">Для обращения к значениям в этой строке следует использовать в шаблоне функцию `JSON.parse`.</span><span class="sxs-lookup"><span data-stu-id="20351-173">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="20351-174">**Данные**</span><span class="sxs-lookup"><span data-stu-id="20351-174">**Data**</span></span> 

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

<span data-ttu-id="20351-175">**Использование**</span><span class="sxs-lookup"><span data-stu-id="20351-175">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="20351-176">**Результат**</span><span class="sxs-lookup"><span data-stu-id="20351-176">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="20351-177">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="20351-177">Custom functions</span></span>

<span data-ttu-id="20351-178">Мы хотим, чтобы размещающая сторона могла добавлять пользовательские функции, а значит, нам нужна надежная резервная схема на случаи, когда определенная функция не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="20351-178">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="20351-179">Мы пока еще обдумываем целесообразность этого решения.</span><span class="sxs-lookup"><span data-stu-id="20351-179">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="20351-180">Условный макет</span><span class="sxs-lookup"><span data-stu-id="20351-180">Conditional layout</span></span>

<span data-ttu-id="20351-181">Чтобы игнорировать элемент целиком при выполнении определенного условия, используйте свойство `$when`.</span><span class="sxs-lookup"><span data-stu-id="20351-181">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="20351-182">Если `$when` имеет значение `false`, такой элемент не будет отображаться для пользователя.</span><span class="sxs-lookup"><span data-stu-id="20351-182">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "{price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "{price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a><span data-ttu-id="20351-183">Компоновка шаблонов</span><span class="sxs-lookup"><span data-stu-id="20351-183">Composing templates</span></span>

<span data-ttu-id="20351-184">Сейчас не поддерживается компоновка шаблона из отдельных частей.</span><span class="sxs-lookup"><span data-stu-id="20351-184">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="20351-185">Но мы рассматриваем варианты такого механизма и скоро сообщим вам о результатах.</span><span class="sxs-lookup"><span data-stu-id="20351-185">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="20351-186">Мы будем рады любым вашим идеям!</span><span class="sxs-lookup"><span data-stu-id="20351-186">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="20351-187">Примеры</span><span class="sxs-lookup"><span data-stu-id="20351-187">Examples</span></span>

<span data-ttu-id="20351-188">Изучите обновленную [страницу примеров](https://adaptivecards.io/samples), где представлены новые виды шаблонов карточек.</span><span class="sxs-lookup"><span data-stu-id="20351-188">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
