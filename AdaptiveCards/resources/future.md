---
title: Стратегия развития адаптивной карты
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138007"
---
# <a name="future-work"></a><span data-ttu-id="ea84d-102">Дальнейшей работы</span><span class="sxs-lookup"><span data-stu-id="ea84d-102">Future work</span></span>

<span data-ttu-id="ea84d-103">Хотя мы внесли отличную хода выполнения, определение адаптивной карты, по-прежнему много работы.</span><span class="sxs-lookup"><span data-stu-id="ea84d-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="ea84d-104">Мы надеемся является, через сообщества разработчиков active botness и отлично партнеров, как Slack и Kik, можно создать отличные экосистемы кросс платформенных карт.</span><span class="sxs-lookup"><span data-stu-id="ea84d-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="ea84d-105">Стратегия</span><span class="sxs-lookup"><span data-stu-id="ea84d-105">Roadmap</span></span>

<span data-ttu-id="ea84d-106">Вы увидите наших [текущий план (неконечного) здесь](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="ea84d-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="ea84d-107">Обратите внимание, что-то в данной статье, может быть изменена что это значение не гарантирует доставку.</span><span class="sxs-lookup"><span data-stu-id="ea84d-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="ea84d-108">Будущие идеи</span><span class="sxs-lookup"><span data-stu-id="ea84d-108">Future ideas</span></span>

<span data-ttu-id="ea84d-109">Ниже приведены некоторые будущих идеи, которые у нас есть, которые являются просто стадии мозговой.</span><span class="sxs-lookup"><span data-stu-id="ea84d-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="ea84d-110">Если вы заинтересованы в любой из них, сообщите об этом в комментарии.</span><span class="sxs-lookup"><span data-stu-id="ea84d-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="ea84d-111">Отличный выглядящие карты на основе данных</span><span class="sxs-lookup"><span data-stu-id="ea84d-111">Great looking Cards from Data</span></span>

<span data-ttu-id="ea84d-112">Мы знаем, многие авторы карты еще нет четко определенных данных карты.</span><span class="sxs-lookup"><span data-stu-id="ea84d-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="ea84d-113">Наш план является исследование модель шаблонов, которая позволила бы карты для создаваемого (на стороне сервера или на стороне клиента) на основе данных и репозиторием четко определенных и настраиваемых шаблонов.</span><span class="sxs-lookup"><span data-stu-id="ea84d-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="ea84d-114">Создание быстро реагирующих карточек</span><span class="sxs-lookup"><span data-stu-id="ea84d-114">Make cards responsive</span></span>

<span data-ttu-id="ea84d-115">Макеты карт следует за событиями доступное пространство.</span><span class="sxs-lookup"><span data-stu-id="ea84d-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="ea84d-116">Адаптивная карты — для адаптации к различных устройств, стили ux и и инфраструктур пользовательского интерфейса, но они еще не реактивное.</span><span class="sxs-lookup"><span data-stu-id="ea84d-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="ea84d-117">Дополнительные свойства должны быть определены в элементах, позволяющих производители карты для предоставления необходимых указаний в библиотеки визуализации, поэтому они интеллектуально можно изменить макет так, поддерживающий цель карточки.</span><span class="sxs-lookup"><span data-stu-id="ea84d-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="ea84d-118">Быстрые исследования</span><span class="sxs-lookup"><span data-stu-id="ea84d-118">Responsive exploration</span></span>

* <span data-ttu-id="ea84d-119">Добавить **важности** свойство, которое добавляет заметки к важность содержимого.</span><span class="sxs-lookup"><span data-stu-id="ea84d-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="ea84d-120">Менее важное содержимое может удаляться по размеру доступного пространства</span><span class="sxs-lookup"><span data-stu-id="ea84d-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="ea84d-121">Добавить **ограничения** и **политики** свойства, описывающие, как реагировать, когда не удается соблюсти ограничения.</span><span class="sxs-lookup"><span data-stu-id="ea84d-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="ea84d-122">Скрыть содержимое или свернуть содержимое до меньшего размера.</span><span class="sxs-lookup"><span data-stu-id="ea84d-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="ea84d-123">Добавление пороговое значение, при превышении изменяет `columnSet` для Карусель столбцов.</span><span class="sxs-lookup"><span data-stu-id="ea84d-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="ea84d-124">Новых типов элементов</span><span class="sxs-lookup"><span data-stu-id="ea84d-124">New element types</span></span>

* <span data-ttu-id="ea84d-125">Сопоставляет?</span><span class="sxs-lookup"><span data-stu-id="ea84d-125">Maps?</span></span> <span data-ttu-id="ea84d-126">-встроить карту в карточку с взаимодействие или переход к растрового изображения</span><span class="sxs-lookup"><span data-stu-id="ea84d-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="ea84d-127">*Какие элементы той или*?</span><span class="sxs-lookup"><span data-stu-id="ea84d-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="ea84d-128">Новые библиотеки визуализации</span><span class="sxs-lookup"><span data-stu-id="ea84d-128">New rendering libraries</span></span>

* <span data-ttu-id="ea84d-129">Реагирование на них?</span><span class="sxs-lookup"><span data-stu-id="ea84d-129">React?</span></span>
* <span data-ttu-id="ea84d-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="ea84d-130">Xamarin?</span></span>
* <span data-ttu-id="ea84d-131">*Какие платформы требуются?*</span><span class="sxs-lookup"><span data-stu-id="ea84d-131">*What frameworks do you want?*</span></span>
