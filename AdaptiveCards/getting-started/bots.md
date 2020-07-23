---
title: Адаптивные карточки для разработчиков ботов
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: e460bf50cdb4f0c1af54f5c7ad6c1d02db9af746
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417501"
---
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="f534c-102">Адаптивные карточки для разработчиков ботов</span><span class="sxs-lookup"><span data-stu-id="f534c-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="f534c-103">Адаптивные карточки отлично подходят для использования в ботах.</span><span class="sxs-lookup"><span data-stu-id="f534c-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="f534c-104">Карточку можно создать один раз, после чего использовать ее на разных платформах, включая Microsoft Teams или свой веб-сайт и т. п.</span><span class="sxs-lookup"><span data-stu-id="f534c-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="f534c-105">В текущей предварительной версии Skype не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f534c-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="f534c-106">Новости см. на странице со сведениями о [поддерживаемых платформах](../resources/partners.md).</span><span class="sxs-lookup"><span data-stu-id="f534c-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="f534c-107">Пробное использование</span><span class="sxs-lookup"><span data-stu-id="f534c-107">Try it out</span></span>

<span data-ttu-id="f534c-108">[Перейдите по этой ссылке и пообщайтесь с нашим ботом-аквалангистом](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="f534c-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="f534c-109">Скажите ему: `I'm looking for scuba`, и он поможет вам заказать дайвинг-тур.</span><span class="sxs-lookup"><span data-stu-id="f534c-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="f534c-110">Все ответы бота созданы с использованием адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="f534c-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="f534c-111">[![Снимок экрана с чатом о подводном плавании](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="f534c-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="f534c-112">**Скачайте код**. Полная версия [исходного кода бота-аквалангиста Contoso](https://github.com/matthidinger/ContosoScubaBot
) доступна на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="f534c-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="f534c-113">Интеграция с Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f534c-113">Bot Framework Integration</span></span>

<span data-ttu-id="f534c-114">[Bot Framework](https://dev.botframework.com/) позволяет создать бота для общения с пользователями, используя различные каналы коммуникации, такие как Skype, Microsoft Teams, Facebook Messenger и т. д.</span><span class="sxs-lookup"><span data-stu-id="f534c-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="f534c-115">Пошаговое руководство</span><span class="sxs-lookup"><span data-stu-id="f534c-115">Walkthrough</span></span>

<span data-ttu-id="f534c-116">Добавить адаптивную карточку в бота довольно просто.</span><span class="sxs-lookup"><span data-stu-id="f534c-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="f534c-117">Шаг 0. Начните с главного сообщения</span><span class="sxs-lookup"><span data-stu-id="f534c-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="f534c-118">Ниже приведены стандартные полезные данные `message` в Bot Framework, которые можно доставить пользователю по любому каналу коммуникации.</span><span class="sxs-lookup"><span data-stu-id="f534c-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="f534c-119">Шаг 1. Добавьте адаптивную карточку в виде `attachment`</span><span class="sxs-lookup"><span data-stu-id="f534c-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="f534c-120">Чтобы разнообразить сообщение, в Bot Framework реализована концепция `attachments`.</span><span class="sxs-lookup"><span data-stu-id="f534c-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="f534c-121">Давайте добавим в сообщение адаптивную карточку, отображающую заданный текст.</span><span class="sxs-lookup"><span data-stu-id="f534c-121">Let's attach an Adaptive Card that displays custom text.</span></span>

![Простая адаптивная карточка](media/bots/hello-adaptivecards.png)

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="f534c-123">Шаг 2. Создайте расширенную карточку</span><span class="sxs-lookup"><span data-stu-id="f534c-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="f534c-124">Адаптивные карточки обеспечивают гораздо больше возможностей, чем отображение текста с заданным форматированием.</span><span class="sxs-lookup"><span data-stu-id="f534c-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="f534c-125">Можно сделать следующее.</span><span class="sxs-lookup"><span data-stu-id="f534c-125">You can:</span></span> 

* <span data-ttu-id="f534c-126">добавлять в карточку `Images`;</span><span class="sxs-lookup"><span data-stu-id="f534c-126">Add `Images` to your card</span></span>
* <span data-ttu-id="f534c-127">упорядочивать содержимое с помощью `Containers` и `Columns`;</span><span class="sxs-lookup"><span data-stu-id="f534c-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="f534c-128">добавлять разные типы `Actions`;</span><span class="sxs-lookup"><span data-stu-id="f534c-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="f534c-129">собирать `Input`, предоставляемые пользователями;</span><span class="sxs-lookup"><span data-stu-id="f534c-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="f534c-130">выполнять в карточке действие `show another card`.</span><span class="sxs-lookup"><span data-stu-id="f534c-130">Have one card `show another card`</span></span>
* <span data-ttu-id="f534c-131">[Ознакомьтесь с исчерпывающим обозревателем схемы](https://adaptivecards.io/explorer/).</span><span class="sxs-lookup"><span data-stu-id="f534c-131">[Check out the full schema explorer](https://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="f534c-132">Пакеты SDK для платформ</span><span class="sxs-lookup"><span data-stu-id="f534c-132">Platform SDKs</span></span>

<span data-ttu-id="f534c-133">Если ваш бот создан с помощью .NET или NodeJS, вы можете воспользоваться библиотеками, упрощающими создание адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="f534c-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="f534c-134">Платформа</span><span class="sxs-lookup"><span data-stu-id="f534c-134">Platform</span></span>|<span data-ttu-id="f534c-135">Установить</span><span class="sxs-lookup"><span data-stu-id="f534c-135">Install</span></span>|<span data-ttu-id="f534c-136">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="f534c-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="f534c-137">.NET</span><span class="sxs-lookup"><span data-stu-id="f534c-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="f534c-138">Документация по .NET Framework для Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f534c-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="f534c-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="f534c-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="f534c-140">Документация по NodeJS для Bot Framework</span><span class="sxs-lookup"><span data-stu-id="f534c-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="f534c-141">Поддержка каналов коммуникации</span><span class="sxs-lookup"><span data-stu-id="f534c-141">Channel status</span></span>

<span data-ttu-id="f534c-142">Bot Framework позволяет публиковать бота в нескольких каналах.</span><span class="sxs-lookup"><span data-stu-id="f534c-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="f534c-143">Мы работаем над тем, чтобы обеспечить полную поддержку адаптивных карточек в разных каналах коммуникации.</span><span class="sxs-lookup"><span data-stu-id="f534c-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="f534c-144">Новости см. на странице со сведениями о [поддерживаемых платформах](../resources/partners.md).</span><span class="sxs-lookup"><span data-stu-id="f534c-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="f534c-145">Узнайте больше!</span><span class="sxs-lookup"><span data-stu-id="f534c-145">Dive in!</span></span>

<span data-ttu-id="f534c-146">В этом руководстве мы предоставили только общие сведения, поэтому почаще проверяйте ссылки ниже, чтобы узнать о том, как можно улучшить ботов с помощью адаптивных карточек.</span><span class="sxs-lookup"><span data-stu-id="f534c-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="f534c-147">[Ознакомьтесь с примерами адаптивных карточек](https://adaptivecards.io/samples/).</span><span class="sxs-lookup"><span data-stu-id="f534c-147">[Browse Sample cards](https://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="f534c-148">Воспользуйтесь [обозревателем схемы](https://adaptivecards.io/explorer), чтобы узнать о доступных элементах.</span><span class="sxs-lookup"><span data-stu-id="f534c-148">Use the [Schema Explorer](https://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="f534c-149">Создайте адаптивную карточку с помощью [интерактивного визуализатора](https://adaptivecards.io/visualizer/index.html?hostApp=Skype).</span><span class="sxs-lookup"><span data-stu-id="f534c-149">Build a card using the [Interactive Visualizer](https://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="f534c-150">[Свяжитесь с нами](https://adaptivecards.io/connect), чтобы оставить свой отзыв.</span><span class="sxs-lookup"><span data-stu-id="f534c-150">[Get in touch](https://adaptivecards.io/connect) with any feedback you have</span></span>
