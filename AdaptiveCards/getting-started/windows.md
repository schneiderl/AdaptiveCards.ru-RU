---
title: Адаптивные карточки для разработчиков Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 39bdc64ed3244aca68d36c886a9562d964ded217
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "76145394"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="66e24-102">Адаптивные карточки для разработчиков Windows</span><span class="sxs-lookup"><span data-stu-id="66e24-102">Adaptive Cards for Windows Developers</span></span>

## <a name="timeline"></a><span data-ttu-id="66e24-103">Информация о сроках</span><span class="sxs-lookup"><span data-stu-id="66e24-103">Timeline</span></span>

<span data-ttu-id="66e24-104">Поддержка адаптивных карточек в Windows впервые реализована в новой функции "Временная шкала", появившейся в Windows 10 версии 1803.</span><span class="sxs-lookup"><span data-stu-id="66e24-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Информация о сроках](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="66e24-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="66e24-106">UserActivity API</span></span>

<span data-ttu-id="66e24-107">С помощью API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) действия пользователя попадают на временную шкалу.</span><span class="sxs-lookup"><span data-stu-id="66e24-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="66e24-108">Адаптивные карточки будут передаваться с помощью свойства `Content` элемента `VisualElement` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="66e24-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a><span data-ttu-id="66e24-109">Модуль обучения</span><span class="sxs-lookup"><span data-stu-id="66e24-109">Learning Module</span></span>

<span data-ttu-id="66e24-110">Вот отличный 45-минутный модуль обучения, который полностью охватывает описанные выше шаги.</span><span class="sxs-lookup"><span data-stu-id="66e24-110">There is a great 45-min learn module that covers these steps end-to-end.</span></span>

[<span data-ttu-id="66e24-111">Интеграция адаптивных карточек во временную шкалу Windows 10</span><span class="sxs-lookup"><span data-stu-id="66e24-111">Integrate adaptive cards into Windows 10 Timeline</span></span>](https://docs.microsoft.com/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a><span data-ttu-id="66e24-112">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="66e24-112">Learn more</span></span>

<span data-ttu-id="66e24-113">Презентация, представленная на конференции Microsoft Build 2017, подробно описывает действия пользователей.</span><span class="sxs-lookup"><span data-stu-id="66e24-113">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="66e24-114">Другие функции Windows</span><span class="sxs-lookup"><span data-stu-id="66e24-114">Other Windows Surfaces</span></span>
<span data-ttu-id="66e24-115">Пока что нам нечего вам предложить, но мы работаем над добавлением адаптивных карточек в другие функции Windows.</span><span class="sxs-lookup"><span data-stu-id="66e24-115">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="66e24-116">Узнайте больше!</span><span class="sxs-lookup"><span data-stu-id="66e24-116">Dive in!</span></span>

<span data-ttu-id="66e24-117">В этом руководстве мы предоставили только общие сведения, поэтому почаще проверяйте ссылки ниже, чтобы узнать больше об адаптивных карточках.</span><span class="sxs-lookup"><span data-stu-id="66e24-117">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="66e24-118">[Ознакомьтесь с примерами адаптивных карточек](http://adaptivecards.io/samples/).</span><span class="sxs-lookup"><span data-stu-id="66e24-118">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="66e24-119">Воспользуйтесь [обозревателем схемы](http://adaptivecards.io/explorer), чтобы узнать о доступных элементах.</span><span class="sxs-lookup"><span data-stu-id="66e24-119">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="66e24-120">Создайте адаптивную карточку с помощью [интерактивного визуализатора](http://adaptivecards.io/visualizer/index.html?hostApp=Skype).</span><span class="sxs-lookup"><span data-stu-id="66e24-120">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="66e24-121">[Свяжитесь с нами](http://adaptivecards.io/connect), чтобы оставить свой отзыв.</span><span class="sxs-lookup"><span data-stu-id="66e24-121">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
