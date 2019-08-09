---
title: Язык шаблона адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 993618ed94eaea1a004c7893a5a3927c0d818cd6
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878901"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="692f4-102">Язык шаблона адаптивных карт</span><span class="sxs-lookup"><span data-stu-id="692f4-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="692f4-103">Шаблоны позволяют отделить **данные** от **макета** на адаптивной карте.</span><span class="sxs-lookup"><span data-stu-id="692f4-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="692f4-104">Шаблон языка — это синтаксис, используемый для создания шаблона.</span><span class="sxs-lookup"><span data-stu-id="692f4-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="692f4-105">Дополнительные сведения о шаблонах [адаптивных карт](index.md) см. в этой статье.</span><span class="sxs-lookup"><span data-stu-id="692f4-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="692f4-106">Эти функции доступны **в предварительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="692f4-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="692f4-107">Ваш отзыв не только Добро пожаловать, но и важен для обеспечения того, чтобы мы доставлять нужные **вам** функции.</span><span class="sxs-lookup"><span data-stu-id="692f4-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="692f4-108">При создании шаблона можно указать данные, встроенные `AdaptiveCard` в полезные данные, или во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="692f4-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="692f4-109">Указание данных в карточке</span><span class="sxs-lookup"><span data-stu-id="692f4-109">Specify data within the card</span></span>

<span data-ttu-id="692f4-110">Чтобы предоставить данные непосредственно в полезных данных карты, просто добавьте `$data` атрибут `AdaptiveCard` в (см. ниже).</span><span class="sxs-lookup"><span data-stu-id="692f4-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="692f4-111">Привязка к данным</span><span class="sxs-lookup"><span data-stu-id="692f4-111">Binding to the data</span></span>

<span data-ttu-id="692f4-112">Можно выполнить привязку к данным `body` в или `actions` на карте.</span><span class="sxs-lookup"><span data-stu-id="692f4-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="692f4-113">Синтаксис привязки начинается с `{` и заканчивается на `}`.</span><span class="sxs-lookup"><span data-stu-id="692f4-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="692f4-114">Например,`{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="692f4-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="692f4-115">Точечная нотация для доступа к подобъектам</span><span class="sxs-lookup"><span data-stu-id="692f4-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="692f4-116">Синтаксис индексатора для получения свойств по ключу или элементам в массиве</span><span class="sxs-lookup"><span data-stu-id="692f4-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="692f4-117">Корректность обработки значений NULL для глубоких иерархий</span><span class="sxs-lookup"><span data-stu-id="692f4-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="692f4-118">*Документация по синтаксическому синтаксису скоро появится*</span><span class="sxs-lookup"><span data-stu-id="692f4-118">*Escape syntax documentation to come soon*</span></span>

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

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="692f4-119">Отделение шаблона от данных</span><span class="sxs-lookup"><span data-stu-id="692f4-119">Separating the template from the data</span></span>

<span data-ttu-id="692f4-120">Кроме того (и более вероятной) вы создадите повторно используемый шаблон "Template", не включая данные.</span><span class="sxs-lookup"><span data-stu-id="692f4-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="692f4-121">Этот шаблон можно сохранить в виде файла и добавить в систему управления версиями.</span><span class="sxs-lookup"><span data-stu-id="692f4-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="692f4-122">**Емплойикардтемплате. JSON**</span><span class="sxs-lookup"><span data-stu-id="692f4-122">**EmployeeCardTemplate.json**</span></span>

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

<span data-ttu-id="692f4-123">Затем загрузите его и предоставьте данные во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="692f4-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="692f4-124">**Пример для JavaScript**</span><span class="sxs-lookup"><span data-stu-id="692f4-124">**JavaScript example**</span></span>

<span data-ttu-id="692f4-125">Использование пакета [адаптивекардс-шаблонов](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="692f4-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

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

## <a name="designer-support"></a><span data-ttu-id="692f4-126">Поддержка конструктора</span><span class="sxs-lookup"><span data-stu-id="692f4-126">Designer Support</span></span>

<span data-ttu-id="692f4-127">Конструктор адаптивной карты был обновлен для поддержки шаблонов.</span><span class="sxs-lookup"><span data-stu-id="692f4-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="692f4-128">Ознакомьтесь с предварительной версией "vNext" по адресу: **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="692f4-128">Try out a "vnext" preview at: **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**</span></span>

<span data-ttu-id="692f4-129">[![Эскиз](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="692f4-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)</span></span>

 
<span data-ttu-id="692f4-130">Этот URL-адрес "vNext" содержит ошибки и будет развертываться часто.</span><span class="sxs-lookup"><span data-stu-id="692f4-130">This "vnext" URL is going to have bugs and will deploy frequently.</span></span> <span data-ttu-id="692f4-131">**Очистите кэш** , чтобы убедиться, что у вас последняя версия, и если вы нашли ошибки, сообщите нам!</span><span class="sxs-lookup"><span data-stu-id="692f4-131">**Clear your cache** to make sure you have the latest, and if you find bugs please let us know!</span></span>

* <span data-ttu-id="692f4-132">**Образец редактора данных** . Укажите здесь образец данных, чтобы просмотреть карту с привязкой к данным в режиме предварительного просмотра.</span><span class="sxs-lookup"><span data-stu-id="692f4-132">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="692f4-133">В этой панели есть небольшая кнопка для заполнения структуры данных от существующих демонстрационных данных.</span><span class="sxs-lookup"><span data-stu-id="692f4-133">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="692f4-134">**Структура данных** — это структура демонстрационных данных.</span><span class="sxs-lookup"><span data-stu-id="692f4-134">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="692f4-135">Поля можно перетащить в область конструктора, чтобы создать привязку к ним</span><span class="sxs-lookup"><span data-stu-id="692f4-135">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="692f4-136">**Режим предварительного просмотра** — нажмите кнопку на панели инструментов, чтобы переключиться между возможностями редактирования и образца — предварительный просмотр данных</span><span class="sxs-lookup"><span data-stu-id="692f4-136">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="692f4-137">**Открыть пример** — нажмите эту кнопку, чтобы открыть различные примеры полезных данных.</span><span class="sxs-lookup"><span data-stu-id="692f4-137">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="692f4-138">Расширенная привязка</span><span class="sxs-lookup"><span data-stu-id="692f4-138">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="692f4-139">Области привязки</span><span class="sxs-lookup"><span data-stu-id="692f4-139">Binding scopes</span></span>

<span data-ttu-id="692f4-140">Существует несколько зарезервированных ключевых слов для доступа к различным областям привязки.</span><span class="sxs-lookup"><span data-stu-id="692f4-140">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="692f4-141">*Примечание.* не все из них реализованы в предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="692f4-141">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="692f4-142">Назначение контекста данных элементам</span><span class="sxs-lookup"><span data-stu-id="692f4-142">Assigning a data context to elements</span></span>

<span data-ttu-id="692f4-143">Чтобы назначить "контекст данных" для любого элемента, добавьте `$data` атрибут к элементу.</span><span class="sxs-lookup"><span data-stu-id="692f4-143">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

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

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="692f4-144">Повторяющиеся элементы в массиве</span><span class="sxs-lookup"><span data-stu-id="692f4-144">Repeating items in an array</span></span>

<span data-ttu-id="692f4-145">Эта часть является немного «темной волшебкой».</span><span class="sxs-lookup"><span data-stu-id="692f4-145">This part is a bit of "dark magic".</span></span> <span data-ttu-id="692f4-146">Добро пожаловать на отзыв.</span><span class="sxs-lookup"><span data-stu-id="692f4-146">Feedback welcome.</span></span>

* <span data-ttu-id="692f4-147">Если `$data` свойству Objects присвоено значение **массива**, то **сам объект будет повторяться для каждого элемента в массиве.**</span><span class="sxs-lookup"><span data-stu-id="692f4-147">If the objects' `$data` property is set to an **array**, then the **object itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="692f4-148">При повторении, `$data` используемом в привязках свойств, областью действия является **отдельный элемент** в массиве.</span><span class="sxs-lookup"><span data-stu-id="692f4-148">As it is being repeated, `$data` used in property bindings are scoped to the **individual item** within the array.</span></span>

<span data-ttu-id="692f4-149">Например, `TextBlock` ниже будет повторяться три раза, так как `$data` это массив.</span><span class="sxs-lookup"><span data-stu-id="692f4-149">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="692f4-150">Обратите внимание `text` , что свойство привязано `name` к свойству отдельного объекта в массиве.</span><span class="sxs-lookup"><span data-stu-id="692f4-150">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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

<span data-ttu-id="692f4-151">**Результат:**</span><span class="sxs-lookup"><span data-stu-id="692f4-151">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="692f4-152">Функции</span><span class="sxs-lookup"><span data-stu-id="692f4-152">Functions</span></span>

<span data-ttu-id="692f4-153">Язык шаблонов не заполнен без некоторых вспомогательных функций.</span><span class="sxs-lookup"><span data-stu-id="692f4-153">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="692f4-154">Мы предложим стандартный набор функций, которые работают с каждым пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="692f4-154">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="692f4-155">Синтаксис, приведенный здесь, по-прежнему находится в воздухе, поэтому вы можете вернуться к началу работы, но вот что мы планируем:</span><span class="sxs-lookup"><span data-stu-id="692f4-155">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="692f4-156">Строковые функции</span><span class="sxs-lookup"><span data-stu-id="692f4-156">String functions</span></span>

* <span data-ttu-id="692f4-157">substr</span><span class="sxs-lookup"><span data-stu-id="692f4-157">substr</span></span>
* <span data-ttu-id="692f4-158">indexOf *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="692f4-158">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="692f4-159">toUpper *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="692f4-159">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="692f4-160">toLower *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="692f4-160">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="692f4-161">Числовые функции</span><span class="sxs-lookup"><span data-stu-id="692f4-161">Number functions</span></span>

* <span data-ttu-id="692f4-162">Форматирование (денежная, десятичная и т. д.) *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="692f4-162">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="692f4-163">Функции даты</span><span class="sxs-lookup"><span data-stu-id="692f4-163">Date functions</span></span>

* <span data-ttu-id="692f4-164">Анализ хорошо известных форматов строк даты *(еще не работает)*</span><span class="sxs-lookup"><span data-stu-id="692f4-164">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="692f4-165">Форматирование хорошо известных представлений даты и времени *(пока не работает)*</span><span class="sxs-lookup"><span data-stu-id="692f4-165">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="692f4-166">Условные функции</span><span class="sxs-lookup"><span data-stu-id="692f4-166">Conditional functions</span></span>

* <span data-ttu-id="692f4-167">If (*выражение*, *труевалуе*, *фалсевалуе*)</span><span class="sxs-lookup"><span data-stu-id="692f4-167">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="692f4-168">**`if`Например**</span><span class="sxs-lookup"><span data-stu-id="692f4-168">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "if(priceChange >= 0, 'good', 'attention')"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="692f4-169">Обработка данных</span><span class="sxs-lookup"><span data-stu-id="692f4-169">Data manipulation</span></span>

* <span data-ttu-id="692f4-170">JSON. Parse — возможность синтаксического анализа строки JSON</span><span class="sxs-lookup"><span data-stu-id="692f4-170">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="692f4-171">**`JSON.parse`Например**</span><span class="sxs-lookup"><span data-stu-id="692f4-171">**`JSON.parse` example**</span></span>

<span data-ttu-id="692f4-172">Это ответ Azure DevOps, где `message` свойство является строкой, сериализованной в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="692f4-172">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="692f4-173">Чтобы получить доступ к значениям в строке, необходимо использовать `JSON.parse` функцию в нашем шаблоне.</span><span class="sxs-lookup"><span data-stu-id="692f4-173">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="692f4-174">**Данные**</span><span class="sxs-lookup"><span data-stu-id="692f4-174">**Data**</span></span> 

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

<span data-ttu-id="692f4-175">**Загрузка**</span><span class="sxs-lookup"><span data-stu-id="692f4-175">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="692f4-176">**Результат**</span><span class="sxs-lookup"><span data-stu-id="692f4-176">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="692f4-177">Пользовательские функции</span><span class="sxs-lookup"><span data-stu-id="692f4-177">Custom functions</span></span>

<span data-ttu-id="692f4-178">Мы хотим убедиться, что узлы могут добавлять пользовательские функции. Это означает, что необходима надежная поддержка резервного использования, если функция не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="692f4-178">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="692f4-179">Мы все еще работаем над этой оценкой.</span><span class="sxs-lookup"><span data-stu-id="692f4-179">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="692f4-180">Условный макет</span><span class="sxs-lookup"><span data-stu-id="692f4-180">Conditional layout</span></span>

<span data-ttu-id="692f4-181">Чтобы удалить весь элемент при выполнении условия, используйте `$when` свойство.</span><span class="sxs-lookup"><span data-stu-id="692f4-181">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="692f4-182">Если `$when` результат вычисления `false` элемента не будет отображаться для пользователя.</span><span class="sxs-lookup"><span data-stu-id="692f4-182">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

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

### <a name="composing-templates"></a><span data-ttu-id="692f4-183">Составление шаблонов</span><span class="sxs-lookup"><span data-stu-id="692f4-183">Composing templates</span></span>

<span data-ttu-id="692f4-184">В настоящее время не поддерживается компоновка шаблона "части".</span><span class="sxs-lookup"><span data-stu-id="692f4-184">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="692f4-185">Но мы исследуем варианты и надеемся поделиться ими в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="692f4-185">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="692f4-186">Здесь вы можете ознакомиться с любыми идеями!</span><span class="sxs-lookup"><span data-stu-id="692f4-186">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="692f4-187">Примеры</span><span class="sxs-lookup"><span data-stu-id="692f4-187">Examples</span></span>

<span data-ttu-id="692f4-188">Мы создали только ограниченный объем выборок, но посмотрим здесь, чтобы приступить к работе.</span><span class="sxs-lookup"><span data-stu-id="692f4-188">We only have a limited amount of samples created so far, but take a look here to get started.</span></span>

* <span data-ttu-id="692f4-189">Загрузите образцы в [конструкторе](http://vnext.adaptivecards.io/designer) , щелкнув **открыть образец** .</span><span class="sxs-lookup"><span data-stu-id="692f4-189">Load samples within the [designer](http://vnext.adaptivecards.io/designer) by clicking **Open Sample**</span></span>
* <span data-ttu-id="692f4-190">Или просто [Просматривайте каталог](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) напрямую</span><span class="sxs-lookup"><span data-stu-id="692f4-190">Or just [browse a directory of them](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) directly</span></span>
