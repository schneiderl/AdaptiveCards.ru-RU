---
title: Текстовые функции
author: matthidinger
ms.author: mahiding
ms.date: 06/18/2020
ms.topic: article
ms.openlocfilehash: d685007cb24e7fa8ef15b53ee5547708fba6b490
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417510"
---
# <a name="text-features"></a>Текстовые функции

[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) предоставляет некоторые дополнительные функции для форматирования и локализации текста.

## <a name="markdown-commonmark-subset"></a>Markdown (вариант CommonMark)

Встроенная функция разметки адаптивных карточек реализована за счет поддержки [CommonMark](https://commonmark.org/help/), **разновидности** синтаксиса Markdown.

> [!NOTE]
>
> [RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) не поддерживает Markdown, но предлагает широкий набор параметров конфигурации текста непосредственно в [TextRun](https://adaptivecards.io/explorer/TextRun.html).

_Поддерживается_

| Стиль текста      | Markdown |
|-----------------|-----|
| **Жирный**        | ```**Bold**``` |
| _Наклонный_        | ```_Italic_``` |
| Маркированный список     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Нумерованный список   | ```1. Green\r2. Orange\r3. Blue``` |
| Гиперссылки      | ```[Title](url)``` |

_Не поддерживается_

* Заголовки
* таблицы;
* образы,
* все, что не указано в таблице выше.

### <a name="markdown-example"></a>Пример разметки Markdown

Приведенный далее код визуализирует текст с такой разметкой:

![Снимок экрана с разметкой Markdown](media/text-features/markdown.png)

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
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Форматирование и локализация даты и времени

Иногда часовой пояс получателя карточки неизвестен, поэтому в адаптивных карточках реализованы функции форматирования `DATE()` и `TIME()` для автоматической локализации времени на целевом устройстве.

### <a name="datetime-example"></a>Пример отображения даты и времени

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

На карточке из этого примера будет отображено следующее: 

> **Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM** (Ваша посылка прибудет во вторник 14 февраля 2017 г. в 06:00).

### <a name="datetime-function-rules"></a>Правила для функций даты и времени

Существуют некоторые требования к правильной интерпретации даты и времени на разных платформах. Если эти требования не соблюдать, будет отображаться необработанная строка.

1. **Регистр учитывается** (нужно использовать только прописные буквы).
1. **Не должно быть пробелов** между `{{`, `}}` или круглыми скобками.
1. **Нужно строго соблюдать требования к форматированию стандарта [RFC 3389](https://tools.ietf.org/html/rfc3339)** (см. примеры ниже).
1. **Необходимо указать** допустимое значение даты и времени.

### <a name="valid-formats"></a>Допустимые форматы

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Параметры форматирования даты

Для отображения даты можно использовать дополнительные параметры форматирования.


|       Формат        |            Пример            |
|---------------------|-------------------------------|
| `COMPACT` (по умолчанию) |          "13.02.2017"          |
|       `SHORT`       |     "Пн 13 февраля 2017 г."     |
|       `LONG`        | "Понедельник 13 февраля 2017 г." |

