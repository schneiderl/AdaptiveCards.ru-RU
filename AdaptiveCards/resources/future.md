---
title: Стратегия развития адаптивной карты
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: 6c6e14108caefa8dd1ff854b29d4651fe9b2d15c
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553486"
---
# <a name="future-work"></a><span data-ttu-id="b7c0a-102">Дальнейшей работы</span><span class="sxs-lookup"><span data-stu-id="b7c0a-102">Future work</span></span>

<span data-ttu-id="b7c0a-103">Хотя мы внесли отличную хода выполнения, определение адаптивной карты, по-прежнему много работы.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="b7c0a-104">Мы надеемся является, через сообщества разработчиков active botness и отлично партнеров, как Slack и Kik, можно создать отличные экосистемы кросс платформенных карт.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="b7c0a-105">Стратегия</span><span class="sxs-lookup"><span data-stu-id="b7c0a-105">Roadmap</span></span>

<span data-ttu-id="b7c0a-106">Вы увидите наших [текущий план (неконечного) здесь](https://github.com/Microsoft/AdaptiveCards/projects/8).</span><span class="sxs-lookup"><span data-stu-id="b7c0a-106">You can see our [current (non-final) roadmap here](https://github.com/Microsoft/AdaptiveCards/projects/8).</span></span> <span data-ttu-id="b7c0a-107">Обратите внимание, что-то в данной статье, может быть изменена что это значение не гарантирует доставку.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="b7c0a-108">Будущие идеи</span><span class="sxs-lookup"><span data-stu-id="b7c0a-108">Future ideas</span></span>

<span data-ttu-id="b7c0a-109">Ниже приведены некоторые будущих идеи, которые у нас есть, которые являются просто стадии мозговой.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="b7c0a-110">Если вы заинтересованы в любой из них, сообщите об этом в комментарии.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="b7c0a-111">Отличный выглядящие карты на основе данных</span><span class="sxs-lookup"><span data-stu-id="b7c0a-111">Great looking Cards from Data</span></span>

<span data-ttu-id="b7c0a-112">Мы знаем, многие авторы карты еще нет четко определенных данных карты.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="b7c0a-113">Наш план является исследование модель шаблонов, которая позволила бы карты для создаваемого (на стороне сервера или на стороне клиента) на основе данных и репозиторием четко определенных и настраиваемых шаблонов.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="b7c0a-114">Создание быстро реагирующих карточек</span><span class="sxs-lookup"><span data-stu-id="b7c0a-114">Make cards responsive</span></span>

<span data-ttu-id="b7c0a-115">Макеты карт следует за событиями доступное пространство.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="b7c0a-116">Адаптивная карты — для адаптации к различных устройств, стили ux и и инфраструктур пользовательского интерфейса, но они еще не реактивное.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="b7c0a-117">Дополнительные свойства должны быть определены в элементах, позволяющих производители карты для предоставления необходимых указаний в библиотеки визуализации, поэтому они интеллектуально можно изменить макет так, поддерживающий цель карточки.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="b7c0a-118">Быстрые исследования</span><span class="sxs-lookup"><span data-stu-id="b7c0a-118">Responsive exploration</span></span>

* <span data-ttu-id="b7c0a-119">Добавить **важности** свойство, которое добавляет заметки к важность содержимого.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="b7c0a-120">Менее важное содержимое может удаляться по размеру доступного пространства</span><span class="sxs-lookup"><span data-stu-id="b7c0a-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="b7c0a-121">Добавить **ограничения** и **политики** свойства, описывающие, как реагировать, когда не удается соблюсти ограничения.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="b7c0a-122">Скрыть содержимое или свернуть содержимое до меньшего размера.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="b7c0a-123">Добавление пороговое значение, при превышении изменяет `columnSet` для Карусель столбцов.</span><span class="sxs-lookup"><span data-stu-id="b7c0a-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="b7c0a-124">Новых типов элементов</span><span class="sxs-lookup"><span data-stu-id="b7c0a-124">New element types</span></span>

* <span data-ttu-id="b7c0a-125">Сопоставляет?</span><span class="sxs-lookup"><span data-stu-id="b7c0a-125">Maps?</span></span> <span data-ttu-id="b7c0a-126">-встроить карту в карточку с взаимодействие или переход к растрового изображения</span><span class="sxs-lookup"><span data-stu-id="b7c0a-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="b7c0a-127">*Какие элементы той или*?</span><span class="sxs-lookup"><span data-stu-id="b7c0a-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="b7c0a-128">Новые библиотеки визуализации</span><span class="sxs-lookup"><span data-stu-id="b7c0a-128">New rendering libraries</span></span>

* <span data-ttu-id="b7c0a-129">Реагирование на них?</span><span class="sxs-lookup"><span data-stu-id="b7c0a-129">React?</span></span>
* <span data-ttu-id="b7c0a-130">Xamarin?</span><span class="sxs-lookup"><span data-stu-id="b7c0a-130">Xamarin?</span></span>
* <span data-ttu-id="b7c0a-131">*Какие платформы требуются?*</span><span class="sxs-lookup"><span data-stu-id="b7c0a-131">*What frameworks do you want?*</span></span>
