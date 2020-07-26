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
# <a name="text-features"></a><span data-ttu-id="37777-102">Текстовые функции</span><span class="sxs-lookup"><span data-stu-id="37777-102">Text features</span></span>

<span data-ttu-id="37777-103">[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) предоставляет некоторые дополнительные функции для форматирования и локализации текста.</span><span class="sxs-lookup"><span data-stu-id="37777-103">[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) offers advanced features for formatting and localizing the text.</span></span>

## <a name="markdown-commonmark-subset"></a><span data-ttu-id="37777-104">Markdown (вариант CommonMark)</span><span class="sxs-lookup"><span data-stu-id="37777-104">Markdown (Commonmark subset)</span></span>

<span data-ttu-id="37777-105">Встроенная функция разметки адаптивных карточек реализована за счет поддержки [CommonMark](https://commonmark.org/help/), **разновидности** синтаксиса Markdown.</span><span class="sxs-lookup"><span data-stu-id="37777-105">To support inline markup, Adaptive Cards support a **subset** of the [Commonmark](https://commonmark.org/help/) Markdown syntax.</span></span>

> [!NOTE]
>
> <span data-ttu-id="37777-106">[RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) не поддерживает Markdown, но предлагает широкий набор параметров конфигурации текста непосредственно в [TextRun](https://adaptivecards.io/explorer/TextRun.html).</span><span class="sxs-lookup"><span data-stu-id="37777-106">[RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) does not support markdown, but offers a wide array of text configuration options directly within the the [TextRun](https://adaptivecards.io/explorer/TextRun.html)</span></span>

<span data-ttu-id="37777-107">_Поддерживается_</span><span class="sxs-lookup"><span data-stu-id="37777-107">_Supported_</span></span>

| <span data-ttu-id="37777-108">Стиль текста</span><span class="sxs-lookup"><span data-stu-id="37777-108">Text Style</span></span>      | <span data-ttu-id="37777-109">Markdown</span><span class="sxs-lookup"><span data-stu-id="37777-109">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="37777-110">**Жирный**</span><span class="sxs-lookup"><span data-stu-id="37777-110">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="37777-111">_Наклонный_</span><span class="sxs-lookup"><span data-stu-id="37777-111">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="37777-112">Маркированный список</span><span class="sxs-lookup"><span data-stu-id="37777-112">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="37777-113">Нумерованный список</span><span class="sxs-lookup"><span data-stu-id="37777-113">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="37777-114">Гиперссылки</span><span class="sxs-lookup"><span data-stu-id="37777-114">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="37777-115">_Не поддерживается_</span><span class="sxs-lookup"><span data-stu-id="37777-115">_Not supported_</span></span>

* <span data-ttu-id="37777-116">Заголовки</span><span class="sxs-lookup"><span data-stu-id="37777-116">Headers</span></span>
* <span data-ttu-id="37777-117">таблицы;</span><span class="sxs-lookup"><span data-stu-id="37777-117">Tables</span></span>
* <span data-ttu-id="37777-118">образы,</span><span class="sxs-lookup"><span data-stu-id="37777-118">Images</span></span>
* <span data-ttu-id="37777-119">все, что не указано в таблице выше.</span><span class="sxs-lookup"><span data-stu-id="37777-119">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="37777-120">Пример разметки Markdown</span><span class="sxs-lookup"><span data-stu-id="37777-120">Markdown Example</span></span>

<span data-ttu-id="37777-121">Приведенный далее код визуализирует текст с такой разметкой:</span><span class="sxs-lookup"><span data-stu-id="37777-121">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="37777-123">Форматирование и локализация даты и времени</span><span class="sxs-lookup"><span data-stu-id="37777-123">Date/Time formatting and localization</span></span>

<span data-ttu-id="37777-124">Иногда часовой пояс получателя карточки неизвестен, поэтому в адаптивных карточках реализованы функции форматирования `DATE()` и `TIME()` для автоматической локализации времени на целевом устройстве.</span><span class="sxs-lookup"><span data-stu-id="37777-124">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="37777-125">Пример отображения даты и времени</span><span class="sxs-lookup"><span data-stu-id="37777-125">Date/Time Example</span></span>

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

<span data-ttu-id="37777-126">На карточке из этого примера будет отображено следующее:</span><span class="sxs-lookup"><span data-stu-id="37777-126">The above card will display:</span></span> 

> <span data-ttu-id="37777-127">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM** (Ваша посылка прибудет во вторник 14 февраля 2017 г. в 06:00).</span><span class="sxs-lookup"><span data-stu-id="37777-127">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="37777-128">Правила для функций даты и времени</span><span class="sxs-lookup"><span data-stu-id="37777-128">Date/Time function rules</span></span>

<span data-ttu-id="37777-129">Существуют некоторые требования к правильной интерпретации даты и времени на разных платформах.</span><span class="sxs-lookup"><span data-stu-id="37777-129">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="37777-130">Если эти требования не соблюдать, будет отображаться необработанная строка.</span><span class="sxs-lookup"><span data-stu-id="37777-130">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="37777-131">**Регистр учитывается** (нужно использовать только прописные буквы).</span><span class="sxs-lookup"><span data-stu-id="37777-131">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="37777-132">**Не должно быть пробелов** между `{{`, `}}` или круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="37777-132">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="37777-133">**Нужно строго соблюдать требования к форматированию стандарта [RFC 3389](https://tools.ietf.org/html/rfc3339)** (см. примеры ниже).</span><span class="sxs-lookup"><span data-stu-id="37777-133">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="37777-134">**Необходимо указать** допустимое значение даты и времени.</span><span class="sxs-lookup"><span data-stu-id="37777-134">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="37777-135">Допустимые форматы</span><span class="sxs-lookup"><span data-stu-id="37777-135">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="37777-136">Параметры форматирования даты</span><span class="sxs-lookup"><span data-stu-id="37777-136">Date formatting param</span></span>

<span data-ttu-id="37777-137">Для отображения даты можно использовать дополнительные параметры форматирования.</span><span class="sxs-lookup"><span data-stu-id="37777-137">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="37777-138">Формат</span><span class="sxs-lookup"><span data-stu-id="37777-138">Format</span></span>        |            <span data-ttu-id="37777-139">Пример</span><span class="sxs-lookup"><span data-stu-id="37777-139">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="37777-140">`COMPACT` (по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="37777-140">`COMPACT` (Default)</span></span> |          <span data-ttu-id="37777-141">"13.02.2017"</span><span class="sxs-lookup"><span data-stu-id="37777-141">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="37777-142">"Пн 13 февраля 2017 г."</span><span class="sxs-lookup"><span data-stu-id="37777-142">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="37777-143">"Понедельник 13 февраля 2017 г."</span><span class="sxs-lookup"><span data-stu-id="37777-143">"Monday, February 13th, 2017"</span></span> |

