---
title: Адаптивная карты для разработчиков программ-роботов
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: 1acc30c0347ea5527de2af1fe74e605c7589cbc6
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553286"
---
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="3e583-102">Адаптивная карты для разработчиков программ-роботов</span><span class="sxs-lookup"><span data-stu-id="3e583-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="3e583-103">Адаптивная карты являются прекрасным решением для программ-роботов.</span><span class="sxs-lookup"><span data-stu-id="3e583-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="3e583-104">Они позволяют создавать карточки один раз, который будет отображаться элегантно внутри нескольких приложений, таких как Microsoft Teams, собственные веб-сайта и многое другое.</span><span class="sxs-lookup"><span data-stu-id="3e583-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="3e583-105">Скайп не поддерживается в текущей предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="3e583-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="3e583-106">См. в разделе [статус партнера](../resources/partners.md) страницы для последней версии.</span><span class="sxs-lookup"><span data-stu-id="3e583-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="3e583-107">Попробуйте сами</span><span class="sxs-lookup"><span data-stu-id="3e583-107">Try it out</span></span>

<span data-ttu-id="3e583-108">Щелкните следующую ссылку и [обратиться к наша программа-робот подводному](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="3e583-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="3e583-109">Скажем `I'm looking for scuba` и с ее помощью вы забронировать поездку подводному своей мечты.</span><span class="sxs-lookup"><span data-stu-id="3e583-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="3e583-110">Все отклики bot создаются с использованием адаптивного карт.</span><span class="sxs-lookup"><span data-stu-id="3e583-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="3e583-111">[![Снимок экрана подводному чата](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="3e583-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="3e583-112">**Получить код**: полный [Bot подводному Contoso исходный код](https://github.com/matthidinger/ContosoScubaBot
) можно найти на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="3e583-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="3e583-113">Интеграция Bot Framework</span><span class="sxs-lookup"><span data-stu-id="3e583-113">Bot Framework Integration</span></span>

<span data-ttu-id="3e583-114">С помощью [Bot Framework](https://dev.botframework.com/) можно написать единый программ-роботов, которое сможет чата с пользователями в нескольких «каналы», например Скайп, Microsoft Teams, Facebook Messenger и т. д.</span><span class="sxs-lookup"><span data-stu-id="3e583-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="3e583-115">Пошаговое руководство</span><span class="sxs-lookup"><span data-stu-id="3e583-115">Walkthrough</span></span>

<span data-ttu-id="3e583-116">Это довольно проста, добавляемый инструмент Adaptive Cards бота.</span><span class="sxs-lookup"><span data-stu-id="3e583-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="3e583-117">Шаг 0. Начните с базовых сообщений</span><span class="sxs-lookup"><span data-stu-id="3e583-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="3e583-118">Ниже приведен стандартный Bot Framework `message` полезные данные, которые могут доставляться в любом канале и отображения текста для пользователя.</span><span class="sxs-lookup"><span data-stu-id="3e583-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="3e583-119">Шаг 1. Добавить инструмент Adaptive Cards `attachment`</span><span class="sxs-lookup"><span data-stu-id="3e583-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="3e583-120">Чтобы добавить некоторые полноты больше всего текста, Bot Framework имеет смысл `attachments`.</span><span class="sxs-lookup"><span data-stu-id="3e583-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="3e583-121">Давайте подключить инструмент Adaptive Cards, отображающий текст.</span><span class="sxs-lookup"><span data-stu-id="3e583-121">Let's attach an Adaptive Card that displays custom text.</span></span>

![Основные инструмент adaptive Cards](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="3e583-123">Шаг 2. Создание более широкие возможности карты</span><span class="sxs-lookup"><span data-stu-id="3e583-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="3e583-124">Адаптивная карты предоставляют гораздо больше, чем просто настраиваемых текстовых.</span><span class="sxs-lookup"><span data-stu-id="3e583-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="3e583-125">Можно выполнить следующие действия: </span><span class="sxs-lookup"><span data-stu-id="3e583-125">You can:</span></span> 

* <span data-ttu-id="3e583-126">Добавление `Images` с вашей карты</span><span class="sxs-lookup"><span data-stu-id="3e583-126">Add `Images` to your card</span></span>
* <span data-ttu-id="3e583-127">Упорядочивайте свое содержимое с `Containers` и `Columns`</span><span class="sxs-lookup"><span data-stu-id="3e583-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="3e583-128">Добавьте несколько типов `Actions`</span><span class="sxs-lookup"><span data-stu-id="3e583-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="3e583-129">Собирать `Input` от пользователей</span><span class="sxs-lookup"><span data-stu-id="3e583-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="3e583-130">Иметь одну карту `show another card`</span><span class="sxs-lookup"><span data-stu-id="3e583-130">Have one card `show another card`</span></span>
* <span data-ttu-id="3e583-131">[Извлечь в обозревателе полную схему](http://adaptivecards.io/explorer/)!</span><span class="sxs-lookup"><span data-stu-id="3e583-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="3e583-132">Пакеты SDK для платформы</span><span class="sxs-lookup"><span data-stu-id="3e583-132">Platform SDKs</span></span>

<span data-ttu-id="3e583-133">Если ваш бот разрабатывается на основе .NET и NodeJS у нас есть библиотеки, чтобы сделать построение адаптивной карт еще проще.</span><span class="sxs-lookup"><span data-stu-id="3e583-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="3e583-134">Платформа</span><span class="sxs-lookup"><span data-stu-id="3e583-134">Platform</span></span>|<span data-ttu-id="3e583-135">Установка</span><span class="sxs-lookup"><span data-stu-id="3e583-135">Install</span></span>|<span data-ttu-id="3e583-136">Узнайте больше</span><span class="sxs-lookup"><span data-stu-id="3e583-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="3e583-137">.NET</span><span class="sxs-lookup"><span data-stu-id="3e583-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="3e583-138">Документация .NET Framework программ-роботов</span><span class="sxs-lookup"><span data-stu-id="3e583-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="3e583-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="3e583-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="3e583-140">Bot Framework NodeJS документы</span><span class="sxs-lookup"><span data-stu-id="3e583-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="3e583-141">Состояние канала</span><span class="sxs-lookup"><span data-stu-id="3e583-141">Channel status</span></span>

<span data-ttu-id="3e583-142">Bot Framework позволяет публиковать бота нескольким каналам.</span><span class="sxs-lookup"><span data-stu-id="3e583-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="3e583-143">Мы работаем с различных каналов, чтобы обеспечивать полную поддержку адаптивной карты.</span><span class="sxs-lookup"><span data-stu-id="3e583-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="3e583-144">См. в разделе [статус партнера](../resources/partners.md) страницы для последней версии.</span><span class="sxs-lookup"><span data-stu-id="3e583-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="3e583-145">Погрузитесь!</span><span class="sxs-lookup"><span data-stu-id="3e583-145">Dive in!</span></span>

<span data-ttu-id="3e583-146">Мы затронули лишь верхушку рабочей области в этом руководстве, поэтому обратитесь Просмотр по ссылкам ниже, чтобы изучить другие способы, что Адаптивная карты можно повысить бота.</span><span class="sxs-lookup"><span data-stu-id="3e583-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="3e583-147">[Обзор образца карты](http://adaptivecards.io/samples/) вдохновения</span><span class="sxs-lookup"><span data-stu-id="3e583-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="3e583-148">Используйте [обозреватель схем](http://adaptivecards.io/explorer) дополнительные доступные элементы</span><span class="sxs-lookup"><span data-stu-id="3e583-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="3e583-149">Построение карт с помощью [интерактивных визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="3e583-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="3e583-150">[Связаться с нами](http://adaptivecards.io/connect) с свои отзывы</span><span class="sxs-lookup"><span data-stu-id="3e583-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
