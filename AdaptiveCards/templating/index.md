---
title: Общие сведения о создании шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 07/29/2019
ms.topic: article
ms.openlocfilehash: 11ade4c2a41111f372873ea9a0677fe823c5b0ab
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750423"
---
# <a name="adaptive-cards-templating-preview"></a><span data-ttu-id="180a8-102">Создание шаблонов адаптивных карточек (ознакомительная версия)</span><span class="sxs-lookup"><span data-stu-id="180a8-102">Adaptive Cards Templating (Preview)</span></span>

<span data-ttu-id="180a8-103">Мы рады представить ознакомительную версию новых средств, которые позволяют **создавать** и **повторно использовать** карточки, а также **делиться** ими.</span><span class="sxs-lookup"><span data-stu-id="180a8-103">We're excited to share a preview of new tools that will help you **create**, **reuse**, and **share** Adaptive Cards.</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="180a8-104">Эти функции предоставляются в **ознакомительной версии и могут быть изменены**.</span><span class="sxs-lookup"><span data-stu-id="180a8-104">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="180a8-105">Ваши отзывы не только приветствуются, но и имеют решающее значение: только благодаря им мы сможем предоставлять функции, которые **вам** действительно необходимы.</span><span class="sxs-lookup"><span data-stu-id="180a8-105">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-can-templating-help-you"></a><span data-ttu-id="180a8-106">Преимущества создания шаблонов</span><span class="sxs-lookup"><span data-stu-id="180a8-106">How can templating help you?</span></span>

<span data-ttu-id="180a8-107">Путем создания шаблонов вы можете отделить **данные** от **макета** в адаптивной карточке.</span><span class="sxs-lookup"><span data-stu-id="180a8-107">Templating enables the separation of **data** from the **layout** in an Adaptive Card.</span></span> 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a><span data-ttu-id="180a8-108">Карточку, спроектированную с применением одного средства, можно сразу заполнить реальными данными</span><span class="sxs-lookup"><span data-stu-id="180a8-108">It helps design a card once, and then populate it with real data</span></span>

<span data-ttu-id="180a8-109">Сегодня невозможно создать карточку с помощью [конструктора адаптивных карточек](https://adaptivecards.io/designer) и использовать этот JSON-файл для наполнения полезных данных **динамическим содержимым**.</span><span class="sxs-lookup"><span data-stu-id="180a8-109">Today it's impossible to create a card using the [Adaptive Card Designer](https://adaptivecards.io/designer) and use that JSON to populate the payload with **dynamic content**.</span></span> <span data-ttu-id="180a8-110">В таком случае необходимо написать пользовательский код для создания строки JSON или использовать пакет SDK объектной модели для создания объектной модели, представляющей вашу карточку, и сериализовать ее в JSON.</span><span class="sxs-lookup"><span data-stu-id="180a8-110">In order to achieve this you must write custom code to build a JSON string, or use the Object Model SDKs to build an OM representing your card and serialize it to JSON.</span></span> <span data-ttu-id="180a8-111">В любом случае использование конструктора — это однократная односторонняя операция, которая не позволяет легко настроить дизайн карточки позже, после того как вы преобразовали ее в код.</span><span class="sxs-lookup"><span data-stu-id="180a8-111">In either case the Designer is a one-time one-way operation and doesn't make it easy to tweak the card design later once you've converted it to code.</span></span>

### <a name="it-makes-tranmissions-over-the-wire-smaller"></a><span data-ttu-id="180a8-112">Меньший объем передаваемых по сети данных</span><span class="sxs-lookup"><span data-stu-id="180a8-112">It makes tranmissions over the wire smaller</span></span>

<span data-ttu-id="180a8-113">Представьте себе мир, в котором шаблон и данные можно объединить **непосредственно в клиенте**.</span><span class="sxs-lookup"><span data-stu-id="180a8-113">Imagine a world where a template and data can be combined **directly on the client**.</span></span> <span data-ttu-id="180a8-114">Это означает, что если вы используете один и тот же шаблон несколько раз или хотите обновить в нем данные, вам просто нужно отправить новые данные на устройство, и оно может повторно применять один и тот же шаблон снова и снова.</span><span class="sxs-lookup"><span data-stu-id="180a8-114">This means if you use the same template multiple times, or want to update it with new data, you just need to send new data to the device and it can re-use the same template over and over.</span></span>

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a><span data-ttu-id="180a8-115">Возможность создавать великолепные карточки с использованием предоставленных пользователями данных</span><span class="sxs-lookup"><span data-stu-id="180a8-115">It helps you create a great looking card from just the data you provide</span></span>

<span data-ttu-id="180a8-116">Мы считаем, что адаптивные карточки — это отличная идея, но что если вам бы не приходилось самостоятельно создавать адаптивную карточку для всего, что вы хотите показать пользователю?</span><span class="sxs-lookup"><span data-stu-id="180a8-116">We think Adaptive Cards are great, but what if you didn't have to write an Adaptive Card for everything you want to display to a user?</span></span> <span data-ttu-id="180a8-117">С помощью службы шаблонов (описанной ниже) мы можем создать среду, в которой каждый сможет добавлять, открывать и публиковать шаблоны с любыми типами данных.</span><span class="sxs-lookup"><span data-stu-id="180a8-117">With a template service (described below) we can create a world where everyone can contribute, discover, and share templates over any type of data.</span></span> 

<span data-ttu-id="180a8-118">Делитесь шаблонами в своих проектах, вашей организации или со всеми в Интернете.</span><span class="sxs-lookup"><span data-stu-id="180a8-118">Share within your own projects, your organization, or with the entire internet.</span></span>

### <a name="ai-and-other-services-could-improve-user-experiences"></a><span data-ttu-id="180a8-119">Улучшенное взаимодействие с пользователем благодаря искусственному интеллекту и другим службам</span><span class="sxs-lookup"><span data-stu-id="180a8-119">AI and other services could improve user experiences</span></span>

<span data-ttu-id="180a8-120">Отделение данных от содержимого открывает возможности использования ИИ и других служб с карточками, повышая эффективность работы пользователей и помогая выполнять поиск.</span><span class="sxs-lookup"><span data-stu-id="180a8-120">By separating data from content it opens a door for AI and other services to  "reason" over the data in the cards we see and enhance user productivity or help us find things.</span></span>

## <a name="what-is-adaptive-cards-templating"></a><span data-ttu-id="180a8-121">Процесс создания шаблонов адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="180a8-121">What is Adaptive Cards Templating?</span></span>

<span data-ttu-id="180a8-122">Этот процесс состоит из 3 основных компонентов:</span><span class="sxs-lookup"><span data-stu-id="180a8-122">It's comprised of 3 major components:</span></span>

1. <span data-ttu-id="180a8-123">**[Язык шаблонов](language.md)**  — это синтаксис, используемый для создания шаблона.</span><span class="sxs-lookup"><span data-stu-id="180a8-123">The **[Template Language](language.md)** is the syntax used for authoring a template.</span></span> <span data-ttu-id="180a8-124">Конструктор также позволяет вам просматривать шаблоны во время разработки, добавляя примеры данных.</span><span class="sxs-lookup"><span data-stu-id="180a8-124">The Designer even lets you preview your templates at design time by including "sample data".</span></span>
2. <span data-ttu-id="180a8-125">**[Пакеты SDK для создания шаблонов](sdk.md)** будут присутствовать на всех поддерживаемых платформах адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="180a8-125">The **[Templating SDK's](sdk.md)** will exist on all supported Adaptive Card platforms.</span></span> <span data-ttu-id="180a8-126">Эти пакеты SDK позволяют вам заполнять шаблон реальными данными на сервере или непосредственно в клиенте.</span><span class="sxs-lookup"><span data-stu-id="180a8-126">These SDKs allow you to populate a template with real data, on the back-end or directly on the client.</span></span> 
3. <span data-ttu-id="180a8-127">**[Служба шаблонов](service.md)** является службой проверки концепции, которая позволяет всем пользователям находить шаблоны, вносить свой вклад и делиться набором известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="180a8-127">The **[Template Service](service.md)** is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

## <a name="template-language"></a><span data-ttu-id="180a8-128">Язык шаблонов</span><span class="sxs-lookup"><span data-stu-id="180a8-128">Template Language</span></span>

<span data-ttu-id="180a8-129">Язык шаблонов — это синтаксис, используемый для создания шаблона адаптивной карточки.</span><span class="sxs-lookup"><span data-stu-id="180a8-129">The template langauge is the syntax used to author an Adaptive Card template.</span></span> 

> [!NOTE]
> 
> <span data-ttu-id="180a8-130">Ознакомьтесь с приведенным ниже примером, открыв новую вкладку со страницей</span><span class="sxs-lookup"><span data-stu-id="180a8-130">Follow along with the example below by opening up a new tab to</span></span>
>
> **https://adaptivecards.io/designer**
> 
> <span data-ttu-id="180a8-131">Нажмите кнопку **режима просмотра**, чтобы переключиться между режимом разработки и режимом просмотра.</span><span class="sxs-lookup"><span data-stu-id="180a8-131">Click the **Preview Mode** button to toggle between design-mode and preview-mode.</span></span>

![Снимок экрана конструктора](content/2019-08-01-13-58-27.png)

<span data-ttu-id="180a8-133">Обновленный конструктор позволяет создавать шаблоны и предоставлять примеры данных для предварительного просмотра карточки во время разработки.</span><span class="sxs-lookup"><span data-stu-id="180a8-133">The newly updated Designer adds support for authoring templates and providing **Sample Data** to preview the card at design-time.</span></span>

<span data-ttu-id="180a8-134">Вставьте приведенный ниже пример в область **редактора полезных данных карточки**:</span><span class="sxs-lookup"><span data-stu-id="180a8-134">Paste the example below into the **Card Payload Editor** pane:</span></span> 

<span data-ttu-id="180a8-135">**Файл EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="180a8-135">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "ColumnSet",
            "style": "accent",
            "bleed": true,
            "columns": [
                {
                    "type": "Column",
                    "width": "auto",
                    "items": [
                        {
                            "type": "Image",
                            "url": "{photo}",
                            "altText": "Profile picture",
                            "size": "Small",
                            "style": "Person"
                        }
                    ]
                },
                {
                    "type": "Column",
                    "width": "stretch",
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "Hi {name}!",
                            "size": "Medium"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Here's a bit about your org...",
                            "spacing": "None"
                        }
                    ]
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: **{manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "{peers}",
                    "title": "{name}",
                    "value": "{title}"
                }
            ]
        }
    ]
}
```

<span data-ttu-id="180a8-136">Затем вставьте приведенные ниже данные JSON в **редактор примера данных**.</span><span class="sxs-lookup"><span data-stu-id="180a8-136">Then paste the JSON data below into the **Sample Data Editor**.</span></span> 

<span data-ttu-id="180a8-137">**Добавив пример данных**, вы сможете точно увидеть, как ваша карточка будет выглядеть во время выполнения, когда будут переданы фактические данные.</span><span class="sxs-lookup"><span data-stu-id="180a8-137">**Sample Data** helps you see exactly how your card will appear at runtime when passed actual data.</span></span>

<span data-ttu-id="180a8-138">**Данные о сотрудниках**</span><span class="sxs-lookup"><span data-stu-id="180a8-138">**EmployeeData**</span></span>

```json
{
    "name": "Matt",
    "photo": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
    "manager": {
        "name": "Thomas",
        "title": "PM Lead"
    },
    "peers": [
        {
            "name": "Lei",
            "title": "Sr Program Manager"
        },
        {
            "name": "Andrew",
            "title": "Program Manager II"
        },
        {
            "name": "Mary Anne",
            "title": "Program Manager"
        }
    ]
}
```

<span data-ttu-id="180a8-139">Нажмите кнопку **режима просмотра**.</span><span class="sxs-lookup"><span data-stu-id="180a8-139">Click the **Preview Mode** button.</span></span> <span data-ttu-id="180a8-140">Карточка должна отображаться в соответствии с примером данных, приведенным выше.</span><span class="sxs-lookup"><span data-stu-id="180a8-140">You should see the card render according to the sample data provided above.</span></span> <span data-ttu-id="180a8-141">Вы можете вносить изменения в пример данных и наблюдать за обновлением карточки в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="180a8-141">Feel free to make tweaks to the sample data and watch the card update in realtime.</span></span>

<span data-ttu-id="180a8-142">**Поздравляем**! Вы только что создали свой первый шаблон адаптивной карточки.</span><span class="sxs-lookup"><span data-stu-id="180a8-142">**Congratulations**, you just authored your first Adaptive Card Template!</span></span> <span data-ttu-id="180a8-143">Теперь давайте узнаем, как заполнить шаблон реальными данными.</span><span class="sxs-lookup"><span data-stu-id="180a8-143">Next let's learn how to populate the template with real data.</span></span>

> <span data-ttu-id="180a8-144">Подробнее о [языке шаблонов](language.md).</span><span class="sxs-lookup"><span data-stu-id="180a8-144">Learn more about the [template language](language.md)</span></span>

## <a name="sdk-support"></a><span data-ttu-id="180a8-145">Поддержка пакетов SDK</span><span class="sxs-lookup"><span data-stu-id="180a8-145">SDK support</span></span>

<span data-ttu-id="180a8-146">Пакеты SDK для создания шаблонов позволяют заполнять шаблон реальными данными.</span><span class="sxs-lookup"><span data-stu-id="180a8-146">The Templating SDKs make it possible to populate a template with real-data.</span></span>

> [!NOTE]
>
> <span data-ttu-id="180a8-147">На этапе ознакомительной версии у вас есть только ограниченный набор пакетов SDK.</span><span class="sxs-lookup"><span data-stu-id="180a8-147">During the initial preview we only have a limited set of SDKs available.</span></span> <span data-ttu-id="180a8-148">После выпуска общей версии будут доступны библиотеки шаблонов для каждой поддерживаемой платформы адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="180a8-148">When we release there will be templating libraries for every supported Adaptive Cards platform.</span></span>

<span data-ttu-id="180a8-149">Платформа</span><span class="sxs-lookup"><span data-stu-id="180a8-149">Platform</span></span> | <span data-ttu-id="180a8-150">Установить</span><span class="sxs-lookup"><span data-stu-id="180a8-150">Install</span></span> | <span data-ttu-id="180a8-151">Документация</span><span class="sxs-lookup"><span data-stu-id="180a8-151">Documentation</span></span>
--- | --- | ---
<span data-ttu-id="180a8-152">JavaScript</span><span class="sxs-lookup"><span data-stu-id="180a8-152">JavaScript</span></span> | `npm install adaptivecards-templating` | [<span data-ttu-id="180a8-153">Документация</span><span class="sxs-lookup"><span data-stu-id="180a8-153">Documentation</span></span>](https://www.npmjs.com/package/adaptivecards-templating)
<span data-ttu-id="180a8-154">.NET</span><span class="sxs-lookup"><span data-stu-id="180a8-154">.NET</span></span> | `nuget install AdaptiveCards.Templating` | [<span data-ttu-id="180a8-155">Документация</span><span class="sxs-lookup"><span data-stu-id="180a8-155">Documentation</span></span>](https://docs.microsoft.com/en-us/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a><span data-ttu-id="180a8-156">Пример JavaScript</span><span class="sxs-lookup"><span data-stu-id="180a8-156">JavaScript Example</span></span>

<span data-ttu-id="180a8-157">В приведенном ниже коде JavaScript показан общий шаблон, который будет использоваться для заполнения шаблона данными.</span><span class="sxs-lookup"><span data-stu-id="180a8-157">The JavaScript below shows the general pattern that will be used to populate a template with data.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    // Data goes here
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

> <span data-ttu-id="180a8-158">Подробнее о [пакетах SDK для создания шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="180a8-158">Learn more about the [templating SDKs](sdk.md)</span></span>

## <a name="template-service"></a><span data-ttu-id="180a8-159">Служба шаблонов</span><span class="sxs-lookup"><span data-stu-id="180a8-159">Template Service</span></span>

<span data-ttu-id="180a8-160">Служба шаблонов адаптивных карточек является службой проверки концепции, которая позволяет всем пользователям находить шаблоны, вносить свой вклад и делиться набором известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="180a8-160">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="180a8-161">Она полезна, если вы хотите отобразить некоторые данные, но не хотите писать для них специальную адаптивную карточку.</span><span class="sxs-lookup"><span data-stu-id="180a8-161">It's useful if you want to display some data but don't want to bother writing a custom Adaptive Card for it.</span></span>

<span data-ttu-id="180a8-162">API для получения шаблона достаточно прост, но на самом деле служба предлагает гораздо больше, включая возможность анализа ваших данных и поиска подходящего шаблона.</span><span class="sxs-lookup"><span data-stu-id="180a8-162">The API to get a template is straight-forward enough, but the service actually offers much more, including the ability to analyze your data and find a template that might work for you.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="180a8-163">Все шаблоны представляют собой простые файлы JSON, которые хранятся в репозитории GitHub, поэтому все пользователи могут внести в них свой вклад, как и в любой другой открытый исходный код.</span><span class="sxs-lookup"><span data-stu-id="180a8-163">All templates are flat JSON files stored in a GitHub repo so anyone can contribute to them like any other open source code.</span></span>

> <span data-ttu-id="180a8-164">Подробнее о [службе шаблонов карточек](service.md).</span><span class="sxs-lookup"><span data-stu-id="180a8-164">Learn more about the [card template Service](service.md)</span></span>

## <a name="whats-next-and-sending-feedback"></a><span data-ttu-id="180a8-165">Дальнейшие действия и отправка отзыва</span><span class="sxs-lookup"><span data-stu-id="180a8-165">What's next and sending feedback</span></span>

<span data-ttu-id="180a8-166">Создание шаблонов и отделение представления от данных значительно приближают нас к нашей миссии: "формированию экосистемы для обмена содержимым карточек привычным и согласованным образом".</span><span class="sxs-lookup"><span data-stu-id="180a8-166">Templating and the separation of presentation from data takes us a whole lot closer toward our mission: "an ecosystem for exchanging card content in a common and consistent way".</span></span>

<span data-ttu-id="180a8-167">Мы стремимся выпускать новые возможности как можно скорее.</span><span class="sxs-lookup"><span data-stu-id="180a8-167">We're eager to share more as soon as we can.</span></span> <span data-ttu-id="180a8-168">А пока оставляйте отзывы здесь, на сайте [GitHub](https://github.com/microsoft/AdaptiveCards) или в Twitter **[@MattHidinger](https://twitter.com/matthidinger)** / **#AdaptiveCards**.</span><span class="sxs-lookup"><span data-stu-id="180a8-168">In the meantime please give feedback here, [GitHub](https://github.com/microsoft/AdaptiveCards), or Twitter **[@MattHidinger](https://twitter.com/matthidinger)**/**#AdaptiveCards**.</span></span> 
