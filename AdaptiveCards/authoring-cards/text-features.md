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
# <a name="text-features"></a><span data-ttu-id="3ebd5-102">Текст функции</span><span class="sxs-lookup"><span data-stu-id="3ebd5-102">Text features</span></span>

<span data-ttu-id="3ebd5-103">`TextBlock` предоставляет некоторые дополнительные функции, для форматирования и локализации текста.</span><span class="sxs-lookup"><span data-stu-id="3ebd5-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="3ebd5-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="3ebd5-104">Markdown</span></span>
<span data-ttu-id="3ebd5-105">Для поддержки встроенных разметки, адаптивной адаптеры поддерживают **подмножества** синтаксиса Markdown.</span><span class="sxs-lookup"><span data-stu-id="3ebd5-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="3ebd5-106">_Поддерживается_</span><span class="sxs-lookup"><span data-stu-id="3ebd5-106">_Supported_</span></span>

| <span data-ttu-id="3ebd5-107">Стиль текста</span><span class="sxs-lookup"><span data-stu-id="3ebd5-107">Text Style</span></span>      | <span data-ttu-id="3ebd5-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="3ebd5-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="3ebd5-109">**Полужирный**</span><span class="sxs-lookup"><span data-stu-id="3ebd5-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="3ebd5-110">_Курсив_</span><span class="sxs-lookup"><span data-stu-id="3ebd5-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="3ebd5-111">Маркированный список</span><span class="sxs-lookup"><span data-stu-id="3ebd5-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="3ebd5-112">Нумерованный список</span><span class="sxs-lookup"><span data-stu-id="3ebd5-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="3ebd5-113">Гиперссылки</span><span class="sxs-lookup"><span data-stu-id="3ebd5-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="3ebd5-114">_не поддерживается_</span><span class="sxs-lookup"><span data-stu-id="3ebd5-114">_Not supported_</span></span>

* <span data-ttu-id="3ebd5-115">Заголовки</span><span class="sxs-lookup"><span data-stu-id="3ebd5-115">Headers</span></span>
* <span data-ttu-id="3ebd5-116">Таблицы</span><span class="sxs-lookup"><span data-stu-id="3ebd5-116">Tables</span></span>
* <span data-ttu-id="3ebd5-117">Изображений</span><span class="sxs-lookup"><span data-stu-id="3ebd5-117">Images</span></span>
* <span data-ttu-id="3ebd5-118">Ничего не в таблице выше</span><span class="sxs-lookup"><span data-stu-id="3ebd5-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="3ebd5-119">Пример разметки markdown</span><span class="sxs-lookup"><span data-stu-id="3ebd5-119">Markdown Example</span></span>

<span data-ttu-id="3ebd5-120">Ниже полезных данных будет выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="3ebd5-120">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="3ebd5-122">Форматирование даты и времени и локализации</span><span class="sxs-lookup"><span data-stu-id="3ebd5-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="3ebd5-123">Иногда вы не знаете часовой пояс для пользователя, получение карточки, поэтому предлагает адаптивной карты `DATE()` и `TIME()` форматирование функций автоматически локализации время на целевом устройстве.</span><span class="sxs-lookup"><span data-stu-id="3ebd5-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="3ebd5-124">Пример даты и времени</span><span class="sxs-lookup"><span data-stu-id="3ebd5-124">Date/Time Example</span></span>

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

<span data-ttu-id="3ebd5-125">Для отображения карты выше:</span><span class="sxs-lookup"><span data-stu-id="3ebd5-125">The above card will display:</span></span> 

> <span data-ttu-id="3ebd5-126">**Пакет прибудет на вторник, 14 февраля 2017 г. в 06:00:00**</span><span class="sxs-lookup"><span data-stu-id="3ebd5-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="3ebd5-127">Правила для функций даты и времени</span><span class="sxs-lookup"><span data-stu-id="3ebd5-127">Date/Time function rules</span></span>

<span data-ttu-id="3ebd5-128">Существуют некоторые правила, для правильной интерпретации функции даты и времени на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="3ebd5-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="3ebd5-129">Если правила не выполнены, то необработанная строка будет отображаться для пользователя, и никто не хочет.</span><span class="sxs-lookup"><span data-stu-id="3ebd5-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="3ebd5-130">**С УЧЕТОМ РЕГИСТРА** (должен быть прописными буквами)</span><span class="sxs-lookup"><span data-stu-id="3ebd5-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="3ebd5-131">**НЕ должно быть ПРОБЕЛОВ** между `{{`, `}}`, или круглые скобки</span><span class="sxs-lookup"><span data-stu-id="3ebd5-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="3ebd5-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) ФОРМАТИРОВАНИЕ** (см. Примеры ниже)</span><span class="sxs-lookup"><span data-stu-id="3ebd5-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="3ebd5-133">**ДОЛЖЕН быть** допустимое значение даты и времени</span><span class="sxs-lookup"><span data-stu-id="3ebd5-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="3ebd5-134">Допустимые форматы</span><span class="sxs-lookup"><span data-stu-id="3ebd5-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="3ebd5-135">Param форматирование дат</span><span class="sxs-lookup"><span data-stu-id="3ebd5-135">Date formatting param</span></span>

<span data-ttu-id="3ebd5-136">Для дат для форматирования выходных данных может быть указан необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="3ebd5-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="3ebd5-137">Формат</span><span class="sxs-lookup"><span data-stu-id="3ebd5-137">Format</span></span>        |            <span data-ttu-id="3ebd5-138">Пример</span><span class="sxs-lookup"><span data-stu-id="3ebd5-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="3ebd5-139">`COMPACT` (По умолчанию)</span><span class="sxs-lookup"><span data-stu-id="3ebd5-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="3ebd5-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="3ebd5-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="3ebd5-141">«ПН фев 13-й, 2017 г.»</span><span class="sxs-lookup"><span data-stu-id="3ebd5-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="3ebd5-142">«Понедельник февраля 13-й, 2017 г.»</span><span class="sxs-lookup"><span data-stu-id="3ebd5-142">"Monday, February 13th, 2017"</span></span> |

