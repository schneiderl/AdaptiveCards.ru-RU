---
title: Адаптивная карты для разработчиков Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 20b324c12cd7cec10f2142fc2cf76039b5c329de
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552856"
---
# <a name="adaptive-cards-for-windows-developers"></a>Адаптивная карты для разработчиков Windows



## <a name="timeline"></a>Информация о сроках

Первый Windows опыта поддерживает адаптивной карты является временной шкалы, совершенно новые возможности появились в Windows 10 версии 1803. 

![Информация о сроках](media/windows/timeline.png)

### <a name="useractivity-api"></a>UserActivity API

[ `Windows.ApplicationModel.UserActivities.UserActivity` ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API является то, что заполняет действия на временной шкале.

Инструмент Adaptive cards. будут предоставлены через `Content` свойство `VisualElement`, как показано ниже:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>Узнайте больше

Этот сеанс конференции Build 2017 включают в себя действия пользователя за detial.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Другие поверхности Windows
У нас нет ничего, пока просто, но мы работаем над Включение адаптивной карты в дополнительные возможности Windows.

## <a name="dive-in"></a>Погрузитесь!

Мы едва набросал в этом руководстве, поэтому зайдите позже и воспользуйтесь ссылками ниже, чтобы узнать дополнительные сведения об адаптивной карты.

* [Обзор образца карты](http://adaptivecards.io/samples/) вдохновения
* Используйте [обозреватель схем](http://adaptivecards.io/explorer) дополнительные доступные элементы
* Построение карт с помощью [интерактивных визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Связаться с нами](http://adaptivecards.io/connect) с свои отзывы
