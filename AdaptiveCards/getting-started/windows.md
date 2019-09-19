---
title: Адаптивные карточки для разработчиков Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 65494ed437303d26a202c9a5b95f88255147cbd0
ms.sourcegitcommit: 48838a50b5f0316e15b48d740a7dd0a5f96ebae4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70923075"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="cc0d0-102">Адаптивные карточки для разработчиков Windows</span><span class="sxs-lookup"><span data-stu-id="cc0d0-102">Adaptive Cards for Windows Developers</span></span>

## <a name="timeline"></a><span data-ttu-id="cc0d0-103">Информация о сроках</span><span class="sxs-lookup"><span data-stu-id="cc0d0-103">Timeline</span></span>

<span data-ttu-id="cc0d0-104">Поддержка адаптивных карточек в Windows впервые реализована в новой функции "Временная шкала", появившейся в Windows 10 версии 1803.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Информация о сроках](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="cc0d0-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="cc0d0-106">UserActivity API</span></span>

<span data-ttu-id="cc0d0-107">С помощью API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) действия пользователя попадают на временную шкалу.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="cc0d0-108">Адаптивные карточки будут передаваться с помощью свойства `Content` элемента `VisualElement` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="cc0d0-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a><span data-ttu-id="cc0d0-109">Модуль обучения</span><span class="sxs-lookup"><span data-stu-id="cc0d0-109">Learning Module</span></span>

<span data-ttu-id="cc0d0-110">Вот отличный 45-минутный модуль обучения, который полностью охватывает описанные выше шаги.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-110">There is a great 45-min learn module that covers these steps end-to-end.</span></span>

[<span data-ttu-id="cc0d0-111">Интеграция адаптивных карточек во временную шкалу Windows 10</span><span class="sxs-lookup"><span data-stu-id="cc0d0-111">Integrate adaptive cards into Windows 10 Timeline</span></span>](https://docs.microsoft.com/en-us/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a><span data-ttu-id="cc0d0-112">Узнайте больше</span><span class="sxs-lookup"><span data-stu-id="cc0d0-112">Learn more</span></span>

<span data-ttu-id="cc0d0-113">Презентация, представленная на конференции Microsoft Build 2017, подробно описывает действия пользователей.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-113">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="cc0d0-114">Другие функции Windows</span><span class="sxs-lookup"><span data-stu-id="cc0d0-114">Other Windows Surfaces</span></span>
<span data-ttu-id="cc0d0-115">Пока что нам нечего вам предложить, но мы работаем над добавлением адаптивных карточек в другие функции Windows.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-115">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="cc0d0-116">Узнайте больше!</span><span class="sxs-lookup"><span data-stu-id="cc0d0-116">Dive in!</span></span>

<span data-ttu-id="cc0d0-117">В этом руководстве мы предоставили только общие сведения, поэтому почаще проверяйте ссылки ниже, чтобы узнать больше об адаптивных карточках.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-117">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="cc0d0-118">[Ознакомьтесь с примерами адаптивных карточек](http://adaptivecards.io/samples/).</span><span class="sxs-lookup"><span data-stu-id="cc0d0-118">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="cc0d0-119">Воспользуйтесь [обозревателем схемы](http://adaptivecards.io/explorer), чтобы узнать о доступных элементах.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-119">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="cc0d0-120">Создайте адаптивную карточку с помощью [интерактивного визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype).</span><span class="sxs-lookup"><span data-stu-id="cc0d0-120">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="cc0d0-121">[Свяжитесь с нами](http://adaptivecards.io/connect), чтобы оставить свой отзыв.</span><span class="sxs-lookup"><span data-stu-id="cc0d0-121">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
