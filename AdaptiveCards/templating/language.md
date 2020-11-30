---
title: Язык шаблонов адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: c03ed2c18039d199f37b9cbd52814f4561dad199
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001861"
---
# <a name="adaptive-cards-template-language"></a>Язык шаблонов адаптивных карточек

При работе с шаблонами можно отделить **данные** от **макета** в адаптивной карточке. Язык шаблонов — это синтаксис, используемый для создания такого шаблона. 

> Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).

> [!IMPORTANT] 
> 
> **Критические изменения** в **версии-кандидате за май 2020 г.**
>
> Мы приложили немало усилий, чтобы этот выпуск увидел свет, и уже находимся на финишной прямой. В окончательную версию нам пришлось внести небольшие критические изменения.

## <a name="breaking-changes-as-of-may-2020"></a>Критические изменения в версии за май 2020 г.

1. Синтаксис привязки изменен с `{...}` на `${...}`.
    * Например, вместо `"text": "Hello {name}"` теперь используется `"text": "Hello ${name}"`.
    
## <a name="binding-to-data"></a>Привязка к данным

Создать шаблон так же просто, как заменить нестатическое содержимое карточки на выражения привязки.

### <a name="static-card-payload"></a>Полезные данные статической карточки

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### <a name="template-payload"></a>Полезные данные шаблона

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* Выражения привязки можно размещать везде, где может находиться статическое содержимое.
* Синтаксис привязки начинается с `${` и заканчивается на `}`. Например, так: `${myProperty}`.
* Используйте *запись через точку* для доступа к вложенным объектам в иерархии объектов. Например, так: `${myParent.myChild}`.
* Правильная обработка значений NULL гарантирует отсутствие исключений при доступе к свойству NULL в графе объектов.
* Используйте *синтаксис индексатора* для получения свойств по ключу или элементам в массиве. Например, так: `${myArray[0]}`.

## <a name="providing-the-data"></a>Предоставление данных

Теперь, когда у вас есть шаблон, можно внести в него данные. Это можно сделать одним из двух способов:

1. **Вариант A — встроив данные в полезные данные шаблона**. Данные можно встроить в полезные данные шаблона `AdaptiveCard`. Для этого просто добавьте атрибут `$data` в корневой объект `AdaptiveCard`.
2. **Вариант Б — внеся данные в качестве отдельного объекта данных**. В этом случае вы предоставляете два отдельных объекта [пакету SDK для создания шаблонов](sdk.md) во время его выполнения: `template` и `data`. Такой подход более популярен, так как обычно создается шаблон, динамические данные в который добавляются позже.

### <a name="option-a-inline-data"></a>Вариант A — встроенные данные

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

### <a name="option-b-separating-the-template-from-the-data"></a>Вариант Б — Отделение шаблона от данных

Вы можете выбрать другой, более распространенный подход: создать многократно используемый шаблон адаптивной карточки, не включая в него данные. Такой шаблон можно сохранить в файле и добавить в систему управления версиями.

**Файл EmployeeCardTemplate.json**

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

Затем вы загружаете его и предоставляете данные во время выполнения с помощью [пакетов SDK для работы с шаблонами](sdk.md).

**Пример JavaScript**

Использование пакета [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).

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

## <a name="designer-support"></a>Поддержка конструктора

Конструктор адаптивных карт теперь включает поддержку шаблонов. 

> Чтобы поработать с конструктором, перейдите по адресу **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)** .

[![Образ](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Sample Data Editor** (Редактор примера данных) — введите здесь пример данных, чтобы оценить карту с привязкой к данным в режиме предварительного просмотра. На этой панели есть небольшая кнопка для заполнения структуры данных из существующего примера данных.
* **Preview Mode** (Режим предварительного просмотра) — нажмите кнопку на панели инструментов, чтобы переключиться между режимами редактирования и предварительного просмотра данных.
* **Open Sample** (Открыть пример) — нажмите эту кнопку, чтобы открыть примеры полезных данных.

## <a name="advanced-binding"></a>Расширенная привязка

### <a name="binding-scopes"></a>Области привязки

Есть несколько зарезервированных ключевых слов для доступа к разным областям привязки. 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Назначение элементам контекста данных

Чтобы назначить любому элементу "контекст данных", добавьте к нужному элементу атрибут `$data`.

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

## <a name="repeating-items-in-an-array"></a>Повторяющиеся элементы в массиве

* Если свойство `$data` в элементе адаптивной карточки привязано к **массиву**, то такой элемент **будет повторяться для каждого элемента массива**. 
* Любые выражения привязки (`${myProperty}`) в значениях свойств будут относиться к **отдельному элементу** в массиве.
* Если выполнена привязка к массиву строк, для доступа к отдельному строковому элементу используйте `${$data}`. Например, так: `"text": "${$data}"`.

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
            "text": "${name}"
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

## <a name="built-in-functions"></a>Встроенные функции

Язык шаблонов нельзя считать полноценным без разнообразных вспомогательных функций. Решение для создания шаблонов адаптивных карточек основано на [языке адаптивных выражений](https://aka.ms/adaptive-expressions) (AEL), который является открытым стандартом для объявления выражений с возможностью их оценки на разных платформах. Это — расширенный набор Logic Apps, поэтому вы можете использовать такой же синтаксис, как, например, в Power Automate.

**Мы рассмотрели лишь небольшую часть встроенных функций.**

Ознакомьтесь с полным списком [предварительно созданных функций для языка адаптивных выражений](https://docs.microsoft.com/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).

### <a name="conditional-evaluation"></a>Условная оценка:

* if(*выражение*, *если_истина*, *если_ложь*).

**Пример для `if`**

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="parsing-json"></a>Анализ JSON

* json(*jsonString*) — анализ строки JSON

**Пример для `json`**

Это ответ Azure DevOps для ситуации, когда свойство `message` содержит сериализованную строку в формате JSON. Для обращения к значениям в этой строке следует использовать в шаблоне функцию `json`.

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
    "text": "${json(message).releaseName}"
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

Пользовательские функции поддерживаются через API в [пакетах SDK для создания шаблонов](sdk.md). 

## <a name="conditional-layout-with-when"></a>Условный макет с `$when`

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

### <a name="composing-templates"></a>Компоновка шаблонов

Сейчас не поддерживается компоновка шаблона из отдельных частей. Но мы рассматриваем варианты такого механизма и скоро сообщим вам о результатах. Мы будем рады любым вашим идеям!

## <a name="examples"></a>Примеры

Изучите обновленную [страницу примеров](https://adaptivecards.io/samples), где представлены новые виды шаблонов карточек.
