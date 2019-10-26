---
title: Язык шаблона адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: b99a2905fb000653b7ee75204221b832a2b5a907
ms.sourcegitcommit: ce044dc969d9b9c47a52bd361bfe2b746071913b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917126"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="ac3fe-102">Язык шаблона адаптивных карт</span><span class="sxs-lookup"><span data-stu-id="ac3fe-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="ac3fe-103">Шаблоны позволяют отделить **данные** от **макета** на адаптивной карте.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="ac3fe-104">Шаблон языка — это синтаксис, используемый для создания шаблона.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="ac3fe-105">Дополнительные [сведения о шаблонах адаптивных карт](index.md) см. в этой статье.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="ac3fe-106">Эти функции предоставляются в **ознакомительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="ac3fe-107">Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="ac3fe-108">При создании шаблона можно указать данные, встроенные в `AdaptiveCard` полезные данные, или во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="ac3fe-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="ac3fe-109">Указание данных в карточке</span><span class="sxs-lookup"><span data-stu-id="ac3fe-109">Specify data within the card</span></span>

<span data-ttu-id="ac3fe-110">Чтобы предоставить данные непосредственно в полезных данных карты, просто добавьте атрибут `$data` в `AdaptiveCard` (см. ниже).</span><span class="sxs-lookup"><span data-stu-id="ac3fe-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="ac3fe-111">Привязка к данным</span><span class="sxs-lookup"><span data-stu-id="ac3fe-111">Binding to the data</span></span>

<span data-ttu-id="ac3fe-112">Можно выполнить привязку к данным в `body` или `actions` карты.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="ac3fe-113">Синтаксис привязки начинается с `{` и заканчивается `}`.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="ac3fe-114">Например, `{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="ac3fe-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="ac3fe-115">Точечная нотация для доступа к подобъектам</span><span class="sxs-lookup"><span data-stu-id="ac3fe-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="ac3fe-116">Синтаксис индексатора для получения свойств по ключу или элементам в массиве</span><span class="sxs-lookup"><span data-stu-id="ac3fe-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="ac3fe-117">Корректность обработки значений NULL для глубоких иерархий</span><span class="sxs-lookup"><span data-stu-id="ac3fe-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="ac3fe-118">*Документация по синтаксическому синтаксису скоро появится*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-118">*Escape syntax documentation to come soon*</span></span>

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

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="ac3fe-119">Отделение шаблона от данных</span><span class="sxs-lookup"><span data-stu-id="ac3fe-119">Separating the template from the data</span></span>

<span data-ttu-id="ac3fe-120">Кроме того (и более вероятной) вы создадите повторно используемый шаблон "Template", не включая данные.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="ac3fe-121">Этот шаблон можно сохранить в виде файла и добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="ac3fe-122">**Файл EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-122">**EmployeeCardTemplate.json**</span></span>

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

<span data-ttu-id="ac3fe-123">Затем загрузите его и предоставьте данные во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="ac3fe-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="ac3fe-124">**Пример для JavaScript**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-124">**JavaScript example**</span></span>

<span data-ttu-id="ac3fe-125">Использование пакета [адаптивекардс-шаблонов](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="ac3fe-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

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

## <a name="designer-support"></a><span data-ttu-id="ac3fe-126">Поддержка конструктора</span><span class="sxs-lookup"><span data-stu-id="ac3fe-126">Designer Support</span></span>

<span data-ttu-id="ac3fe-127">Конструктор адаптивной карты был обновлен для поддержки шаблонов.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="ac3fe-128">Ознакомьтесь с предварительной версией "vNext" по адресу:  **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-128">Try out a "vnext" preview at: **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**</span></span>

<span data-ttu-id="ac3fe-129">[изображение![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="ac3fe-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)</span></span>

 
<span data-ttu-id="ac3fe-130">Этот URL-адрес "vNext" содержит ошибки и будет развертываться часто.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-130">This "vnext" URL is going to have bugs and will deploy frequently.</span></span> <span data-ttu-id="ac3fe-131">**Очистите кэш** , чтобы убедиться, что у вас последняя версия, и если вы нашли ошибки, сообщите нам!</span><span class="sxs-lookup"><span data-stu-id="ac3fe-131">**Clear your cache** to make sure you have the latest, and if you find bugs please let us know!</span></span>

* <span data-ttu-id="ac3fe-132">**Образец редактора данных** . Укажите здесь образец данных, чтобы просмотреть карту с привязкой к данным в режиме предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-132">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="ac3fe-133">В этой панели есть небольшая кнопка для заполнения структуры данных от существующих демонстрационных данных.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-133">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="ac3fe-134">**Структура данных** — это структура демонстрационных данных.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-134">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="ac3fe-135">Поля можно перетащить в область конструктора, чтобы создать привязку к ним</span><span class="sxs-lookup"><span data-stu-id="ac3fe-135">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="ac3fe-136">**Режим предварительного просмотра** — нажмите кнопку на панели инструментов, чтобы переключиться между возможностями редактирования и образца — предварительный просмотр данных</span><span class="sxs-lookup"><span data-stu-id="ac3fe-136">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="ac3fe-137">**Открыть пример** — нажмите эту кнопку, чтобы открыть различные примеры полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-137">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="ac3fe-138">Расширенная привязка</span><span class="sxs-lookup"><span data-stu-id="ac3fe-138">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="ac3fe-139">Области привязки</span><span class="sxs-lookup"><span data-stu-id="ac3fe-139">Binding scopes</span></span>

<span data-ttu-id="ac3fe-140">Существует несколько зарезервированных ключевых слов для доступа к различным областям привязки.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-140">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="ac3fe-141">*Примечание.* не все из них реализованы в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-141">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="ac3fe-142">Назначение контекста данных элементам</span><span class="sxs-lookup"><span data-stu-id="ac3fe-142">Assigning a data context to elements</span></span>

<span data-ttu-id="ac3fe-143">Чтобы назначить "контекст данных" для любого элемента, добавьте к элементу атрибут `$data`.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-143">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

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

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="ac3fe-144">Повторяющиеся элементы в массиве</span><span class="sxs-lookup"><span data-stu-id="ac3fe-144">Repeating items in an array</span></span>

<span data-ttu-id="ac3fe-145">Эта часть является немного «темной волшебкой».</span><span class="sxs-lookup"><span data-stu-id="ac3fe-145">This part is a bit of "dark magic".</span></span> <span data-ttu-id="ac3fe-146">Добро пожаловать на отзыв.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-146">Feedback welcome.</span></span>

* <span data-ttu-id="ac3fe-147">Если свойство `$data` объектов имеет значение **массива**, то **сам объект будет повторяться для каждого элемента в массиве.**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-147">If the objects' `$data` property is set to an **array**, then the **object itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="ac3fe-148">По мере повтора `$data`, используемая в привязках свойств, ограничивается **отдельным элементом** в массиве.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-148">As it is being repeated, `$data` used in property bindings are scoped to the **individual item** within the array.</span></span>

<span data-ttu-id="ac3fe-149">Например, `TextBlock` ниже будет повторяться три раза, так как `$data` является массивом.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-149">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="ac3fe-150">Обратите внимание, что свойство `text` привязано к свойству `name` отдельного объекта в массиве.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-150">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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

<span data-ttu-id="ac3fe-151">**Результат:**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-151">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="ac3fe-152">Функции</span><span class="sxs-lookup"><span data-stu-id="ac3fe-152">Functions</span></span>

<span data-ttu-id="ac3fe-153">Язык шаблонов не заполнен без некоторых вспомогательных функций.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-153">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="ac3fe-154">Мы предложим стандартный набор функций, которые работают с каждым пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-154">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="ac3fe-155">Синтаксис, приведенный здесь, по-прежнему находится в воздухе, поэтому вы можете вернуться к началу работы, но вот что мы планируем:</span><span class="sxs-lookup"><span data-stu-id="ac3fe-155">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="ac3fe-156">Строковые функции</span><span class="sxs-lookup"><span data-stu-id="ac3fe-156">String functions</span></span>

* <span data-ttu-id="ac3fe-157">substr</span><span class="sxs-lookup"><span data-stu-id="ac3fe-157">substr</span></span>
* <span data-ttu-id="ac3fe-158">indexOf *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-158">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="ac3fe-159">toUpper *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-159">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="ac3fe-160">toLower *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-160">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="ac3fe-161">Числовые функции</span><span class="sxs-lookup"><span data-stu-id="ac3fe-161">Number functions</span></span>

* <span data-ttu-id="ac3fe-162">Форматирование (денежная, десятичная и т. д.) *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-162">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="ac3fe-163">Функции даты</span><span class="sxs-lookup"><span data-stu-id="ac3fe-163">Date functions</span></span>

* <span data-ttu-id="ac3fe-164">Анализ хорошо известных форматов строк даты *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-164">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="ac3fe-165">Форматирование хорошо известных представлений даты и времени *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="ac3fe-165">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="ac3fe-166">Условные функции</span><span class="sxs-lookup"><span data-stu-id="ac3fe-166">Conditional functions</span></span>

* <span data-ttu-id="ac3fe-167">If (*выражение*, *труевалуе*, *фалсевалуе*)</span><span class="sxs-lookup"><span data-stu-id="ac3fe-167">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="ac3fe-168">**Пример`if`**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-168">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="ac3fe-169">Обработка данных</span><span class="sxs-lookup"><span data-stu-id="ac3fe-169">Data manipulation</span></span>

* <span data-ttu-id="ac3fe-170">JSON. Parse — возможность синтаксического анализа строки JSON</span><span class="sxs-lookup"><span data-stu-id="ac3fe-170">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="ac3fe-171">**Пример`JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-171">**`JSON.parse` example**</span></span>

<span data-ttu-id="ac3fe-172">Это ответ Azure DevOps, где свойство `message` является строкой, сериализованной в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-172">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="ac3fe-173">Чтобы получить доступ к значениям в строке, необходимо использовать функцию `JSON.parse` в нашем шаблоне.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-173">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="ac3fe-174">**Данные**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-174">**Data**</span></span> 

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

<span data-ttu-id="ac3fe-175">**Загрузка**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-175">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="ac3fe-176">**Результат**</span><span class="sxs-lookup"><span data-stu-id="ac3fe-176">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="ac3fe-177">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="ac3fe-177">Custom functions</span></span>

<span data-ttu-id="ac3fe-178">Мы хотим убедиться, что узлы могут добавлять пользовательские функции. Это означает, что необходима надежная поддержка резервного использования, если функция не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-178">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="ac3fe-179">Мы все еще работаем над этой оценкой.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-179">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="ac3fe-180">Условный макет</span><span class="sxs-lookup"><span data-stu-id="ac3fe-180">Conditional layout</span></span>

<span data-ttu-id="ac3fe-181">Чтобы удалить весь элемент при выполнении условия, используйте свойство `$when`.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-181">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="ac3fe-182">Если `$when` оценивается как `false` элемент не будет отображаться для пользователя.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-182">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

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

### <a name="composing-templates"></a><span data-ttu-id="ac3fe-183">Составление шаблонов</span><span class="sxs-lookup"><span data-stu-id="ac3fe-183">Composing templates</span></span>

<span data-ttu-id="ac3fe-184">В настоящее время не поддерживается компоновка шаблона "части".</span><span class="sxs-lookup"><span data-stu-id="ac3fe-184">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="ac3fe-185">Но мы исследуем варианты и надеемся поделиться ими в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-185">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="ac3fe-186">Здесь вы можете ознакомиться с любыми идеями!</span><span class="sxs-lookup"><span data-stu-id="ac3fe-186">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="ac3fe-187">Примеры.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-187">Examples</span></span>

<span data-ttu-id="ac3fe-188">Мы создали только ограниченный объем выборок, но посмотрим здесь, чтобы приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="ac3fe-188">We only have a limited amount of samples created so far, but take a look here to get started.</span></span>

* <span data-ttu-id="ac3fe-189">Загрузите образцы в [конструкторе](http://vnext.adaptivecards.io/designer) , щелкнув **открыть образец** .</span><span class="sxs-lookup"><span data-stu-id="ac3fe-189">Load samples within the [designer](http://vnext.adaptivecards.io/designer) by clicking **Open Sample**</span></span>
* <span data-ttu-id="ac3fe-190">Или просто [Просматривайте каталог](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) напрямую</span><span class="sxs-lookup"><span data-stu-id="ac3fe-190">Or just [browse a directory of them](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) directly</span></span>
