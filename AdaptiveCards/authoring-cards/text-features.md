---
title: Текст функции
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: ac8ec0c48e06377ebd17f1b31abe463c48809fe3
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553616"
---
# <a name="text-features"></a>Текст функции

`TextBlock` предоставляет некоторые дополнительные функции, для форматирования и локализации текста.

## <a name="markdown"></a>Markdown
Для поддержки встроенных разметки, адаптивной адаптеры поддерживают **подмножества** синтаксиса Markdown.

_Поддерживается_

| Стиль текста      | Markdown |
|-----------------|-----|
| **Полужирный**        | ```**Bold**``` |
| _Курсив_        | ```_Italic_``` |
| Маркированный список     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Нумерованный список   | ```1. Green\r2. Orange\r3. Blue``` |
| Гиперссылки      | ```[Title](url)``` |

_не поддерживается_

* Заголовки
* Таблицы
* Изображений
* Ничего не в таблице выше

### <a name="markdown-example"></a>Пример разметки markdown

Ниже полезных данных будет выглядеть примерно так:

![Снимок экрана markdown](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Форматирование даты и времени и локализации

Иногда вы не знаете часовой пояс для пользователя, получение карточки, поэтому предлагает адаптивной карты `DATE()` и `TIME()` форматирование функций автоматически локализации время на целевом устройстве.

### <a name="datetime-example"></a>Пример даты и времени

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

Для отображения карты выше: 

> **Пакет прибудет на вторник, 14 февраля 2017 г. в 06:00:00**

### <a name="datetime-function-rules"></a>Правила для функций даты и времени

Существуют некоторые правила, для правильной интерпретации функции даты и времени на всех платформах. Если правила не выполнены, то необработанная строка будет отображаться для пользователя, и никто не хочет.

1. **С УЧЕТОМ РЕГИСТРА** (должен быть прописными буквами)
1. **НЕ должно быть ПРОБЕЛОВ** между `{{`, `}}`, или круглые скобки
1. **STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) ФОРМАТИРОВАНИЕ** (см. Примеры ниже)
1. **ДОЛЖЕН быть** допустимое значение даты и времени

### <a name="valid-formats"></a>Допустимые форматы

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Param форматирование дат

Для дат для форматирования выходных данных может быть указан необязательный параметр.


|       Формат        |            Пример            |
|---------------------|-------------------------------|
| `COMPACT` (По умолчанию) |          "2/13/2017"          |
|       `SHORT`       |     «ПН фев 13-й, 2017 г.»     |
|       `LONG`        | «Понедельник февраля 13-й, 2017 г.» |

