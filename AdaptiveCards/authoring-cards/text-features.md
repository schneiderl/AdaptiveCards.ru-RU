---
title: Текстовые функции
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: ac8ec0c48e06377ebd17f1b31abe463c48809fe3
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "59553616"
---
# <a name="text-features"></a><span data-ttu-id="63add-102">Текстовые функции</span><span class="sxs-lookup"><span data-stu-id="63add-102">Text features</span></span>

<span data-ttu-id="63add-103">`TextBlock` предоставляет некоторые дополнительные функции для форматирования и локализации текста.</span><span class="sxs-lookup"><span data-stu-id="63add-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="63add-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="63add-104">Markdown</span></span>
<span data-ttu-id="63add-105">Встроенная функция разметки адаптивных карточек реализована за счет поддержки **соответствующих компонентов** синтаксиса Markdown.</span><span class="sxs-lookup"><span data-stu-id="63add-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="63add-106">_Поддерживается_</span><span class="sxs-lookup"><span data-stu-id="63add-106">_Supported_</span></span>

| <span data-ttu-id="63add-107">Стиль текста</span><span class="sxs-lookup"><span data-stu-id="63add-107">Text Style</span></span>      | <span data-ttu-id="63add-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="63add-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="63add-109">**Жирный**</span><span class="sxs-lookup"><span data-stu-id="63add-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="63add-110">_Наклонный_</span><span class="sxs-lookup"><span data-stu-id="63add-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="63add-111">Маркированный список</span><span class="sxs-lookup"><span data-stu-id="63add-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="63add-112">Нумерованный список</span><span class="sxs-lookup"><span data-stu-id="63add-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="63add-113">Гиперссылки</span><span class="sxs-lookup"><span data-stu-id="63add-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="63add-114">_Не поддерживается_</span><span class="sxs-lookup"><span data-stu-id="63add-114">_Not supported_</span></span>

* <span data-ttu-id="63add-115">Заголовки</span><span class="sxs-lookup"><span data-stu-id="63add-115">Headers</span></span>
* <span data-ttu-id="63add-116">таблицы;</span><span class="sxs-lookup"><span data-stu-id="63add-116">Tables</span></span>
* <span data-ttu-id="63add-117">образы,</span><span class="sxs-lookup"><span data-stu-id="63add-117">Images</span></span>
* <span data-ttu-id="63add-118">все, что не указано в таблице выше.</span><span class="sxs-lookup"><span data-stu-id="63add-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="63add-119">Пример разметки Markdown</span><span class="sxs-lookup"><span data-stu-id="63add-119">Markdown Example</span></span>

<span data-ttu-id="63add-120">Приведенный далее код визуализирует текст с такой разметкой:</span><span class="sxs-lookup"><span data-stu-id="63add-120">The below payload would render something like this:</span></span>

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
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="63add-122">Форматирование и локализация даты и времени</span><span class="sxs-lookup"><span data-stu-id="63add-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="63add-123">Иногда часовой пояс получателя карточки неизвестен, поэтому в адаптивных карточках реализованы функции форматирования `DATE()` и `TIME()` для автоматической локализации времени на целевом устройстве.</span><span class="sxs-lookup"><span data-stu-id="63add-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="63add-124">Пример отображения даты и времени</span><span class="sxs-lookup"><span data-stu-id="63add-124">Date/Time Example</span></span>

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

<span data-ttu-id="63add-125">На карточке из этого примера будет отображено следующее:</span><span class="sxs-lookup"><span data-stu-id="63add-125">The above card will display:</span></span> 

> <span data-ttu-id="63add-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM** (Ваша посылка прибудет во вторник 14 февраля 2017 г. в 06:00).</span><span class="sxs-lookup"><span data-stu-id="63add-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="63add-127">Правила для функций даты и времени</span><span class="sxs-lookup"><span data-stu-id="63add-127">Date/Time function rules</span></span>

<span data-ttu-id="63add-128">Существуют некоторые требования к правильной интерпретации даты и времени на разных платформах.</span><span class="sxs-lookup"><span data-stu-id="63add-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="63add-129">Если эти требования не соблюдать, будет отображаться необработанная строка.</span><span class="sxs-lookup"><span data-stu-id="63add-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="63add-130">**Регистр учитывается** (нужно использовать только прописные буквы).</span><span class="sxs-lookup"><span data-stu-id="63add-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="63add-131">**Не должно быть пробелов** между `{{`, `}}` или круглыми скобками.</span><span class="sxs-lookup"><span data-stu-id="63add-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="63add-132">**Нужно строго соблюдать требования к форматированию стандарта [RFC 3389](https://tools.ietf.org/html/rfc3339)** (см. примеры ниже).</span><span class="sxs-lookup"><span data-stu-id="63add-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="63add-133">**Необходимо указать** допустимое значение даты и времени.</span><span class="sxs-lookup"><span data-stu-id="63add-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="63add-134">Допустимые форматы</span><span class="sxs-lookup"><span data-stu-id="63add-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="63add-135">Параметры форматирования даты</span><span class="sxs-lookup"><span data-stu-id="63add-135">Date formatting param</span></span>

<span data-ttu-id="63add-136">Для отображения даты можно использовать дополнительные параметры форматирования.</span><span class="sxs-lookup"><span data-stu-id="63add-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="63add-137">Формат</span><span class="sxs-lookup"><span data-stu-id="63add-137">Format</span></span>        |            <span data-ttu-id="63add-138">Пример</span><span class="sxs-lookup"><span data-stu-id="63add-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="63add-139">`COMPACT` (по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="63add-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="63add-140">"13.02.2017"</span><span class="sxs-lookup"><span data-stu-id="63add-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="63add-141">"Пн 13 февраля 2017 г."</span><span class="sxs-lookup"><span data-stu-id="63add-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="63add-142">"Понедельник 13 февраля 2017 г."</span><span class="sxs-lookup"><span data-stu-id="63add-142">"Monday, February 13th, 2017"</span></span> |

