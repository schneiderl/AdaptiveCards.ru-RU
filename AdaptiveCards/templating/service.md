---
title: Служба шаблонов адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 8ccccd3c3e67324acf123e03b947372e1517faab
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454987"
---
# <a name="adaptive-cards-template-service"></a><span data-ttu-id="650ab-102">Служба шаблонов адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="650ab-102">Adaptive Cards Template Service</span></span>

<span data-ttu-id="650ab-103">Служба шаблонов адаптивных карточек является службой проверки концепции, которая позволяет всем пользователям находить шаблоны, вносить свой вклад и делиться набором известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="650ab-103">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="650ab-104">Она полезна, если вы хотите отобразить определенные данные, но не хотите создавать для них отдельную адаптивную карточку.</span><span class="sxs-lookup"><span data-stu-id="650ab-104">It's useful if you want to display some data but don't want to bother writing a custom adaptive card for it.</span></span>

> <span data-ttu-id="650ab-105">Ознакомьтесь с [общими сведениями о работе с шаблонами адаптивных карточек](index.md).</span><span class="sxs-lookup"><span data-stu-id="650ab-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="650ab-106">*Условия и соглашения*</span><span class="sxs-lookup"><span data-stu-id="650ab-106">*Terms and agreement*</span></span> 
> 
> <span data-ttu-id="650ab-107">Эта служба **уровня альфа** предоставляется на условиях "как есть", включая все возможные проблемы, и не обеспечивается никакой поддержкой.</span><span class="sxs-lookup"><span data-stu-id="650ab-107">This **alpha-level** service is provided "as-is", with all faults and is not supported in any way.</span></span> <span data-ttu-id="650ab-108">Любой сбор данных из этой службы согласуется с [заявлением о конфиденциальности корпорации Майкрософт](https://go.microsoft.com/fwlink/?LinkID=824704).</span><span class="sxs-lookup"><span data-stu-id="650ab-108">Any data collection from the service is subject to the [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkID=824704).</span></span>
> 
> <span data-ttu-id="650ab-109">Эти функции предоставляются в **ознакомительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="650ab-109">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="650ab-110">Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.</span><span class="sxs-lookup"><span data-stu-id="650ab-110">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-does-the-service-help-me"></a><span data-ttu-id="650ab-111">Как эта служба поможет вам?</span><span class="sxs-lookup"><span data-stu-id="650ab-111">How does the service help me?</span></span>

<span data-ttu-id="650ab-112">Предположим, что у вас уже есть определенный фрагмент данных (например, из финансовой системы, Microsoft Graph, schema.org или пользовательской службы организации).</span><span class="sxs-lookup"><span data-stu-id="650ab-112">Let's say I just got a piece of data, maybe it's financial data, Microsoft Graph data, schema.org data, or custom data from within my organization.</span></span> 

<span data-ttu-id="650ab-113">Эти данные нужно отображать для пользователей.</span><span class="sxs-lookup"><span data-stu-id="650ab-113">Now I want to display the data to a user.</span></span> 

<span data-ttu-id="650ab-114">Обычно для этого приходилось писать пользовательский код во всех интерфейсных стеках, через которые данные доставляются пользователям.</span><span class="sxs-lookup"><span data-stu-id="650ab-114">Traditionally that means writing custom UI code in all of the front-end stacks that I deliver to end-users.</span></span>

<span data-ttu-id="650ab-115">Но что, если бы приложение могло самостоятельно обнаруживать новые шаблоны для пользовательского интерфейса, используя типы предоставленных данных?</span><span class="sxs-lookup"><span data-stu-id="650ab-115">But what if there were a world where my app could "learn" new UI templates based on the type of data?</span></span> <span data-ttu-id="650ab-116">При этом любой пользователь мог бы добавлять, улучшать и применять в своих проектах общие шаблоны для пользовательского интерфейса. И не только в пределах организации, но и во всем Интернете.</span><span class="sxs-lookup"><span data-stu-id="650ab-116">A world where anyone could contribute, enhance, and share common UI templates, within their own projects, within an organization, or for the entire internet.</span></span>

## <a name="what-is-the-card-template-service"></a><span data-ttu-id="650ab-117">Так что же собой представляет служба шаблонов карточек?</span><span class="sxs-lookup"><span data-stu-id="650ab-117">What is the card template service?</span></span>

<span data-ttu-id="650ab-118">По сути, служба шаблонов карточек — это конечная точка RESTful, которая помогает выполнять следующие операции:</span><span class="sxs-lookup"><span data-stu-id="650ab-118">The card template service is a simple REST endpoint that helps:</span></span>

* <span data-ttu-id="650ab-119">**поиск** шаблона на основе анализа структуры данных;</span><span class="sxs-lookup"><span data-stu-id="650ab-119">**Find** a template by analyzing the structure of your data</span></span>
* <span data-ttu-id="650ab-120">**получение** шаблона, который можно привязать к данным непосредственно в клиенте, *не отправляя данные на сервер или не перемещая их с устройства иным образом*;</span><span class="sxs-lookup"><span data-stu-id="650ab-120">**Get** a template so you can bind it directly on the client, *without sending your data to the server or ever leaving the device*</span></span>
* <span data-ttu-id="650ab-121">**заполнение** шаблона на сервере, если привязка данных на стороне клиента невозможна или неудобна.</span><span class="sxs-lookup"><span data-stu-id="650ab-121">**Populate** a template on the server, when client-side data binding isn't appropriate or possible</span></span>

<span data-ttu-id="650ab-122">В основе этой службы лежит следующее:</span><span class="sxs-lookup"><span data-stu-id="650ab-122">Behind it all, is:</span></span>

* <span data-ttu-id="650ab-123">Общий репозиторий шаблонов с открытым кодом на сайте GitHub</span><span class="sxs-lookup"><span data-stu-id="650ab-123">A shared, open-source template repository backed by GitHub.</span></span> <span data-ttu-id="650ab-124">*(сейчас этот репозиторий считается частным, но он станет открытым, как только мы решим самые очевидные проблемы)* .</span><span class="sxs-lookup"><span data-stu-id="650ab-124">*(The repo is currently private but will be made public as soon as we tie up some loose ends)*</span></span>
* <span data-ttu-id="650ab-125">Все шаблоны в этим репозитории — это неструктурированные JSON-файлы. Это упрощает редактирование, обсуждение и предоставление шаблонов в рамках обычного рабочего процесса разработки.</span><span class="sxs-lookup"><span data-stu-id="650ab-125">All the templates are flat JSON files in the repo, which makes editing, contributing, and sharing a natural part of a developer workflow.</span></span>
* <span data-ttu-id="650ab-126">К коду этой службы будет предоставлен доступ, чтобы вы могли разместить любую полезную для себя информацию.</span><span class="sxs-lookup"><span data-stu-id="650ab-126">The code for the service will be made available so you can host wherever makes the most sense to you.</span></span> 

## <a name="using-the-service"></a><span data-ttu-id="650ab-127">Использование службы</span><span class="sxs-lookup"><span data-stu-id="650ab-127">Using the service</span></span>

### <a name="get-all-templates"></a><span data-ttu-id="650ab-128">Получение полного списка шаблонов</span><span class="sxs-lookup"><span data-stu-id="650ab-128">Get all templates</span></span> 

<span data-ttu-id="650ab-129">Эта конечная точка возвращает список всех известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="650ab-129">This endpoint returns a list of all known templates.</span></span>

> `HTTP GET https://templates.adaptivecards.io/list`

<span data-ttu-id="650ab-130">**Фрагмент ответа**</span><span class="sxs-lookup"><span data-stu-id="650ab-130">**Response excerpt**</span></span>

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

### <a name="find-a-template"></a><span data-ttu-id="650ab-131">Поиск шаблона</span><span class="sxs-lookup"><span data-stu-id="650ab-131">Find a template</span></span>

<span data-ttu-id="650ab-132">Эта конечная точка пытается найти шаблон, анализируя структуру данных.</span><span class="sxs-lookup"><span data-stu-id="650ab-132">This endpoint tries to find a template by analyzing the structure of your data.</span></span>

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a><span data-ttu-id="650ab-133">Пример</span><span class="sxs-lookup"><span data-stu-id="650ab-133">Example</span></span>

<span data-ttu-id="650ab-134">Предположим, что пользователь открывает конечную точку [Microsoft Graph](https://graph.microsoft.com) для получения данных организации о себе.</span><span class="sxs-lookup"><span data-stu-id="650ab-134">Let's say I just hit a [Microsoft Graph](https://graph.microsoft.com) endpoint to get organizational data about me.</span></span>

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Снимок экрана с обозревателем Graph](content/2019-08-01-12-08-13.png)

<span data-ttu-id="650ab-136">Этот API возвращает **данные в формате JSON**. Но как **отобразить их для пользователя** с помощью адаптивных карточек?</span><span class="sxs-lookup"><span data-stu-id="650ab-136">That API returned **JSON data**, but how do I **display it** to users using Adaptive Cards?</span></span> 

<span data-ttu-id="650ab-137">Сначала нужно выяснить, есть ли шаблон для данных этого типа. Для этого создается HTTP-запрос к конечной точке `/find` с данными в `POST body`.</span><span class="sxs-lookup"><span data-stu-id="650ab-137">First I want to see if a template exists for this type of data, so I make an HTTP request to the `/find` endpoint with my data in the `POST body`.</span></span>

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

<span data-ttu-id="650ab-138">**Ответ:**</span><span class="sxs-lookup"><span data-stu-id="650ab-138">**Response:**</span></span>

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

<span data-ttu-id="650ab-139">Служба возвращает полный список подходящих шаблонов с оценкой `confidence`, которая обозначает точность соответствия.</span><span class="sxs-lookup"><span data-stu-id="650ab-139">The service returns a list of any matching templates, along with a `confidence` indicating how close the match is.</span></span> <span data-ttu-id="650ab-140">Теперь по URL-адресу шаблона можно **получить** этот шаблон или **заполнить** его на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="650ab-140">Now I can use that template URL to **get** the template, or **populate** it server-side.</span></span>

### <a name="get-a-template"></a><span data-ttu-id="650ab-141">Получение шаблона</span><span class="sxs-lookup"><span data-stu-id="650ab-141">Get a template</span></span>

<span data-ttu-id="650ab-142">Шаблон, полученный из этой конечной точки, можно заполнить данными во время выполнения [с помощью пакетов SDK для работы с шаблонами](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="650ab-142">A template retrieved from this endpoint can be populated with data at runtime [using the templatng SDKs](sdk.md).</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

<span data-ttu-id="650ab-143">Вы также можете включить в шаблон "пример данных". Это упростит редактирование в конструкторе:</span><span class="sxs-lookup"><span data-stu-id="650ab-143">You can also include "sample data" with the template, which makes editing in the designer more friendly:</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a><span data-ttu-id="650ab-144">Пример</span><span class="sxs-lookup"><span data-stu-id="650ab-144">Example</span></span>

<span data-ttu-id="650ab-145">Давайте получим шаблон профиля Microsoft Graph, который мы нашли в `/find` выше.</span><span class="sxs-lookup"><span data-stu-id="650ab-145">Let's get the Microsoft Graph profile template that was returned from `/find` above.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="650ab-146">**Фрагмент ответа**</span><span class="sxs-lookup"><span data-stu-id="650ab-146">**Response excerpt**</span></span>

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

<span data-ttu-id="650ab-147">Теперь используйте этот шаблон с [пакетами SDK для работы с шаблонами](sdk.md), чтобы создать готовую к просмотру адаптивную карточку.</span><span class="sxs-lookup"><span data-stu-id="650ab-147">Now use this template with the [templating SDKs](sdk.md) to create a ready-to-render Adaptive Card.</span></span>

### <a name="populate-a-template-server-side"></a><span data-ttu-id="650ab-148">Заполнение шаблона на стороне сервера</span><span class="sxs-lookup"><span data-stu-id="650ab-148">Populate a template server-side</span></span>

<span data-ttu-id="650ab-149">В некоторых случаях нет смысла заполнять шаблон в клиенте.</span><span class="sxs-lookup"><span data-stu-id="650ab-149">In some cases it may not make sense to populate a template on the client.</span></span>  <span data-ttu-id="650ab-150">Для таких сценариев служба может возвращать полностью заполненную адаптивную карточку, которую вы передадите любому средству просмотра адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="650ab-150">For these use cases, you can have the service return a fully-populated Adaptive Card, ready to be passed to any Adaptive Card Renderer.</span></span>

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a><span data-ttu-id="650ab-151">Пример</span><span class="sxs-lookup"><span data-stu-id="650ab-151">Example</span></span>

<span data-ttu-id="650ab-152">Давайте заполним шаблон профиля Microsoft Graph, который мы нашли в `/find`, используя представленные выше данные.</span><span class="sxs-lookup"><span data-stu-id="650ab-152">Let's populate the Microsoft Graph profile template that was returned from `/find` using the data above.</span></span>

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

<span data-ttu-id="650ab-153">**Фрагмент ответа**</span><span class="sxs-lookup"><span data-stu-id="650ab-153">**Response excerpt**</span></span>

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

<span data-ttu-id="650ab-154">Обратите внимание, что в ответе текст первого вхождения `TextBlock` содержит `"Megan Bowen"` вместо `"{name}"`, как в запросе `GET`.</span><span class="sxs-lookup"><span data-stu-id="650ab-154">Notice how the response replaced the text of the first `TextBlock` with `"Megan Bowen"` instead of `"{name}"`, as in the `GET` request.</span></span> <span data-ttu-id="650ab-155">Теперь эту адаптивную карточку можно передать в любое средство просмотра адаптивных карточек, не применяя методы обработки шаблонов на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="650ab-155">This AdaptiveCard can now be passed to any Adaptive Card renderer without going through client-side templating.</span></span>

## <a name="contributing-templates"></a><span data-ttu-id="650ab-156">Участие в разработке шаблонов</span><span class="sxs-lookup"><span data-stu-id="650ab-156">Contributing templates</span></span>

<span data-ttu-id="650ab-157">Служба шаблонов работает на основе репозитория GitHub, который сейчас является **закрытым**, но будет открыт сразу после устранения наиболее очевидных проблем.</span><span class="sxs-lookup"><span data-stu-id="650ab-157">The template service is backed by a GitHub repo (which is currently **private**), but we will open source once we tie up some loose ends.</span></span>

<span data-ttu-id="650ab-158">Мы надеемся, что использование GitHub в качестве резервного хранилища для шаблонов позволит нам сделать более "демократичными" процессы создания, развития и совместного использования шаблонов.</span><span class="sxs-lookup"><span data-stu-id="650ab-158">Our hope is that by using GitHub as a backing store for the templates, we can "democratize" the process of authoring, enhancing, and sharing templates.</span></span> <span data-ttu-id="650ab-159">Любой желающий может отправить запрос на вытягивание для нового шаблона или внести улучшения в существующие, используя удобный и привычный для разработчика интерфейс GitHub.</span><span class="sxs-lookup"><span data-stu-id="650ab-159">Anyone can submit a Pull Request that includes an entirely new template, or make enhancements to existing ones... all within the developer-friendly experience of GitHub.</span></span>

## <a name="self-hosting-the-service"></a><span data-ttu-id="650ab-160">Размещение службы на собственном оборудовании</span><span class="sxs-lookup"><span data-stu-id="650ab-160">Self-hosting the service</span></span>

<span data-ttu-id="650ab-161">Не все типы данных можно размещать в "централизованной" службе шаблонов адаптивных карт на `https://templates.adaptivecards.io`.</span><span class="sxs-lookup"><span data-stu-id="650ab-161">Not all types of data are appropriate for the "central" Adaptive Cards template service hosted at `https://templates.adaptivecards.io`.</span></span> 

<span data-ttu-id="650ab-162">Мы сделаем так, что любой желающий сможет разместить службу шаблонов в пределах своей организации. Для этого мы не только откроем исходный код службы, но и создадим очень простые методы для развертывания в Azure или на клиентском оборудовании.</span><span class="sxs-lookup"><span data-stu-id="650ab-162">We want to make sure anyone can host the template service within your organization, so the source code will be made available and we'll make it very simple to deploy to Azure or your own back-end.</span></span>

<span data-ttu-id="650ab-163">Дополнительная информация об этом будет доступна позже.</span><span class="sxs-lookup"><span data-stu-id="650ab-163">More on this at a later date.</span></span>