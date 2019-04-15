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
# <a name="adaptive-cards-for-bot-developers"></a>Адаптивная карты для разработчиков программ-роботов

Адаптивная карты являются прекрасным решением для программ-роботов. Они позволяют создавать карточки один раз, который будет отображаться элегантно внутри нескольких приложений, таких как Microsoft Teams, собственные веб-сайта и многое другое.

> [!NOTE]
> Скайп не поддерживается в текущей предварительной версии. См. в разделе [статус партнера](../resources/partners.md) страницы для последней версии.

## <a name="try-it-out"></a>Попробуйте сами

Щелкните следующую ссылку и [обратиться к наша программа-робот подводному](http://contososcubademo.azurewebsites.net/). Скажем `I'm looking for scuba` и с ее помощью вы забронировать поездку подводному своей мечты.  

Все отклики bot создаются с использованием адаптивного карт.

[![Снимок экрана подводному чата](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Получить код**: полный [Bot подводному Contoso исходный код](https://github.com/matthidinger/ContosoScubaBot
) можно найти на сайте GitHub.


## <a name="bot-framework-integration"></a>Интеграция Bot Framework

С помощью [Bot Framework](https://dev.botframework.com/) можно написать единый программ-роботов, которое сможет чата с пользователями в нескольких «каналы», например Скайп, Microsoft Teams, Facebook Messenger и т. д.

## <a name="walkthrough"></a>Пошаговое руководство

Это довольно проста, добавляемый инструмент Adaptive Cards бота.

### <a name="step-0-start-with-a-basic-message"></a>Шаг 0. Начните с базовых сообщений

Ниже приведен стандартный Bot Framework `message` полезные данные, которые могут доставляться в любом канале и отображения текста для пользователя.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Шаг 1. Добавить инструмент Adaptive Cards `attachment`

Чтобы добавить некоторые полноты больше всего текста, Bot Framework имеет смысл `attachments`. 

Давайте подключить инструмент Adaptive Cards, отображающий текст.

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

### <a name="step-2-build-even-richer-cards"></a>Шаг 2. Создание более широкие возможности карты 

Адаптивная карты предоставляют гораздо больше, чем просто настраиваемых текстовых. 

Можно выполнить следующие действия:  

* Добавление `Images` с вашей карты
* Упорядочивайте свое содержимое с `Containers` и `Columns`
* Добавьте несколько типов `Actions`
* Собирать `Input` от пользователей
* Иметь одну карту `show another card`
* [Извлечь в обозревателе полную схему](http://adaptivecards.io/explorer/)! 

## <a name="platform-sdks"></a>Пакеты SDK для платформы

Если ваш бот разрабатывается на основе .NET и NodeJS у нас есть библиотеки, чтобы сделать построение адаптивной карт еще проще.

Платформа|Установка|Узнайте больше
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Документация .NET Framework программ-роботов](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Bot Framework NodeJS документы](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>Состояние канала

Bot Framework позволяет публиковать бота нескольким каналам. Мы работаем с различных каналов, чтобы обеспечивать полную поддержку адаптивной карты. См. в разделе [статус партнера](../resources/partners.md) страницы для последней версии.


## <a name="dive-in"></a>Погрузитесь!

Мы затронули лишь верхушку рабочей области в этом руководстве, поэтому обратитесь Просмотр по ссылкам ниже, чтобы изучить другие способы, что Адаптивная карты можно повысить бота.

* [Обзор образца карты](http://adaptivecards.io/samples/) вдохновения
* Используйте [обозреватель схем](http://adaptivecards.io/explorer) дополнительные доступные элементы
* Построение карт с помощью [интерактивных визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Связаться с нами](http://adaptivecards.io/connect) с свои отзывы
