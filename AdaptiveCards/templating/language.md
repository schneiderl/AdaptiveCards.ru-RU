---
title: Язык шаблонов адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: ffd2ec065550f483bf602483eebf622565f7f47a
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "82136180"
---
# <a name="adaptive-cards-template-language"></a>Язык шаблонов адаптивных карточек

При работе с шаблонами можно отделить **данные** от **макета** в адаптивной карточке. Язык шаблонов — это синтаксис, используемый для создания такого шаблона. 

> Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).

> [!IMPORTANT] 
> 
> Эти функции предоставляются в **ознакомительной версии и могут быть изменены**. Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.

При создании шаблона вы можете включить в него данные с помощью встроенной структуры `AdaptiveCard` или во время выполнения с помощью [пакетов SDK для работы с шаблонами](sdk.md).

## <a name="specify-data-within-the-card"></a>Включение данных в карточку

Чтобы добавить полезные данные непосредственно в адаптивную карточку, добавьте атрибут `$data` в `AdaptiveCard`, как показано ниже.

## <a name="binding-to-the-data"></a>Привязка к данным

Можно выполнить привязку к данным в `body` или `actions` карточки.

* Синтаксис привязки начинается с `{` и заканчивается `}`. Например, так: `{myProperty}`.
* Запись через точку для доступа к вложенным объектам
* Синтаксис индексатора для получения свойств по ключу или элементов массива
* Корректная обработка значений NULL для глубоких иерархий
* *Скоро появится документация по синтаксису экранирования*

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

## <a name="separating-the-template-from-the-data"></a>Отделение шаблона от данных

Вы можете выбрать другой, более распространенный подход: создать многократно используемый "шаблон" адаптивной карточки, не включая в него данные. Такой шаблон можно сохранить в файле и добавить в систему управления версиями.

**Файл EmployeeCardTemplate.json**

```json
{
    "type": "AdaptiveCard",
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

Затем вы загружаете его и предоставляете данные во время выполнения с помощью [пакетов SDK для работы с шаблонами](sdk.md).

**Пример JavaScript**

Использование пакета [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).

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

## <a name="designer-support"></a>Поддержка конструктора

Конструктор адаптивных карт теперь включает поддержку шаблонов. 

> Чтобы поработать с конструктором, перейдите по адресу **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .

[![Образ](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Sample Data Editor** (Редактор примера данных) — введите здесь пример данных, чтобы оценить карту с привязкой к данным в режиме предварительного просмотра. На этой панели есть небольшая кнопка для заполнения структуры данных из существующего примера данных.
* **Data Structure** (Структура данных) — структура, которая определяет архитектуру примера данных. Поля можно перетащить в область конструктора, чтобы создать привязку к ним. 
* **Preview Mode** (Режим предварительного просмотра) — нажмите кнопку на панели инструментов, чтобы переключиться между режимами редактирования и предварительного просмотра данных.
* **Open Sample** (Открыть пример) — нажмите эту кнопку, чтобы открыть примеры полезных данных.

## <a name="advanced-binding"></a>Расширенная привязка

### <a name="binding-scopes"></a>Области привязки

Есть несколько зарезервированных ключевых слов для доступа к разным областям привязки. 

*Примечание.* В режиме ознакомительной версии реализованы не все варианты.

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Назначение элементам контекста данных

Чтобы назначить любому элементу "контекст данных", добавьте к нужному элементу атрибут `$data`.

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

## <a name="repeating-items-in-an-array"></a>Повторяющиеся элементы в массиве

Мы и сами не в полной мере представляем себе, как это работает. Будем рады вашим отзывам.

* Если свойство `$data` в элементе адаптивной карточки привязано к **массиву**, то такой элемент **будет повторяться для каждого элемента массива**. 
* Любые выражения привязки (`{myProperty}`) в значениях свойств будут относиться к **отдельному элементу** в массиве.
* Если выполнена привязка к массиву строк, для доступа к отдельному строковому элементу используйте `{$data}`. Например, так: `"text": "{$data}"`.

Например, элемент `TextBlock` в приведенном ниже примере будет повторяться три раза, так как `$data` является массивом. Обратите внимание, что свойство `text` привязано к свойству `name` отдельного объекта в этом массиве. 

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

**Результат:**

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

## <a name="functions"></a>Функции

Язык шаблонов нельзя считать полным без вспомогательных функций. Мы предоставляем стандартный набор функций, которые работают с любым пакетом SDK. 

Приведенный здесь синтаксис еще не считается окончательным. Рекомендуем регулярно просматривать сведения об обновлениях. Но здесь мы в общих чертах опишем наши планы.

### <a name="string-functions"></a>Строковые функции:

* substr;
* indexOf *(пока не работает)* ;
* toUpper *(пока не работает)* ;
* toLower *(пока не работает)* .

### <a name="number-functions"></a>Численные функции:

* форматирование (валюта, десятичные числа и т. д.) *(пока не работает)* .

### <a name="date-functions"></a>Функции даты:

* анализ хорошо известных строковых форматов даты *(пока не работает)* ;
* анализ хорошо известных представлений даты и времени *(пока не работает)* .

### <a name="conditional-functions"></a>Условные функции:

* if(*выражение*, *если_истина*, *если_ложь*).

**Пример для `if`**

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a>Обработка данных

* JSON.parse — возможность анализа строки в формате JSON 

**Пример для `JSON.parse`**

Это ответ Azure DevOps для ситуации, когда свойство `message` содержит сериализованную строку в формате JSON. Для обращения к значениям в этой строке следует использовать в шаблоне функцию `JSON.parse`.

**Данные** 

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

**Использование**

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

**Результат**

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a>Пользовательские функции

Мы хотим, чтобы размещающая сторона могла добавлять пользовательские функции, а значит, нам нужна надежная резервная схема на случаи, когда определенная функция не поддерживается. Мы пока еще обдумываем целесообразность этого решения.

## <a name="conditional-layout"></a>Условный макет

Чтобы игнорировать элемент целиком при выполнении определенного условия, используйте свойство `$when`. Если `$when` имеет значение `false`, такой элемент не будет отображаться для пользователя.

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

### <a name="composing-templates"></a>Компоновка шаблонов

Сейчас не поддерживается компоновка шаблона из отдельных частей. Но мы рассматриваем варианты такого механизма и скоро сообщим вам о результатах. Мы будем рады любым вашим идеям!


## <a name="examples"></a>Примеры

Изучите обновленную [страницу примеров](https://adaptivecards.io/samples), где представлены новые виды шаблонов карточек.
