---
title: Общие сведения о создании шаблонов
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 41eb972603b1688a1f1857cec83208b9b55b02c3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417617"
---
# <a name="adaptive-cards-templating"></a><span data-ttu-id="dd6dc-102">Создание шаблонов адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="dd6dc-102">Adaptive Cards Templating</span></span>

<span data-ttu-id="dd6dc-103">Мы рады представить ознакомительную версию новых средств, которые позволяют **создавать** и **повторно использовать** карточки, а также **делиться** ими.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-103">We're excited to share a preview of new tools that will help you **create**, **reuse**, and **share** Adaptive Cards.</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="dd6dc-104">**Критические изменения** в **релиз-кандидате за май 2020 г.**</span><span class="sxs-lookup"><span data-stu-id="dd6dc-104">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="dd6dc-105">Релиз-кандидат для создания шаблонов включает небольшие критические изменения, которые следует учитывать, если вы используете старые пакеты.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-105">The templating release candidate includes some minor breaking changes that you should be aware of if you've been using the older packages.</span></span> <span data-ttu-id="dd6dc-106">Подробности см. ниже.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-106">See below for details.</span></span>


## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="dd6dc-107">Критические изменения в версии за май 2020 г.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-107">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="dd6dc-108">Синтаксис привязки изменен с `{...}` на `${...}`.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-108">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="dd6dc-109">Например, вместо `"text": "Hello {name}"` теперь используется `"text": "Hello ${name}"`.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-109">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="dd6dc-110">API JavaScript больше не содержит объект `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-110">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="dd6dc-111">Просто передайте данные в функцию `expand`.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-111">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="dd6dc-112">Дополнительные сведения см. на [странице с описанием пакета SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dc-112">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="dd6dc-113">Интерфейс API .NET был модернизирован для более точного соответствия API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-113">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="dd6dc-114">Дополнительные сведения см. на [странице о пакете SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dc-114">Please see the [SDK page](sdk.md) for full details.</span></span>

## <a name="how-can-templating-help-you"></a><span data-ttu-id="dd6dc-115">Преимущества создания шаблонов</span><span class="sxs-lookup"><span data-stu-id="dd6dc-115">How can templating help you</span></span>

<span data-ttu-id="dd6dc-116">Путем создания шаблонов вы можете отделить **данные** от **макета** в адаптивной карточке.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-116">Templating enables the separation of **data** from the **layout** in an Adaptive Card.</span></span> 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a><span data-ttu-id="dd6dc-117">Карточку, спроектированную с применением одного средства, можно сразу заполнить реальными данными</span><span class="sxs-lookup"><span data-stu-id="dd6dc-117">It helps design a card once, and then populate it with real data</span></span>

<span data-ttu-id="dd6dc-118">Сегодня невозможно создать карточку с помощью [конструктора адаптивных карточек](https://adaptivecards.io/designer) и использовать этот JSON-файл для наполнения полезных данных **динамическим содержимым**.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-118">Today it's impossible to create a card using the [Adaptive Card Designer](https://adaptivecards.io/designer) and use that JSON to populate the payload with **dynamic content**.</span></span> <span data-ttu-id="dd6dc-119">В таком случае необходимо написать пользовательский код для создания строки JSON или использовать пакет SDK объектной модели для создания объектной модели, представляющей вашу карточку, и сериализовать ее в JSON.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-119">In order to achieve this you must write custom code to build a JSON string, or use the Object Model SDKs to build an OM representing your card and serialize it to JSON.</span></span> <span data-ttu-id="dd6dc-120">В любом случае использование конструктора — это однократная односторонняя операция, которая не позволяет легко настроить дизайн карточки позже, после того как вы преобразовали ее в код.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-120">In either case the Designer is a one-time one-way operation and doesn't make it easy to tweak the card design later once you've converted it to code.</span></span>

### <a name="it-makes-transmissions-over-the-wire-smaller"></a><span data-ttu-id="dd6dc-121">Меньший объем передаваемых по сети данных</span><span class="sxs-lookup"><span data-stu-id="dd6dc-121">It makes transmissions over the wire smaller</span></span>

<span data-ttu-id="dd6dc-122">Представьте себе мир, в котором шаблон и данные можно объединить **непосредственно в клиенте**.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-122">Imagine a world where a template and data can be combined **directly on the client**.</span></span> <span data-ttu-id="dd6dc-123">Это означает, что если вы используете один и тот же шаблон несколько раз или хотите обновить в нем данные, вам просто нужно отправить новые данные на устройство, и оно может повторно применять один и тот же шаблон снова и снова.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-123">This means if you use the same template multiple times, or want to update it with new data, you just need to send new data to the device and it can re-use the same template over and over.</span></span>

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a><span data-ttu-id="dd6dc-124">Возможность создавать великолепные карточки с использованием предоставленных пользователями данных</span><span class="sxs-lookup"><span data-stu-id="dd6dc-124">It helps you create a great looking card from just the data you provide</span></span>

<span data-ttu-id="dd6dc-125">Мы считаем, что адаптивные карточки — это отличная идея, но что если вам бы не приходилось самостоятельно создавать адаптивную карточку для всего, что вы хотите показать пользователю?</span><span class="sxs-lookup"><span data-stu-id="dd6dc-125">We think Adaptive Cards are great, but what if you didn't have to write an Adaptive Card for everything you want to display to a user?</span></span> <span data-ttu-id="dd6dc-126">С помощью службы шаблонов (описанной ниже) мы можем создать среду, в которой каждый сможет добавлять, открывать и публиковать шаблоны с любыми типами данных.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-126">With a template service (described below) we can create a world where everyone can contribute, discover, and share templates over any type of data.</span></span> 

<span data-ttu-id="dd6dc-127">Делитесь шаблонами в своих проектах, вашей организации или со всеми в Интернете.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-127">Share within your own projects, your organization, or with the entire internet.</span></span>

### <a name="ai-and-other-services-could-improve-user-experiences"></a><span data-ttu-id="dd6dc-128">Улучшенное взаимодействие с пользователем благодаря искусственному интеллекту и другим службам</span><span class="sxs-lookup"><span data-stu-id="dd6dc-128">AI and other services could improve user experiences</span></span>

<span data-ttu-id="dd6dc-129">Отделение данных от содержимого открывает возможности использования ИИ и других служб с карточками, повышая эффективность работы пользователей и помогая выполнять поиск.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-129">By separating data from content it opens a door for AI and other services to  "reason" over the data in the cards we see and enhance user productivity or help us find things.</span></span>

## <a name="what-is-adaptive-cards-templating"></a><span data-ttu-id="dd6dc-130">Процесс создания шаблонов адаптивных карточек</span><span class="sxs-lookup"><span data-stu-id="dd6dc-130">What is Adaptive Cards Templating?</span></span>

<span data-ttu-id="dd6dc-131">Этот процесс состоит из 3 основных компонентов:</span><span class="sxs-lookup"><span data-stu-id="dd6dc-131">It's comprised of 3 major components:</span></span>

1. <span data-ttu-id="dd6dc-132">**[Язык шаблонов](language.md)**  — это синтаксис, используемый для создания шаблона.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-132">The **[Template Language](language.md)** is the syntax used for authoring a template.</span></span> <span data-ttu-id="dd6dc-133">Конструктор также позволяет вам просматривать шаблоны во время разработки, добавляя примеры данных.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-133">The Designer even lets you preview your templates at design time by including "sample data".</span></span>
2. <span data-ttu-id="dd6dc-134">**[Пакеты SDK для создания шаблонов](sdk.md)** будут присутствовать на всех поддерживаемых платформах адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-134">The **[Templating SDK's](sdk.md)** will exist on all supported Adaptive Card platforms.</span></span> <span data-ttu-id="dd6dc-135">Эти пакеты SDK позволяют вам заполнять шаблон реальными данными на сервере или непосредственно в клиенте.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-135">These SDKs allow you to populate a template with real data, on the back-end or directly on the client.</span></span> 
3. <span data-ttu-id="dd6dc-136">**[Служба шаблонов](service.md)** является службой проверки концепции, которая позволяет всем пользователям находить шаблоны, вносить свой вклад и делиться набором известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-136">The **[Template Service](service.md)** is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

## <a name="template-language"></a><span data-ttu-id="dd6dc-137">Язык шаблонов</span><span class="sxs-lookup"><span data-stu-id="dd6dc-137">Template Language</span></span>

<span data-ttu-id="dd6dc-138">Язык шаблонов — это синтаксис, используемый для создания шаблона адаптивной карточки.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-138">The template language is the syntax used to author an Adaptive Card template.</span></span> 

> [!NOTE]
> 
> <span data-ttu-id="dd6dc-139">Ознакомьтесь с приведенным ниже примером, открыв новую вкладку со страницей</span><span class="sxs-lookup"><span data-stu-id="dd6dc-139">Follow along with the example below by opening up a new tab to</span></span>
>
> **https://adaptivecards.io/designer**
> 
> <span data-ttu-id="dd6dc-140">Нажмите кнопку **режима просмотра**, чтобы переключиться между режимом разработки и режимом просмотра.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-140">Click the **Preview Mode** button to toggle between design-mode and preview-mode.</span></span>

![Снимок экрана конструктора](content/2019-08-01-13-58-27.png)

<span data-ttu-id="dd6dc-142">Обновленный конструктор позволяет создавать шаблоны и предоставлять **примеры данных** для предварительного просмотра карточки во время разработки.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-142">The newly updated Designer adds support for authoring templates and providing **Sample Data** to preview the card at design-time.</span></span>

<span data-ttu-id="dd6dc-143">Вставьте приведенный ниже пример в область **редактора полезных данных карточки**:</span><span class="sxs-lookup"><span data-stu-id="dd6dc-143">Paste the example below into the **Card Payload Editor** pane:</span></span> 

<span data-ttu-id="dd6dc-144">**Файл EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="dd6dc-144">**EmployeeCardTemplate.json**</span></span>

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
                            "url": "${photo}",
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
                            "text": "Hi ${name}!",
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
            "text": "Your manager is: **${manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "${peers}",
                    "title": "${name}",
                    "value": "${title}"
                }
            ]
        }
    ]
}
```

<span data-ttu-id="dd6dc-145">Затем вставьте приведенные ниже данные JSON в **редактор примера данных**.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-145">Then paste the JSON data below into the **Sample Data Editor**.</span></span> 

<span data-ttu-id="dd6dc-146">**Добавив пример данных**, вы сможете точно увидеть, как ваша карточка будет выглядеть во время выполнения, когда будут переданы фактические данные.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-146">**Sample Data** helps you see exactly how your card will appear at runtime when passed actual data.</span></span>

<span data-ttu-id="dd6dc-147">**Данные о сотрудниках**</span><span class="sxs-lookup"><span data-stu-id="dd6dc-147">**EmployeeData**</span></span>

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

<span data-ttu-id="dd6dc-148">Нажмите кнопку **режима просмотра**.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-148">Click the **Preview Mode** button.</span></span> <span data-ttu-id="dd6dc-149">Карточка должна отображаться в соответствии с примером данных, приведенным выше.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-149">You should see the card render according to the sample data provided above.</span></span> <span data-ttu-id="dd6dc-150">Вы можете вносить изменения в пример данных и наблюдать за обновлением карточки в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-150">Feel free to make tweaks to the sample data and watch the card update in realtime.</span></span>

<span data-ttu-id="dd6dc-151">**Поздравляем**! Вы только что создали свой первый шаблон адаптивной карточки.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-151">**Congratulations**, you just authored your first Adaptive Card Template!</span></span> <span data-ttu-id="dd6dc-152">Теперь давайте узнаем, как заполнить шаблон реальными данными.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-152">Next let's learn how to populate the template with real data.</span></span>

> <span data-ttu-id="dd6dc-153">Подробнее о [языке шаблонов](language.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dc-153">Learn more about the [template language](language.md)</span></span>

## <a name="sdk-support"></a><span data-ttu-id="dd6dc-154">Поддержка пакетов SDK</span><span class="sxs-lookup"><span data-stu-id="dd6dc-154">SDK support</span></span>

<span data-ttu-id="dd6dc-155">Пакеты SDK для создания шаблонов позволяют заполнять шаблон реальными данными.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-155">The Templating SDKs make it possible to populate a template with real-data.</span></span>

> [!NOTE]
>
> <span data-ttu-id="dd6dc-156">Сейчас для .NET и NodeJS доступны пакеты SDK для создания шаблонов.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-156">At this time templating SDKs are available for .NET and NodeJS.</span></span> <span data-ttu-id="dd6dc-157">В перспективе мы намерены выпускать такие пакеты SDK для всех неохваченных платформ адаптивных карточек, таких как iOS, Android, UWP и т. д.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-157">Over time we will release templating SDKs for all remaining Adaptive Cards platform, like iOS, Android, UWP, etc.</span></span>

<span data-ttu-id="dd6dc-158">Платформа</span><span class="sxs-lookup"><span data-stu-id="dd6dc-158">Platform</span></span> | <span data-ttu-id="dd6dc-159">Пакет</span><span class="sxs-lookup"><span data-stu-id="dd6dc-159">Package</span></span> | <span data-ttu-id="dd6dc-160">Установить</span><span class="sxs-lookup"><span data-stu-id="dd6dc-160">Install</span></span> | <span data-ttu-id="dd6dc-161">Документация</span><span class="sxs-lookup"><span data-stu-id="dd6dc-161">Documentation</span></span>
--- | --- | --- | ---
<span data-ttu-id="dd6dc-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="dd6dc-162">JavaScript</span></span> | <span data-ttu-id="dd6dc-163">[![Установка с помощью npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="dd6dc-163">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span> | `npm install adaptivecards-templating` | [<span data-ttu-id="dd6dc-164">Документация</span><span class="sxs-lookup"><span data-stu-id="dd6dc-164">Documentation</span></span>](https://www.npmjs.com/package/adaptivecards-templating)
<span data-ttu-id="dd6dc-165">.NET</span><span class="sxs-lookup"><span data-stu-id="dd6dc-165">.NET</span></span> | <span data-ttu-id="dd6dc-166">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="dd6dc-166">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span> | `dotnet add package AdaptiveCards.Templating` | [<span data-ttu-id="dd6dc-167">Документация</span><span class="sxs-lookup"><span data-stu-id="dd6dc-167">Documentation</span></span>](https://docs.microsoft.com/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a><span data-ttu-id="dd6dc-168">Пример JavaScript</span><span class="sxs-lookup"><span data-stu-id="dd6dc-168">JavaScript Example</span></span>

<span data-ttu-id="dd6dc-169">В приведенном ниже коде JavaScript показан общий шаблон, который будет использоваться для заполнения шаблона данными.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-169">The JavaScript below shows the general pattern that will be used to populate a template with data.</span></span>

```js
var template = new ACData.Template({ 
    // Card Template JSON
});

var card = template.expand({
    $root: {
        // Data Fields
    }
});

// Now you have an AdaptiveCard ready to render!
```

### <a name="c-example"></a><span data-ttu-id="dd6dc-170">Пример для C#</span><span class="sxs-lookup"><span data-stu-id="dd6dc-170">C# Example</span></span>

<span data-ttu-id="dd6dc-171">В приведенном ниже коде на C# показан общий шаблон, который будет использоваться для заполнения шаблона данными.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-171">The C# below shows the general pattern that will be used to populate a template with data.</span></span>

```csharp
var template = new AdaptiveCards.Templating.AdaptiveCardTemplate(cardJson);
   
var card = template.Expand(new {Key="Value"});

// Now you have an AdaptiveCard ready to render!
```

> <span data-ttu-id="dd6dc-172">Подробнее о [пакетах SDK для создания шаблонов](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dc-172">Learn more about the [templating SDKs](sdk.md)</span></span>

## <a name="template-service"></a><span data-ttu-id="dd6dc-173">Служба шаблонов</span><span class="sxs-lookup"><span data-stu-id="dd6dc-173">Template Service</span></span>

<span data-ttu-id="dd6dc-174">Служба шаблонов адаптивных карточек является службой проверки концепции, которая позволяет всем пользователям находить шаблоны, вносить свой вклад и делиться набором известных шаблонов.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-174">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="dd6dc-175">Она полезна, если вы хотите отобразить некоторые данные, но не хотите писать для них специальную адаптивную карточку.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-175">It's useful if you want to display some data but don't want to bother writing a custom Adaptive Card for it.</span></span>

<span data-ttu-id="dd6dc-176">API для получения шаблона достаточно прост, но на самом деле служба предлагает гораздо больше, включая возможность анализа ваших данных и поиска подходящего шаблона.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-176">The API to get a template is straight-forward enough, but the service actually offers much more, including the ability to analyze your data and find a template that might work for you.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="dd6dc-177">Все шаблоны представляют собой простые файлы JSON, которые хранятся в репозитории GitHub, поэтому все пользователи могут внести в них свой вклад, как и в любой другой открытый исходный код.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-177">All templates are flat JSON files stored in a GitHub repo so anyone can contribute to them like any other open source code.</span></span>

> <span data-ttu-id="dd6dc-178">Подробнее о [службе шаблонов карточек](service.md).</span><span class="sxs-lookup"><span data-stu-id="dd6dc-178">Learn more about the [card template Service](service.md)</span></span>

## <a name="whats-next-and-sending-feedback"></a><span data-ttu-id="dd6dc-179">Дальнейшие действия и отправка отзыва</span><span class="sxs-lookup"><span data-stu-id="dd6dc-179">What's next and sending feedback</span></span>

<span data-ttu-id="dd6dc-180">Создание шаблонов и отделение представления от данных значительно приближают нас к нашей миссии, то есть стандартизированной экосистеме для обмена содержимым между приложениями и службами.</span><span class="sxs-lookup"><span data-stu-id="dd6dc-180">Templating and the separation of presentation from data takes us a whole lot closer toward our mission: "an ecosystem standardized content exchange between apps and services".</span></span> <span data-ttu-id="dd6dc-181">У нас есть много интересного в этой сфере, так что оставайтесь в курсе и сообщите нам на [GitHub](https://github.com/Microsoft/AdaptiveCards/issues), как все работает!</span><span class="sxs-lookup"><span data-stu-id="dd6dc-181">We've got plenty to deliver in this area, so stay tuned and let us know how it's working for you on [GitHub](https://github.com/Microsoft/AdaptiveCards/issues)!</span></span>
