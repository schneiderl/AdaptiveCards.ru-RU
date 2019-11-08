---
title: Язык шаблона адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 42a1f43fbcfe1416820637af750acc960b9effde
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750401"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="b1db0-102">Язык шаблона адаптивных карт</span><span class="sxs-lookup"><span data-stu-id="b1db0-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="b1db0-103">Шаблоны позволяют отделить **данные** от **макета** на адаптивной карте.</span><span class="sxs-lookup"><span data-stu-id="b1db0-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="b1db0-104">Шаблон языка — это синтаксис, используемый для создания шаблона.</span><span class="sxs-lookup"><span data-stu-id="b1db0-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="b1db0-105">Дополнительные [сведения о шаблонах адаптивных карт](index.md) см. в этой статье.</span><span class="sxs-lookup"><span data-stu-id="b1db0-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="b1db0-106">Эти функции предоставляются в **ознакомительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="b1db0-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="b1db0-107">Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.</span><span class="sxs-lookup"><span data-stu-id="b1db0-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="b1db0-108">При создании шаблона можно указать данные, встроенные в `AdaptiveCard` полезные данные, или во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b1db0-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="b1db0-109">Указание данных в карточке</span><span class="sxs-lookup"><span data-stu-id="b1db0-109">Specify data within the card</span></span>

<span data-ttu-id="b1db0-110">Чтобы предоставить данные непосредственно в полезных данных карты, просто добавьте атрибут `$data` в `AdaptiveCard` (см. ниже).</span><span class="sxs-lookup"><span data-stu-id="b1db0-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="b1db0-111">Привязка к данным</span><span class="sxs-lookup"><span data-stu-id="b1db0-111">Binding to the data</span></span>

<span data-ttu-id="b1db0-112">Можно выполнить привязку к данным в `body` или `actions` карты.</span><span class="sxs-lookup"><span data-stu-id="b1db0-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="b1db0-113">Синтаксис привязки начинается с `{` и заканчивается `}`.</span><span class="sxs-lookup"><span data-stu-id="b1db0-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="b1db0-114">Например, `{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="b1db0-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="b1db0-115">Точечная нотация для доступа к подобъектам</span><span class="sxs-lookup"><span data-stu-id="b1db0-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="b1db0-116">Синтаксис индексатора для получения свойств по ключу или элементам в массиве</span><span class="sxs-lookup"><span data-stu-id="b1db0-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="b1db0-117">Корректность обработки значений NULL для глубоких иерархий</span><span class="sxs-lookup"><span data-stu-id="b1db0-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="b1db0-118">*Документация по синтаксическому синтаксису скоро появится*</span><span class="sxs-lookup"><span data-stu-id="b1db0-118">*Escape syntax documentation to come soon*</span></span>

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

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="b1db0-119">Отделение шаблона от данных</span><span class="sxs-lookup"><span data-stu-id="b1db0-119">Separating the template from the data</span></span>

<span data-ttu-id="b1db0-120">Кроме того (и более вероятной) вы создадите повторно используемый шаблон "Template", не включая данные.</span><span class="sxs-lookup"><span data-stu-id="b1db0-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="b1db0-121">Этот шаблон можно сохранить в виде файла и добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="b1db0-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="b1db0-122">**Файл EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="b1db0-122">**EmployeeCardTemplate.json**</span></span>

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

<span data-ttu-id="b1db0-123">Затем загрузите его и предоставьте данные во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b1db0-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="b1db0-124">**Пример для JavaScript**</span><span class="sxs-lookup"><span data-stu-id="b1db0-124">**JavaScript example**</span></span>

<span data-ttu-id="b1db0-125">Использование пакета [адаптивекардс-шаблонов](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="b1db0-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

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

## <a name="designer-support"></a><span data-ttu-id="b1db0-126">Поддержка конструктора</span><span class="sxs-lookup"><span data-stu-id="b1db0-126">Designer Support</span></span>

<span data-ttu-id="b1db0-127">Конструктор адаптивной карты был обновлен для поддержки шаблонов.</span><span class="sxs-lookup"><span data-stu-id="b1db0-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="b1db0-128">Попробуйте:  **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="b1db0-128">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="b1db0-129">[изображение ![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="b1db0-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="b1db0-130">**Образец редактора данных** . Укажите здесь образец данных, чтобы просмотреть карту с привязкой к данным в режиме предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="b1db0-130">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="b1db0-131">В этой панели есть небольшая кнопка для заполнения структуры данных от существующих демонстрационных данных.</span><span class="sxs-lookup"><span data-stu-id="b1db0-131">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="b1db0-132">**Структура данных** — это структура демонстрационных данных.</span><span class="sxs-lookup"><span data-stu-id="b1db0-132">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="b1db0-133">Поля можно перетащить в область конструктора, чтобы создать привязку к ним</span><span class="sxs-lookup"><span data-stu-id="b1db0-133">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="b1db0-134">**Режим предварительного просмотра** — нажмите кнопку на панели инструментов, чтобы переключиться между возможностями редактирования и образца — предварительный просмотр данных</span><span class="sxs-lookup"><span data-stu-id="b1db0-134">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="b1db0-135">**Открыть пример** — нажмите эту кнопку, чтобы открыть различные примеры полезных данных.</span><span class="sxs-lookup"><span data-stu-id="b1db0-135">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="b1db0-136">Расширенная привязка</span><span class="sxs-lookup"><span data-stu-id="b1db0-136">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="b1db0-137">Области привязки</span><span class="sxs-lookup"><span data-stu-id="b1db0-137">Binding scopes</span></span>

<span data-ttu-id="b1db0-138">Существует несколько зарезервированных ключевых слов для доступа к различным областям привязки.</span><span class="sxs-lookup"><span data-stu-id="b1db0-138">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="b1db0-139">*Примечание.* не все из них реализованы в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="b1db0-139">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="b1db0-140">Назначение контекста данных элементам</span><span class="sxs-lookup"><span data-stu-id="b1db0-140">Assigning a data context to elements</span></span>

<span data-ttu-id="b1db0-141">Чтобы назначить "контекст данных" для любого элемента, добавьте к элементу атрибут `$data`.</span><span class="sxs-lookup"><span data-stu-id="b1db0-141">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

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

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="b1db0-142">Повторяющиеся элементы в массиве</span><span class="sxs-lookup"><span data-stu-id="b1db0-142">Repeating items in an array</span></span>

<span data-ttu-id="b1db0-143">Эта часть является немного «темной волшебкой».</span><span class="sxs-lookup"><span data-stu-id="b1db0-143">This part is a bit of "dark magic".</span></span> <span data-ttu-id="b1db0-144">Добро пожаловать на отзыв.</span><span class="sxs-lookup"><span data-stu-id="b1db0-144">Feedback welcome.</span></span>

* <span data-ttu-id="b1db0-145">Если свойство `$data` объектов имеет значение **массива**, то **сам объект будет повторяться для каждого элемента в массиве.**</span><span class="sxs-lookup"><span data-stu-id="b1db0-145">If the objects' `$data` property is set to an **array**, then the **object itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="b1db0-146">По мере повтора `$data`, используемая в привязках свойств, ограничивается **отдельным элементом** в массиве.</span><span class="sxs-lookup"><span data-stu-id="b1db0-146">As it is being repeated, `$data` used in property bindings are scoped to the **individual item** within the array.</span></span>

<span data-ttu-id="b1db0-147">Например, `TextBlock` ниже будет повторяться три раза, так как `$data` является массивом.</span><span class="sxs-lookup"><span data-stu-id="b1db0-147">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="b1db0-148">Обратите внимание, что свойство `text` привязано к свойству `name` отдельного объекта в массиве.</span><span class="sxs-lookup"><span data-stu-id="b1db0-148">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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

<span data-ttu-id="b1db0-149">**Результат:**</span><span class="sxs-lookup"><span data-stu-id="b1db0-149">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="b1db0-150">Функции</span><span class="sxs-lookup"><span data-stu-id="b1db0-150">Functions</span></span>

<span data-ttu-id="b1db0-151">Язык шаблонов не заполнен без некоторых вспомогательных функций.</span><span class="sxs-lookup"><span data-stu-id="b1db0-151">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="b1db0-152">Мы предложим стандартный набор функций, которые работают с каждым пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="b1db0-152">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="b1db0-153">Синтаксис, приведенный здесь, по-прежнему находится в воздухе, поэтому вы можете вернуться к началу работы, но вот что мы планируем:</span><span class="sxs-lookup"><span data-stu-id="b1db0-153">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="b1db0-154">Строковые функции</span><span class="sxs-lookup"><span data-stu-id="b1db0-154">String functions</span></span>

* <span data-ttu-id="b1db0-155">substr</span><span class="sxs-lookup"><span data-stu-id="b1db0-155">substr</span></span>
* <span data-ttu-id="b1db0-156">indexOf *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="b1db0-156">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="b1db0-157">toUpper *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="b1db0-157">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="b1db0-158">toLower *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="b1db0-158">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="b1db0-159">Числовые функции</span><span class="sxs-lookup"><span data-stu-id="b1db0-159">Number functions</span></span>

* <span data-ttu-id="b1db0-160">Форматирование (денежная, десятичная и т. д.) *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="b1db0-160">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="b1db0-161">Функции даты</span><span class="sxs-lookup"><span data-stu-id="b1db0-161">Date functions</span></span>

* <span data-ttu-id="b1db0-162">Анализ хорошо известных форматов строк даты *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="b1db0-162">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="b1db0-163">Форматирование хорошо известных представлений даты и времени *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="b1db0-163">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="b1db0-164">Условные функции</span><span class="sxs-lookup"><span data-stu-id="b1db0-164">Conditional functions</span></span>

* <span data-ttu-id="b1db0-165">If (*выражение*, *труевалуе*, *фалсевалуе*)</span><span class="sxs-lookup"><span data-stu-id="b1db0-165">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="b1db0-166">**Пример`if`**</span><span class="sxs-lookup"><span data-stu-id="b1db0-166">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="b1db0-167">Обработка данных</span><span class="sxs-lookup"><span data-stu-id="b1db0-167">Data manipulation</span></span>

* <span data-ttu-id="b1db0-168">JSON. Parse — возможность синтаксического анализа строки JSON</span><span class="sxs-lookup"><span data-stu-id="b1db0-168">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="b1db0-169">**Пример`JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="b1db0-169">**`JSON.parse` example**</span></span>

<span data-ttu-id="b1db0-170">Это ответ Azure DevOps, где свойство `message` является строкой, сериализованной в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="b1db0-170">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="b1db0-171">Чтобы получить доступ к значениям в строке, необходимо использовать функцию `JSON.parse` в нашем шаблоне.</span><span class="sxs-lookup"><span data-stu-id="b1db0-171">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="b1db0-172">**Данные**</span><span class="sxs-lookup"><span data-stu-id="b1db0-172">**Data**</span></span> 

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

<span data-ttu-id="b1db0-173">**Загрузка**</span><span class="sxs-lookup"><span data-stu-id="b1db0-173">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="b1db0-174">**Результат**</span><span class="sxs-lookup"><span data-stu-id="b1db0-174">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="b1db0-175">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="b1db0-175">Custom functions</span></span>

<span data-ttu-id="b1db0-176">Мы хотим убедиться, что узлы могут добавлять пользовательские функции. Это означает, что необходима надежная поддержка резервного использования, если функция не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="b1db0-176">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="b1db0-177">Мы все еще работаем над этой оценкой.</span><span class="sxs-lookup"><span data-stu-id="b1db0-177">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="b1db0-178">Условный макет</span><span class="sxs-lookup"><span data-stu-id="b1db0-178">Conditional layout</span></span>

<span data-ttu-id="b1db0-179">Чтобы удалить весь элемент при выполнении условия, используйте свойство `$when`.</span><span class="sxs-lookup"><span data-stu-id="b1db0-179">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="b1db0-180">Если `$when` оценивается как `false` элемент не будет отображаться для пользователя.</span><span class="sxs-lookup"><span data-stu-id="b1db0-180">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

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

### <a name="composing-templates"></a><span data-ttu-id="b1db0-181">Составление шаблонов</span><span class="sxs-lookup"><span data-stu-id="b1db0-181">Composing templates</span></span>

<span data-ttu-id="b1db0-182">В настоящее время не поддерживается компоновка шаблона "части".</span><span class="sxs-lookup"><span data-stu-id="b1db0-182">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="b1db0-183">Но мы исследуем варианты и надеемся поделиться ими в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="b1db0-183">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="b1db0-184">Здесь вы можете ознакомиться с любыми идеями!</span><span class="sxs-lookup"><span data-stu-id="b1db0-184">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="b1db0-185">Примеры.</span><span class="sxs-lookup"><span data-stu-id="b1db0-185">Examples</span></span>

<span data-ttu-id="b1db0-186">Перейдите на страницу обновленных [примеров](https://adaptivecards.io/samples) , чтобы просмотреть все виды новых шаблонов карточек.</span><span class="sxs-lookup"><span data-stu-id="b1db0-186">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
