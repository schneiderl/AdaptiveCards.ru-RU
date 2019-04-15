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
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="b77b3-102">Адаптивная карты для разработчиков Windows</span><span class="sxs-lookup"><span data-stu-id="b77b3-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="b77b3-103">Информация о сроках</span><span class="sxs-lookup"><span data-stu-id="b77b3-103">Timeline</span></span>

<span data-ttu-id="b77b3-104">Первый Windows опыта поддерживает адаптивной карты является временной шкалы, совершенно новые возможности появились в Windows 10 версии 1803.</span><span class="sxs-lookup"><span data-stu-id="b77b3-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Информация о сроках](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="b77b3-106">UserActivity API</span><span class="sxs-lookup"><span data-stu-id="b77b3-106">UserActivity API</span></span>

<span data-ttu-id="b77b3-107">[ `Windows.ApplicationModel.UserActivities.UserActivity` ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API является то, что заполняет действия на временной шкале.</span><span class="sxs-lookup"><span data-stu-id="b77b3-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="b77b3-108">Инструмент Adaptive cards. будут предоставлены через `Content` свойство `VisualElement`, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b77b3-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="b77b3-109">Узнайте больше</span><span class="sxs-lookup"><span data-stu-id="b77b3-109">Learn more</span></span>

<span data-ttu-id="b77b3-110">Этот сеанс конференции Build 2017 включают в себя действия пользователя за detial.</span><span class="sxs-lookup"><span data-stu-id="b77b3-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="b77b3-111">Другие поверхности Windows</span><span class="sxs-lookup"><span data-stu-id="b77b3-111">Other Windows Surfaces</span></span>
<span data-ttu-id="b77b3-112">У нас нет ничего, пока просто, но мы работаем над Включение адаптивной карты в дополнительные возможности Windows.</span><span class="sxs-lookup"><span data-stu-id="b77b3-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="b77b3-113">Погрузитесь!</span><span class="sxs-lookup"><span data-stu-id="b77b3-113">Dive in!</span></span>

<span data-ttu-id="b77b3-114">Мы едва набросал в этом руководстве, поэтому зайдите позже и воспользуйтесь ссылками ниже, чтобы узнать дополнительные сведения об адаптивной карты.</span><span class="sxs-lookup"><span data-stu-id="b77b3-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="b77b3-115">[Обзор образца карты](http://adaptivecards.io/samples/) вдохновения</span><span class="sxs-lookup"><span data-stu-id="b77b3-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="b77b3-116">Используйте [обозреватель схем](http://adaptivecards.io/explorer) дополнительные доступные элементы</span><span class="sxs-lookup"><span data-stu-id="b77b3-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="b77b3-117">Построение карт с помощью [интерактивных визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="b77b3-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="b77b3-118">[Связаться с нами](http://adaptivecards.io/connect) с свои отзывы</span><span class="sxs-lookup"><span data-stu-id="b77b3-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
