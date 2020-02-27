---
title: Дорожная карта адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454897"
---
# <a name="future-work"></a><span data-ttu-id="e4a5f-102">Предстоящая работа</span><span class="sxs-lookup"><span data-stu-id="e4a5f-102">Future work</span></span>

<span data-ttu-id="e4a5f-103">Хотя мы проделали отличную работу по определению адаптивных карточек, работы еще хватает.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="e4a5f-104">Мы надеемся, что с помощью активных сообществ разработчиков, таких как botness, и отличных партнеров, таких как Slack и Kik, мы сможем сформировать эффективную экосистему кроссплатформенных карточек.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="e4a5f-105">Стратегия</span><span class="sxs-lookup"><span data-stu-id="e4a5f-105">Roadmap</span></span>

<span data-ttu-id="e4a5f-106">Текущую (неокончательную) дорожную карту можно просмотреть [здесь](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="e4a5f-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="e4a5f-107">Имейте ввиду, что все, что в ней указано, не является окончательным, может быть изменено и не обязательно будет поставляться.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="e4a5f-108">Будущие идеи</span><span class="sxs-lookup"><span data-stu-id="e4a5f-108">Future ideas</span></span>

<span data-ttu-id="e4a5f-109">Ниже приведены некоторые будущие идеи, которые пока находятся на стадии мозгового штурма.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="e4a5f-110">Если вас заинтересует какая-либо из них, сообщите нам об этом в комментарии.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="e4a5f-111">Привлекательные карточки с данными</span><span class="sxs-lookup"><span data-stu-id="e4a5f-111">Great looking Cards from Data</span></span>

<span data-ttu-id="e4a5f-112">Мы понимаем, что многие разработчики карточек уже имеют четко определенные данные, на основе которых созданы карточки.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="e4a5f-113">Наш план заключается в изучении шаблонной модели, которая позволит создавать карточки (на стороне сервера или клиента) на основе данных и репозитория четко определенных и настраиваемых шаблонов.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="e4a5f-114">Создание реагирующих карточек</span><span class="sxs-lookup"><span data-stu-id="e4a5f-114">Make cards responsive</span></span>

<span data-ttu-id="e4a5f-115">Макеты карточек должны динамично реагировать на свободное место.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="e4a5f-116">Адаптивные карточки можно адаптировать к различным устройствам, стилям взаимодействия с пользователем и платформам пользовательского интерфейса, но они еще не являются реагирующими.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="e4a5f-117">Нужно определить дополнительные свойства для элементов, которые позволят производителям карточек предоставлять необходимые указания в библиотеках отрисовки, чтобы они могли интеллектуально изменять макет таким образом, чтобы выполнялась цель карточки.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="e4a5f-118">Изучение с откликом</span><span class="sxs-lookup"><span data-stu-id="e4a5f-118">Responsive exploration</span></span>

* <span data-ttu-id="e4a5f-119">Добавьте свойство **importance**, которое обозначает важность содержимого.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="e4a5f-120">Можно удалить менее важное содержимое, чтобы вместить карточку в доступном пространстве.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="e4a5f-121">Добавьте свойства **constraints** и **policy**, описывающие, как следует реагировать, если ограничения не могут быть выполнены.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="e4a5f-122">Скрывайте или сворачивайте содержимое, чтобы уменьшить размер карточки.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="e4a5f-123">Добавьте пороговое значение, при превышении которого `columnSet` превращается в карусель столбцов.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="e4a5f-124">Новые типы элементов</span><span class="sxs-lookup"><span data-stu-id="e4a5f-124">New element types</span></span>

* <span data-ttu-id="e4a5f-125">Карты?</span><span class="sxs-lookup"><span data-stu-id="e4a5f-125">Maps?</span></span> <span data-ttu-id="e4a5f-126">Внедрите карту в интерактивную карточку или отобразите точечный рисунок, если карточка не поддерживает подобное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="e4a5f-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="e4a5f-127">*Какие элементы вам нужны*?</span><span class="sxs-lookup"><span data-stu-id="e4a5f-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="e4a5f-128">Новые библиотеки отрисовки</span><span class="sxs-lookup"><span data-stu-id="e4a5f-128">New rendering libraries</span></span>

* <span data-ttu-id="e4a5f-129">React?</span><span class="sxs-lookup"><span data-stu-id="e4a5f-129">React?</span></span>
* <span data-ttu-id="e4a5f-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="e4a5f-130">Xamarin?</span></span>
* <span data-ttu-id="e4a5f-131">*Какие платформы вам нужны?*</span><span class="sxs-lookup"><span data-stu-id="e4a5f-131">*What frameworks do you want?*</span></span>
