---
title: Начало работы
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9cc7344ac357dcb95c7e47e377dbb12fbcd66957
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417483"
---
# <a name="getting-started"></a><span data-ttu-id="04708-102">Начало работы</span><span class="sxs-lookup"><span data-stu-id="04708-102">Getting Started</span></span> 

<span data-ttu-id="04708-103">Адаптивная карточка — это объектная модель карточки с сериализацией в формате JSON.</span><span class="sxs-lookup"><span data-stu-id="04708-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="04708-104">Структура адаптивной карточки</span><span class="sxs-lookup"><span data-stu-id="04708-104">Adaptive Card structure</span></span>

<span data-ttu-id="04708-105">Базовая структура карточки выглядит так:</span><span class="sxs-lookup"><span data-stu-id="04708-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="04708-106">`AdaptiveCard` — это корневой объект, описывающий саму адаптивную карточку, включая ее составные элементы, действия, параметры ее речевого воспроизведения и версию схемы, необходимой для ее визуализации.</span><span class="sxs-lookup"><span data-stu-id="04708-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="04708-107">`body` — это содержимое карточки, которое состоит из структурных блоков, называемых `elements`.</span><span class="sxs-lookup"><span data-stu-id="04708-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="04708-108">Эти элементы могут комбинироваться самым разным образом, обеспечивая разнообразие карточек.</span><span class="sxs-lookup"><span data-stu-id="04708-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="04708-109">`actions` — это действия, которые в карточке может выполнять пользователь.</span><span class="sxs-lookup"><span data-stu-id="04708-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="04708-110">Это свойство описывает действия, которые обычно визуализируются на панели действий внизу.</span><span class="sxs-lookup"><span data-stu-id="04708-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="04708-111">Пример карточки</span><span class="sxs-lookup"><span data-stu-id="04708-111">Example Card</span></span>

<span data-ttu-id="04708-112">Этот пример карточки содержит одну строку текста и изображение.</span><span class="sxs-lookup"><span data-stu-id="04708-112">This sample card which includes a single line of text followed by an image.</span></span>

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

## <a name="type-property"></a><span data-ttu-id="04708-113">Свойство `Type`</span><span class="sxs-lookup"><span data-stu-id="04708-113">`Type` property</span></span>

<span data-ttu-id="04708-114">У каждого элемента есть свойство `type`, которое определяет тип объекта для него.</span><span class="sxs-lookup"><span data-stu-id="04708-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="04708-115">Из предыдущего примера карточки видно, что у нас есть два элемента: `TextBlock` и `Image`.</span><span class="sxs-lookup"><span data-stu-id="04708-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="04708-116">Все элементы адаптивных карточек **располагаются по вертикали** и **находятся в границах своих родительских элементов** (как и `display: block` в HTML).</span><span class="sxs-lookup"><span data-stu-id="04708-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="04708-117">Но вы можете использовать `ColumnSet` для расположения столбцов контейнеров рядом.</span><span class="sxs-lookup"><span data-stu-id="04708-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="04708-118">Адаптивные элементы</span><span class="sxs-lookup"><span data-stu-id="04708-118">Adaptive Elements</span></span>

<span data-ttu-id="04708-119">Ниже перечислены основные элементы.</span><span class="sxs-lookup"><span data-stu-id="04708-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="04708-120">**TextBlock** добавляет блок текста со свойствами, определяющими внешний вид текста.</span><span class="sxs-lookup"><span data-stu-id="04708-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="04708-121">**Image** добавляет изображение со свойствами, определяющими внешний вид изображения.</span><span class="sxs-lookup"><span data-stu-id="04708-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="04708-122">Элементы контейнера</span><span class="sxs-lookup"><span data-stu-id="04708-122">Container elements</span></span>

<span data-ttu-id="04708-123">Карточки могут также содержать контейнеры с коллекциями дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="04708-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="04708-124">**Container** определяет коллекцию элементов.</span><span class="sxs-lookup"><span data-stu-id="04708-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="04708-125">**ColumnSet/Column** определяет коллекцию столбцов, каждый из которых представляет контейнер.</span><span class="sxs-lookup"><span data-stu-id="04708-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="04708-126">**FactSet** — это контейнер с данными.</span><span class="sxs-lookup"><span data-stu-id="04708-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="04708-127">**ImageSet** — это контейнер с изображениями для визуализации в пользовательском интерфейсе соответствующих изображений из коллекции.</span><span class="sxs-lookup"><span data-stu-id="04708-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="04708-128">Элементы ввода</span><span class="sxs-lookup"><span data-stu-id="04708-128">Input elements</span></span>

<span data-ttu-id="04708-129">Элементы ввода позволяют создавать в интерфейсе карточки простые формы.</span><span class="sxs-lookup"><span data-stu-id="04708-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="04708-130">**Input.Text** позволяет пользователю вводить текст.</span><span class="sxs-lookup"><span data-stu-id="04708-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="04708-131">**Input.Date** позволяет пользователю вводить дату.</span><span class="sxs-lookup"><span data-stu-id="04708-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="04708-132">**Input.Time** позволяет пользователю вводить время.</span><span class="sxs-lookup"><span data-stu-id="04708-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="04708-133">**Input.Number** позволяет пользователю вводить числа.</span><span class="sxs-lookup"><span data-stu-id="04708-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="04708-134">**Input.ChoiceSet** предоставляет пользователю набор вариантов и возможность их выбора.</span><span class="sxs-lookup"><span data-stu-id="04708-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="04708-135">**Input.Toggle** предоставляет пользователю два варианта с возможностью выбрать один из них.</span><span class="sxs-lookup"><span data-stu-id="04708-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="04708-136">Действия</span><span class="sxs-lookup"><span data-stu-id="04708-136">Actions</span></span>

<span data-ttu-id="04708-137">Действия добавляют в карточки кнопки.</span><span class="sxs-lookup"><span data-stu-id="04708-137">Actions add buttons to the card.</span></span> <span data-ttu-id="04708-138">С их помощью можно выполнять различные действия, такие как переход по URL-адресу или передача определенных сведений.</span><span class="sxs-lookup"><span data-stu-id="04708-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="04708-139">**Action.OpenUrl** — это кнопка для перехода по внешнему URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="04708-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="04708-140">**Action.ShowCard** отображает вложенную карточку для просмотра пользователем.</span><span class="sxs-lookup"><span data-stu-id="04708-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="04708-141">**Action.Submit** сбор данных ото всех элементов в один объект и его отправка способом, определяемым целевым приложением.</span><span class="sxs-lookup"><span data-stu-id="04708-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="04708-142">**Пример использования Action.Submit**. С помощью Skype и Action.Submit данные о действиях бота Bot Framework возвращаются боту со свойством **Value**, содержащим объект со всеми данными, введенными пользователями.</span><span class="sxs-lookup"><span data-stu-id="04708-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="04708-143">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="04708-143">Learn More</span></span>

* <span data-ttu-id="04708-144">[Ознакомьтесь с примерами адаптивных карточек](https://adaptivecards.io/samples/).</span><span class="sxs-lookup"><span data-stu-id="04708-144">[Browse Sample cards](https://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="04708-145">Воспользуйтесь [обозревателем схемы](https://adaptivecards.io/explorer), чтобы найти доступные элементы.</span><span class="sxs-lookup"><span data-stu-id="04708-145">Use the [Schema Explorer](https://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="04708-146">Создайте адаптивную карточку с помощью [интерактивного визуализатора](https://adaptivecards.io/visualizer/).</span><span class="sxs-lookup"><span data-stu-id="04708-146">Build a card using the [Interactive Visualizer](https://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="04708-147">[Свяжитесь с нами](https://adaptivecards.io/connect), чтобы оставить свой отзыв.</span><span class="sxs-lookup"><span data-stu-id="04708-147">[Get in touch](https://adaptivecards.io/connect) with any feedback you have</span></span>
