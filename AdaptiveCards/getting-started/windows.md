---
title: Адаптивные карточки для разработчиков Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 39bdc64ed3244aca68d36c886a9562d964ded217
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145394"
---
# <a name="adaptive-cards-for-windows-developers"></a>Адаптивные карточки для разработчиков Windows

## <a name="timeline"></a>Информация о сроках

Поддержка адаптивных карточек в Windows впервые реализована в новой функции "Временная шкала", появившейся в Windows 10 версии 1803. 

![Информация о сроках](media/windows/timeline.png)

### <a name="useractivity-api"></a>API UserActivity

С помощью API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) действия пользователя попадают на временную шкалу.

Адаптивные карточки будут передаваться с помощью свойства `Content` элемента `VisualElement` следующим образом:

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a>Модуль обучения

Вот отличный 45-минутный модуль обучения, который полностью охватывает описанные выше шаги.

[Интеграция адаптивных карточек во временную шкалу Windows 10](https://docs.microsoft.com/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a>Дополнительные сведения

Презентация, представленная на конференции Microsoft Build 2017, подробно описывает действия пользователей.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Другие функции Windows
Пока что нам нечего вам предложить, но мы работаем над добавлением адаптивных карточек в другие функции Windows.

## <a name="dive-in"></a>Узнайте больше!

В этом руководстве мы предоставили только общие сведения, поэтому почаще проверяйте ссылки ниже, чтобы узнать больше об адаптивных карточках.

* [Ознакомьтесь с примерами адаптивных карточек](http://adaptivecards.io/samples/).
* Воспользуйтесь [обозревателем схемы](http://adaptivecards.io/explorer), чтобы узнать о доступных элементах.
* Создайте адаптивную карточку с помощью [интерактивного визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype).
* [Свяжитесь с нами](http://adaptivecards.io/connect), чтобы оставить свой отзыв.
