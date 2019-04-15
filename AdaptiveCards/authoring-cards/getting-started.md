---
title: начало работы
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9d363da0c10b242e23d2594984292fcc1f31382f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552686"
---
# <a name="getting-started"></a><span data-ttu-id="79b1f-102">начало работы</span><span class="sxs-lookup"><span data-stu-id="79b1f-102">Getting Started</span></span> 

<span data-ttu-id="79b1f-103">Инструмент Adaptive Cards — это объектная модель сериализации JSON карты.</span><span class="sxs-lookup"><span data-stu-id="79b1f-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="79b1f-104">Адаптивная структуры карты</span><span class="sxs-lookup"><span data-stu-id="79b1f-104">Adaptive Card structure</span></span>

<span data-ttu-id="79b1f-105">Базовая структура карты выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="79b1f-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="79b1f-106">`AdaptiveCard` — Корневой объект описывает AdaptiveCard, включая его состав элемента, его действия, как оно произношения и версии схемы, необходимых для его отображения.</span><span class="sxs-lookup"><span data-stu-id="79b1f-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="79b1f-107">`body` -Текст карточки состоит из стандартных блоков называется `elements`.</span><span class="sxs-lookup"><span data-stu-id="79b1f-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="79b1f-108">Элементы могут быть включены в практически неограниченная соглашениях, чтобы создавать много типов карт.</span><span class="sxs-lookup"><span data-stu-id="79b1f-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="79b1f-109">`actions` -Многие карточки имеют набор действий, которые пользователь может воспользоваться на нем.</span><span class="sxs-lookup"><span data-stu-id="79b1f-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="79b1f-110">Это свойство описывает эти действия, которые обычно отображаемые в «панель действий» внизу.</span><span class="sxs-lookup"><span data-stu-id="79b1f-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="79b1f-111">Пример карты</span><span class="sxs-lookup"><span data-stu-id="79b1f-111">Example Card</span></span>

<span data-ttu-id="79b1f-112">Эта карточка пример, включающий строку текста, следуют изображения.</span><span class="sxs-lookup"><span data-stu-id="79b1f-112">This sample card which includes a single line of text followed by an image.</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a><span data-ttu-id="79b1f-113">Свойство `Type`</span><span class="sxs-lookup"><span data-stu-id="79b1f-113">`Type` property</span></span>

<span data-ttu-id="79b1f-114">Каждый элемент имеет `type` свойство, которое определяет, что это объект.</span><span class="sxs-lookup"><span data-stu-id="79b1f-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="79b1f-115">Взглянув на карточке выше, вы увидите у нас есть два элемента `TextBlock` и `Image`.</span><span class="sxs-lookup"><span data-stu-id="79b1f-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="79b1f-116">Все элементы инструмент Adaptive Cards **располагаются по вертикали,** и **разверните, чтобы ширина родительских** (представить `display: block` в формате HTML).</span><span class="sxs-lookup"><span data-stu-id="79b1f-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="79b1f-117">Тем не менее, можно использовать `ColumnSet` для создания столбцов side-by-side контейнеров.</span><span class="sxs-lookup"><span data-stu-id="79b1f-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="79b1f-118">Адаптивные элементы</span><span class="sxs-lookup"><span data-stu-id="79b1f-118">Adaptive Elements</span></span>

<span data-ttu-id="79b1f-119">Ниже приведены самые основные элементы.</span><span class="sxs-lookup"><span data-stu-id="79b1f-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="79b1f-120">**TextBlock** -добавляет блок текста с помощью свойства, определяющие, как выглядит текст</span><span class="sxs-lookup"><span data-stu-id="79b1f-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="79b1f-121">**Изображение** -добавляет изображение с помощью свойства, определяющие, как выглядит изображение</span><span class="sxs-lookup"><span data-stu-id="79b1f-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="79b1f-122">Элементы контейнера</span><span class="sxs-lookup"><span data-stu-id="79b1f-122">Container elements</span></span>

<span data-ttu-id="79b1f-123">Карты могут также иметь контейнеры, которые размещают коллекцию дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="79b1f-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="79b1f-124">**Контейнер** -определяет коллекцию элементов</span><span class="sxs-lookup"><span data-stu-id="79b1f-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="79b1f-125">**Набор столбцов или столбцов** -определяет коллекцию столбцов, каждый столбец — это контейнер</span><span class="sxs-lookup"><span data-stu-id="79b1f-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="79b1f-126">**FactSet** -контейнер фактов</span><span class="sxs-lookup"><span data-stu-id="79b1f-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="79b1f-127">**ImageSet** -контейнера изображения, Интерфейс может показать соответствующие фото качества коллекции для коллекции изображений.</span><span class="sxs-lookup"><span data-stu-id="79b1f-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="79b1f-128">Входные элементы</span><span class="sxs-lookup"><span data-stu-id="79b1f-128">Input elements</span></span>

<span data-ttu-id="79b1f-129">Элементы ввода дают возможность задавать для собственного пользовательского интерфейса для создания простых форм:</span><span class="sxs-lookup"><span data-stu-id="79b1f-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="79b1f-130">**Input.Text** -получить текстовое содержимое от пользователя</span><span class="sxs-lookup"><span data-stu-id="79b1f-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="79b1f-131">**Input.Date** -получение даты от пользователя</span><span class="sxs-lookup"><span data-stu-id="79b1f-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="79b1f-132">**Input.Time** -получить время от пользователя</span><span class="sxs-lookup"><span data-stu-id="79b1f-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="79b1f-133">**Input.Number** -получить это значение от пользователя</span><span class="sxs-lookup"><span data-stu-id="79b1f-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="79b1f-134">**Input.ChoiceSet** — предоставить пользователю набор вариантов и их выбор</span><span class="sxs-lookup"><span data-stu-id="79b1f-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="79b1f-135">**Input.Toggle** — предоставить пользователю выбор между двумя элементами одного из вариантов и их выбор</span><span class="sxs-lookup"><span data-stu-id="79b1f-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="79b1f-136">Действия</span><span class="sxs-lookup"><span data-stu-id="79b1f-136">Actions</span></span>

<span data-ttu-id="79b1f-137">Действия добавляют кнопки на карточке.</span><span class="sxs-lookup"><span data-stu-id="79b1f-137">Actions add buttons to the card.</span></span> <span data-ttu-id="79b1f-138">Их можно выполнять различные действия, такие как открытие URL-адрес или передавать некоторые данные.</span><span class="sxs-lookup"><span data-stu-id="79b1f-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="79b1f-139">**Action.OpenUrl** -кнопки открывается внешний URL-адрес для просмотра</span><span class="sxs-lookup"><span data-stu-id="79b1f-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="79b1f-140">**Action.ShowCard** -запрашивает вложенных карту для отображения пользователю.</span><span class="sxs-lookup"><span data-stu-id="79b1f-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="79b1f-141">**Action.Submit** -задавать для всех элементов ввода необходимо собирать в объект, который затем отправляется пользователю через определенные ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="79b1f-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="79b1f-142">**Пример Action.Submit**: С помощью Скайп, Action.Submit для отправки программы-робота, Bot Framework действия программ-роботов с **значение** свойство, содержащее объект со всеми входных данных на нем.</span><span class="sxs-lookup"><span data-stu-id="79b1f-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="79b1f-143">Подробнее</span><span class="sxs-lookup"><span data-stu-id="79b1f-143">Learn More</span></span>

* <span data-ttu-id="79b1f-144">[Обзор образца карты](http://adaptivecards.io/samples/) вдохновения</span><span class="sxs-lookup"><span data-stu-id="79b1f-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="79b1f-145">Используйте [обозреватель схем](http://adaptivecards.io/explorer) для просмотра доступных элементов</span><span class="sxs-lookup"><span data-stu-id="79b1f-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="79b1f-146">Построение карт с помощью [интерактивных визуализатора](http://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="79b1f-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="79b1f-147">[Связаться с нами](http://adaptivecards.io/connect) с свои отзывы</span><span class="sxs-lookup"><span data-stu-id="79b1f-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
