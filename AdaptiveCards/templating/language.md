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
# <a name="adaptive-cards-template-language"></a>Язык шаблона адаптивных карт

Шаблоны позволяют отделить **данные** от **макета** на адаптивной карте. Шаблон языка — это синтаксис, используемый для создания шаблона. 

> Дополнительные [сведения о шаблонах адаптивных карт](index.md) см. в этой статье.

> [!IMPORTANT] 
> 
> Эти функции предоставляются в **ознакомительной версии и могут быть изменены**. Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.

При создании шаблона можно указать данные, встроенные в `AdaptiveCard` полезные данные, или во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).

## <a name="specify-data-within-the-card"></a>Указание данных в карточке

Чтобы предоставить данные непосредственно в полезных данных карты, просто добавьте атрибут `$data` в `AdaptiveCard` (см. ниже).

## <a name="binding-to-the-data"></a>Привязка к данным

Можно выполнить привязку к данным в `body` или `actions` карты.

* Синтаксис привязки начинается с `{` и заканчивается `}`. Например, `{myProperty}`
* Точечная нотация для доступа к подобъектам
* Синтаксис индексатора для получения свойств по ключу или элементам в массиве
* Корректность обработки значений NULL для глубоких иерархий
* *Документация по синтаксическому синтаксису скоро появится*

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

Кроме того (и более вероятной) вы создадите повторно используемый шаблон "Template", не включая данные. Этот шаблон можно сохранить в виде файла и добавить в систему управления версиями.

**Файл EmployeeCardTemplate.json**

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

Затем загрузите его и предоставьте данные во время выполнения с помощью [пакетов SDK для шаблонов](sdk.md).

**Пример для JavaScript**

Использование пакета [адаптивекардс-шаблонов](https://npmjs.com/package/adaptivecards-templating) .

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

Конструктор адаптивной карты был обновлен для поддержки шаблонов. 

> Ознакомьтесь с предварительной версией "vNext" по адресу:  **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**

[изображение![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)

 
Этот URL-адрес "vNext" содержит ошибки и будет развертываться часто. **Очистите кэш** , чтобы убедиться, что у вас последняя версия, и если вы нашли ошибки, сообщите нам!

* **Образец редактора данных** . Укажите здесь образец данных, чтобы просмотреть карту с привязкой к данным в режиме предварительного просмотра. В этой панели есть небольшая кнопка для заполнения структуры данных от существующих демонстрационных данных.
* **Структура данных** — это структура демонстрационных данных. Поля можно перетащить в область конструктора, чтобы создать привязку к ним 
* **Режим предварительного просмотра** — нажмите кнопку на панели инструментов, чтобы переключиться между возможностями редактирования и образца — предварительный просмотр данных
* **Открыть пример** — нажмите эту кнопку, чтобы открыть различные примеры полезных данных.

## <a name="advanced-binding"></a>Расширенная привязка

### <a name="binding-scopes"></a>Области привязки

Существует несколько зарезервированных ключевых слов для доступа к различным областям привязки. 

*Примечание.* не все из них реализованы в предварительной версии.

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Назначение контекста данных элементам

Чтобы назначить "контекст данных" для любого элемента, добавьте к элементу атрибут `$data`.

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

Эта часть является немного «темной волшебкой». Добро пожаловать на отзыв.

* Если свойство `$data` объектов имеет значение **массива**, то **сам объект будет повторяться для каждого элемента в массиве.** 
* По мере повтора `$data`, используемая в привязках свойств, ограничивается **отдельным элементом** в массиве.

Например, `TextBlock` ниже будет повторяться три раза, так как `$data` является массивом. Обратите внимание, что свойство `text` привязано к свойству `name` отдельного объекта в массиве. 

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

Язык шаблонов не заполнен без некоторых вспомогательных функций. Мы предложим стандартный набор функций, которые работают с каждым пакетом SDK. 

Синтаксис, приведенный здесь, по-прежнему находится в воздухе, поэтому вы можете вернуться к началу работы, но вот что мы планируем:

### <a name="string-functions"></a>Строковые функции

* substr
* indexOf *(еще не работает)*
* toUpper *(пока не работает)*
* toLower *(еще не работает)*

### <a name="number-functions"></a>Числовые функции

* Форматирование (денежная, десятичная и т. д.) *(пока не работает)*

### <a name="date-functions"></a>Функции даты

* Анализ хорошо известных форматов строк даты *(еще не работает)*
* Форматирование хорошо известных представлений даты и времени *(пока не работает)*

### <a name="conditional-functions"></a>Условные функции

* If (*выражение*, *труевалуе*, *фалсевалуе*)

**Пример`if`**

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a>Обработка данных

* JSON. Parse — возможность синтаксического анализа строки JSON 

**Пример`JSON.parse`**

Это ответ Azure DevOps, где свойство `message` является строкой, сериализованной в формате JSON. Чтобы получить доступ к значениям в строке, необходимо использовать функцию `JSON.parse` в нашем шаблоне.

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

**Загрузка**

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

Мы хотим убедиться, что узлы могут добавлять пользовательские функции. Это означает, что необходима надежная поддержка резервного использования, если функция не поддерживается. Мы все еще работаем над этой оценкой.

## <a name="conditional-layout"></a>Условный макет

Чтобы удалить весь элемент при выполнении условия, используйте свойство `$when`. Если `$when` оценивается как `false` элемент не будет отображаться для пользователя.

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

### <a name="composing-templates"></a>Составление шаблонов

В настоящее время не поддерживается компоновка шаблона "части". Но мы исследуем варианты и надеемся поделиться ими в ближайшее время. Здесь вы можете ознакомиться с любыми идеями!


## <a name="examples"></a>Примеры.

Мы создали только ограниченный объем выборок, но посмотрим здесь, чтобы приступить к работе.

* Загрузите образцы в [конструкторе](http://vnext.adaptivecards.io/designer) , щелкнув **открыть образец** .
* Или просто [Просматривайте каталог](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) напрямую
