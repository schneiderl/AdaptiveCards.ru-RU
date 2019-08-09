---
title: Служба шаблонов адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 81d1e598b6157b6ba1fedbf458a7c624705afcd5
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878891"
---
# <a name="adaptive-cards-template-service"></a><span data-ttu-id="93bad-102">Служба шаблонов адаптивных карт</span><span class="sxs-lookup"><span data-stu-id="93bad-102">Adaptive Cards Template Service</span></span>

<span data-ttu-id="93bad-103">Служба шаблонов адаптивных карт — это служба для подтверждения концепции, которая позволяет любому пользователю находить, публиковать и совместно использовать набор хорошо известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="93bad-103">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="93bad-104">Это полезно, если требуется отобразить некоторые данные, но не нужно тратить на них настраиваемую адаптивную карту.</span><span class="sxs-lookup"><span data-stu-id="93bad-104">It's useful if you want to display some data but don't want to bother writing a custom adaptive card for it.</span></span>

> <span data-ttu-id="93bad-105">Дополнительные сведения о шаблонах [адаптивных карт](index.md) см. в этой статье.</span><span class="sxs-lookup"><span data-stu-id="93bad-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="93bad-106">*Условия и соглашения*</span><span class="sxs-lookup"><span data-stu-id="93bad-106">*Terms and agreement*</span></span> 
> 
> <span data-ttu-id="93bad-107">Эта служба на **уровне альфа** предоставляется "как есть", со всеми ошибками и не поддерживается каким-либо образом.</span><span class="sxs-lookup"><span data-stu-id="93bad-107">This **alpha-level** service is provided "as-is", with all faults and is not supported in any way.</span></span> <span data-ttu-id="93bad-108">Любой сбор данных из службы подчиняется заявлению [о конфиденциальности Майкрософт](https://go.microsoft.com/fwlink/?LinkID=824704).</span><span class="sxs-lookup"><span data-stu-id="93bad-108">Any data collection from the service is subject to the [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkID=824704).</span></span>
> 
> <span data-ttu-id="93bad-109">Эти функции доступны **в предварительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="93bad-109">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="93bad-110">Ваш отзыв не только Добро пожаловать, но и важен для обеспечения того, чтобы мы доставлять нужные **вам** функции.</span><span class="sxs-lookup"><span data-stu-id="93bad-110">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-does-the-service-help-me"></a><span data-ttu-id="93bad-111">Как служба помогает мне?</span><span class="sxs-lookup"><span data-stu-id="93bad-111">How does the service help me?</span></span>

<span data-ttu-id="93bad-112">Предположим, что у меня есть фрагмент данных, возможно, это финансовые данные, Microsoft Graph данные, schema.org данные или пользовательские данные из моей организации.</span><span class="sxs-lookup"><span data-stu-id="93bad-112">Let's say I just got a piece of data, maybe it's financial data, Microsoft Graph data, schema.org data, or custom data from within my organization.</span></span> 

<span data-ttu-id="93bad-113">Теперь я хочу отобразить данные пользователю.</span><span class="sxs-lookup"><span data-stu-id="93bad-113">Now I want to display the data to a user.</span></span> 

<span data-ttu-id="93bad-114">Традиционно это означает написание пользовательского ПОЛЬЗОВАТЕЛЬСКОГО кода во всех внешних стеках, которые я доставляет конечным пользователям.</span><span class="sxs-lookup"><span data-stu-id="93bad-114">Traditionally that means writing custom UI code in all of the front-end stacks that I deliver to end-users.</span></span>

<span data-ttu-id="93bad-115">Но что, если существовал мир, где мое приложение могло бы «изучать» новые шаблоны пользовательского интерфейса на основе типа данных?</span><span class="sxs-lookup"><span data-stu-id="93bad-115">But what if there were a world where my app could "learn" new UI templates based on the type of data?</span></span> <span data-ttu-id="93bad-116">Мир, в котором любой пользователь может вносить, улучшать и совместно использовать общие шаблоны пользовательского интерфейса в своих проектах, в организации или для всего Интернета.</span><span class="sxs-lookup"><span data-stu-id="93bad-116">A world where anyone could contribute, enhance, and share common UI templates, within their own projects, within an organization, or for the entire internet.</span></span>

## <a name="what-is-the-card-template-service"></a><span data-ttu-id="93bad-117">Что такое служба шаблонов карточек?</span><span class="sxs-lookup"><span data-stu-id="93bad-117">What is the card template service?</span></span>

<span data-ttu-id="93bad-118">Служба шаблонов карточек — это простая конечная точка RESTFUL, которая помогает:</span><span class="sxs-lookup"><span data-stu-id="93bad-118">The card template service is a simple REST endpoint that helps:</span></span>

* <span data-ttu-id="93bad-119">**Поиск** шаблона путем анализа структуры данных</span><span class="sxs-lookup"><span data-stu-id="93bad-119">**Find** a template by analyzing the structure of your data</span></span>
* <span data-ttu-id="93bad-120">**Получите** шаблон, чтобы привязать его непосредственно на клиенте, *не отправляя данные на сервер или не выходя из устройства* .</span><span class="sxs-lookup"><span data-stu-id="93bad-120">**Get** a template so you can bind it directly on the client, *without sending your data to the server or ever leaving the device*</span></span>
* <span data-ttu-id="93bad-121">**Заполнение** шаблона на сервере, когда привязка данных на стороне клиента не подходит или возможно</span><span class="sxs-lookup"><span data-stu-id="93bad-121">**Populate** a template on the server, when client-side data binding isn't appropriate or possible</span></span>

<span data-ttu-id="93bad-122">Под ним все это:</span><span class="sxs-lookup"><span data-stu-id="93bad-122">Behind it all, is:</span></span>

* <span data-ttu-id="93bad-123">Общий репозиторий шаблонов с открытым исходным кодом, поддерживающий GitHub.</span><span class="sxs-lookup"><span data-stu-id="93bad-123">A shared, open-source template repository backed by GitHub.</span></span> <span data-ttu-id="93bad-124">*(Репозиторий в настоящий момент является частным, но будет сделан открытым, как только мы привязать некоторые свободные концы)*</span><span class="sxs-lookup"><span data-stu-id="93bad-124">*(The repo is currently private but will be made public as soon as we tie up some loose ends)*</span></span>
* <span data-ttu-id="93bad-125">Все шаблоны представляют собой плоские JSON-файлы в репозитории, что упрощает редактирование, участие и совместное использование рабочего процесса разработчика.</span><span class="sxs-lookup"><span data-stu-id="93bad-125">All the templates are flat JSON files in the repo, which makes editing, contributing, and sharing a natural part of a developer workflow.</span></span>
* <span data-ttu-id="93bad-126">Код для службы будет сделан доступным, чтобы вы могли разместить все, что вам нужно.</span><span class="sxs-lookup"><span data-stu-id="93bad-126">The code for the service will be made available so you can host wherever makes the most sense to you.</span></span> 

## <a name="using-the-service"></a><span data-ttu-id="93bad-127">Использование службы</span><span class="sxs-lookup"><span data-stu-id="93bad-127">Using the service</span></span>

### <a name="get-all-templates"></a><span data-ttu-id="93bad-128">Получить все шаблоны</span><span class="sxs-lookup"><span data-stu-id="93bad-128">Get all templates</span></span> 

<span data-ttu-id="93bad-129">Эта конечная точка возвращает список всех известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="93bad-129">This endpoint returns a list of all known templates.</span></span>

> `HTTP GET https://templates.adaptivecards.io/list`

<span data-ttu-id="93bad-130">**Фрагмент ответа**</span><span class="sxs-lookup"><span data-stu-id="93bad-130">**Response excerpt**</span></span>

```json
{
  "graph.microsoft.com": {
    "templates": [
      {
        "file": "Files.json",
        "fullPath": "graph.microsoft.com/Files.json"
      },
      {
        "file": "Profile.json",
        "fullPath": "graph.microsoft.com/Profile.json"
      }
   ]
}
```

### <a name="find-a-template"></a><span data-ttu-id="93bad-131">Поиск шаблона</span><span class="sxs-lookup"><span data-stu-id="93bad-131">Find a template</span></span>

<span data-ttu-id="93bad-132">Эта конечная точка пытается найти шаблон путем анализа структуры данных.</span><span class="sxs-lookup"><span data-stu-id="93bad-132">This endpoint tries to find a template by analyzing the structure of your data.</span></span>

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a><span data-ttu-id="93bad-133">Пример</span><span class="sxs-lookup"><span data-stu-id="93bad-133">Example</span></span>

<span data-ttu-id="93bad-134">Предположим, что я просто нажал на конечную точку [Microsoft Graph](https://graph.microsoft.com) , чтобы получать организационные данные.</span><span class="sxs-lookup"><span data-stu-id="93bad-134">Let's say I just hit a [Microsoft Graph](https://graph.microsoft.com) endpoint to get organizational data about me.</span></span>

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Снимок экрана проводника Graph](content/2019-08-01-12-08-13.png)

<span data-ttu-id="93bad-136">Этот API вернул **данные JSON**, но как **отображать их** пользователям с помощью адаптивных карт?</span><span class="sxs-lookup"><span data-stu-id="93bad-136">That API returned **JSON data**, but how do I **display it** to users using Adaptive Cards?</span></span> 

<span data-ttu-id="93bad-137">Сначала я хочу узнать, существует ли шаблон для данных этого типа, поэтому я создаю HTTP-запрос к `/find` конечной точке с данными `POST body`в.</span><span class="sxs-lookup"><span data-stu-id="93bad-137">First I want to see if a template exists for this type of data, so I make an HTTP request to the `/find` endpoint with my data in the `POST body`.</span></span>

```
HTTP POST https://templates.adaptivecards.io/find

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

<span data-ttu-id="93bad-138">**Ответ**</span><span class="sxs-lookup"><span data-stu-id="93bad-138">**Response:**</span></span>

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

<span data-ttu-id="93bad-139">Служба возвращает список всех совпадающих шаблонов, а `confidence` также указывает, насколько близко это соответствие.</span><span class="sxs-lookup"><span data-stu-id="93bad-139">The service returns a list of any matching templates, along with a `confidence` indicating how close the match is.</span></span> <span data-ttu-id="93bad-140">Теперь можно использовать этот URL-адрес шаблона для **получения** шаблона или **заполнения** его на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="93bad-140">Now I can use that template URL to **get** the template, or **populate** it server-side.</span></span>

### <a name="get-a-template"></a><span data-ttu-id="93bad-141">Получение шаблона</span><span class="sxs-lookup"><span data-stu-id="93bad-141">Get a template</span></span>

<span data-ttu-id="93bad-142">Шаблон, полученный из этой конечной точки, можно заполнить данными во время выполнения [с помощью пакетов SDK для темплатнг](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="93bad-142">A template retrieved from this endpoint can be populated with data at runtime [using the templatng SDKs](sdk.md).</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

<span data-ttu-id="93bad-143">Можно также включить в шаблон "образец данных", что делает редактирование в конструкторе более удобным:</span><span class="sxs-lookup"><span data-stu-id="93bad-143">You can also include "sample data" with the template, which makes editing in the designer more friendly:</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a><span data-ttu-id="93bad-144">Пример</span><span class="sxs-lookup"><span data-stu-id="93bad-144">Example</span></span>

<span data-ttu-id="93bad-145">Попробуем получить шаблон Microsoft Graphного профиля, возвращенный `/find` выше.</span><span class="sxs-lookup"><span data-stu-id="93bad-145">Let's get the Microsoft Graph profile template that was returned from `/find` above.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="93bad-146">**Фрагмент ответа**</span><span class="sxs-lookup"><span data-stu-id="93bad-146">**Response excerpt**</span></span>

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "{name}"
    },
    {
        // ...snip
    }
  ]
}
```

<span data-ttu-id="93bad-147">Теперь используйте этот шаблон с пакетами [SDK для шаблонов](sdk.md) , чтобы создать готовую к просмотру адаптивную карту.</span><span class="sxs-lookup"><span data-stu-id="93bad-147">Now use this template with the [templating SDKs](sdk.md) to create a ready-to-render Adaptive Card.</span></span>

### <a name="populate-a-template-server-side"></a><span data-ttu-id="93bad-148">Заполнение шаблона на стороне сервера</span><span class="sxs-lookup"><span data-stu-id="93bad-148">Populate a template server-side</span></span>

<span data-ttu-id="93bad-149">В некоторых случаях не имеет смысла заполнять шаблон на клиенте.</span><span class="sxs-lookup"><span data-stu-id="93bad-149">In some cases it may not make sense to populate a template on the client.</span></span>  <span data-ttu-id="93bad-150">В этих случаях служба может вернуть полностью заполненную адаптивную карту, готовую к передаче любому адаптивному модулю подготовки карт.</span><span class="sxs-lookup"><span data-stu-id="93bad-150">For these use cases, you can have the service return a fully-populated Adaptive Card, ready to be passed to any Adaptive Card Renderer.</span></span>

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a><span data-ttu-id="93bad-151">Пример</span><span class="sxs-lookup"><span data-stu-id="93bad-151">Example</span></span>

<span data-ttu-id="93bad-152">Запустим шаблон Microsoft Graphного профиля, который был возвращен `/find` с помощью приведенных выше данных.</span><span class="sxs-lookup"><span data-stu-id="93bad-152">Let's populate the Microsoft Graph profile template that was returned from `/find` using the data above.</span></span>

```
HTTP POST https://templates.adaptivecards.io/graph.microsoft.com/Profile.json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

<span data-ttu-id="93bad-153">**Фрагмент ответа**</span><span class="sxs-lookup"><span data-stu-id="93bad-153">**Response excerpt**</span></span>

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "Megan Bowen"
    },
    {
        // ...snip
    }
  ]
}
```

<span data-ttu-id="93bad-154">Обратите внимание, что ответ `TextBlock` заменяет текст первого с помощью `"Megan Bowen"` вместо `"{name}"`, как в `GET` запросе.</span><span class="sxs-lookup"><span data-stu-id="93bad-154">Notice how the response replaced the text of the first `TextBlock` with `"Megan Bowen"` instead of `"{name}"`, as in the `GET` request.</span></span> <span data-ttu-id="93bad-155">Теперь эту Адаптивекард можно передать в любой адаптивный модуль подготовки карт, не прополняя клиентские шаблоны.</span><span class="sxs-lookup"><span data-stu-id="93bad-155">This AdaptiveCard can now be passed to any Adaptive Card renderer without going through client-side templating.</span></span>

## <a name="contributing-templates"></a><span data-ttu-id="93bad-156">Участвующие шаблоны</span><span class="sxs-lookup"><span data-stu-id="93bad-156">Contributing templates</span></span>

<span data-ttu-id="93bad-157">Служба шаблонов поддерживается репозиторием GitHub (в настоящее время является **частным**), но мы откроем исходный код после того, как мы присвоим несколько свободных окончаний.</span><span class="sxs-lookup"><span data-stu-id="93bad-157">The template service is backed by a GitHub repo (which is currently **private**), but we will open source once we tie up some loose ends.</span></span>

<span data-ttu-id="93bad-158">Мы надеемся, что, используя GitHub в качестве резервного хранилища для шаблонов, мы можем «более демократичным» процесс создания, улучшения и совместного использования шаблонов.</span><span class="sxs-lookup"><span data-stu-id="93bad-158">Our hope is that by using GitHub as a backing store for the templates, we can "democratize" the process of authoring, enhancing, and sharing templates.</span></span> <span data-ttu-id="93bad-159">Любой пользователь может отправить запрос на вытягивание, включающий совершенно новый шаблон, или внести улучшения в существующие... Все это в понятном для разработчика интерфейсе GitHub.</span><span class="sxs-lookup"><span data-stu-id="93bad-159">Anyone can submit a Pull Request that includes an entirely new template, or make enhancements to existing ones... all within the developer-friendly experience of GitHub.</span></span>

## <a name="self-hosting-the-service"></a><span data-ttu-id="93bad-160">Размещение службы в собственном размещении</span><span class="sxs-lookup"><span data-stu-id="93bad-160">Self-hosting the service</span></span>

<span data-ttu-id="93bad-161">Не все типы данных подходят для службы шаблона "Central" адаптивных карт, размещенной в `https://templates.adaptivecards.io`.</span><span class="sxs-lookup"><span data-stu-id="93bad-161">Not all types of data are appropriate for the "central" Adaptive Cards template service hosted at `https://templates.adaptivecards.io`.</span></span> 

<span data-ttu-id="93bad-162">Мы хотим убедиться, что любой пользователь может разместить службу шаблонов в вашей организации, поэтому исходный код станет доступен, и мы сделаем его очень простым для развертывания в Azure или в своей серверной части.</span><span class="sxs-lookup"><span data-stu-id="93bad-162">We want to make sure anyone can host the template service within your organization, so the source code will be made available and we'll make it very simple to deploy to Azure or your own back-end.</span></span>

<span data-ttu-id="93bad-163">Подробнее об этом позже.</span><span class="sxs-lookup"><span data-stu-id="93bad-163">More on this at a later date.</span></span>