---
title: Адаптивные карточки для разработчиков ботов
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: 1acc30c0347ea5527de2af1fe74e605c7589cbc6
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "59553286"
---
# <a name="adaptive-cards-for-bot-developers"></a>Адаптивные карточки для разработчиков ботов

Адаптивные карточки отлично подходят для использования в ботах. Карточку можно создать один раз, после чего использовать ее на разных платформах, включая Microsoft Teams или свой веб-сайт и т. п.

> [!NOTE]
> В текущей предварительной версии Skype не поддерживается. Новости см. на странице со сведениями о [поддерживаемых платформах](../resources/partners.md).

## <a name="try-it-out"></a>Попробуйте сами

[Перейдите по этой ссылке и пообщайтесь с нашим ботом-аквалангистом](http://contososcubademo.azurewebsites.net/). Скажите ему: `I'm looking for scuba`, и он поможет вам заказать дайвинг-тур.  

Все ответы бота созданы с использованием адаптивных карточек.

[![Снимок экрана с чатом о подводном плавании](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Скачайте код**. Полная версия [исходного кода бота-аквалангиста Contoso](https://github.com/matthidinger/ContosoScubaBot
) доступна на сайте GitHub.


## <a name="bot-framework-integration"></a>Интеграция с Bot Framework

[Bot Framework](https://dev.botframework.com/) позволяет создать бота для общения с пользователями, используя различные каналы коммуникации, такие как Skype, Microsoft Teams, Facebook Messenger и т. д.

## <a name="walkthrough"></a>Пошаговое руководство

Добавить адаптивную карточку в бота довольно просто.

### <a name="step-0-start-with-a-basic-message"></a>Шаг 0. Начните с главного сообщения

Ниже приведены стандартные полезные данные `message` в Bot Framework, которые можно доставить пользователю по любому каналу коммуникации.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Шаг 1. Добавьте адаптивную карточку в виде `attachment`

Чтобы разнообразить сообщение, в Bot Framework реализована концепция `attachments`. 

Давайте добавим в сообщение адаптивную карточку, отображающую заданный текст.

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

### <a name="step-2-build-even-richer-cards"></a>Шаг 2. Создайте расширенную карточку 

Адаптивные карточки обеспечивают гораздо больше возможностей, чем отображение текста с заданным форматированием. 

Можно сделать следующее. 

* добавлять в карточку `Images`;
* упорядочивать содержимое с помощью `Containers` и `Columns`;
* добавлять разные типы `Actions`;
* собирать `Input`, предоставляемые пользователями;
* выполнять в карточке действие `show another card`.
* [Ознакомьтесь с исчерпывающим обозревателем схемы](http://adaptivecards.io/explorer/). 

## <a name="platform-sdks"></a>Пакеты SDK для платформ

Если ваш бот создан с помощью .NET или NodeJS, вы можете воспользоваться библиотеками, упрощающими создание адаптивных карточек.

Платформа|Установка|Узнайте больше
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Документация по .NET Framework для Bot Framework](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Документация по NodeJS для Bot Framework](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>Поддержка каналов коммуникации

Bot Framework позволяет публиковать бота в нескольких каналах. Мы работаем над тем, чтобы обеспечить полную поддержку адаптивных карточек в разных каналах коммуникации. Новости см. на странице со сведениями о [поддерживаемых платформах](../resources/partners.md).


## <a name="dive-in"></a>Узнайте больше!

В этом руководстве мы предоставили только общие сведения, поэтому почаще проверяйте ссылки ниже, чтобы узнать о том, как можно улучшить ботов с помощью адаптивных карточек.

* [Ознакомьтесь с примерами адаптивных карточек](http://adaptivecards.io/samples/).
* Воспользуйтесь [обозревателем схемы](http://adaptivecards.io/explorer), чтобы узнать о доступных элементах.
* Создайте адаптивную карточку с помощью [интерактивного визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype).
* [Свяжитесь с нами](http://adaptivecards.io/connect), чтобы оставить свой отзыв.
