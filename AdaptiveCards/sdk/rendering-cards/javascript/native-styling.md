---
title: Собственный стиль — пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 687a90dd572ba2df786816fdd9dc313746cca982
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454647"
---
# <a name="native-styling---javascript"></a><span data-ttu-id="bb11d-102">Собственный стиль — JavaScript</span><span class="sxs-lookup"><span data-stu-id="bb11d-102">Native styling - JavaScript</span></span>

<span data-ttu-id="bb11d-103">Используйте CSS для точного структурирования HTML-кода карточки.</span><span class="sxs-lookup"><span data-stu-id="bb11d-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="bb11d-104">Следующие классы CSS будут добавлены в различные элементы.</span><span class="sxs-lookup"><span data-stu-id="bb11d-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="bb11d-105">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="bb11d-105">CSS class</span></span> | <span data-ttu-id="bb11d-106">Использование</span><span class="sxs-lookup"><span data-stu-id="bb11d-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="bb11d-107">. AC-контейнер</span><span class="sxs-lookup"><span data-stu-id="bb11d-107">.ac-container</span></span> | <span data-ttu-id="bb11d-108">контейнеры</span><span class="sxs-lookup"><span data-stu-id="bb11d-108">containers</span></span> |
| <span data-ttu-id="bb11d-109">. AC — выбираемый</span><span class="sxs-lookup"><span data-stu-id="bb11d-109">.ac-selectable</span></span>  | <span data-ttu-id="bb11d-110">элементы с `selectAction`</span><span class="sxs-lookup"><span data-stu-id="bb11d-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="bb11d-111">. AC-образ</span><span class="sxs-lookup"><span data-stu-id="bb11d-111">.ac-image</span></span> | <span data-ttu-id="bb11d-112">image</span><span class="sxs-lookup"><span data-stu-id="bb11d-112">image</span></span> |
| <span data-ttu-id="bb11d-113">. AC-кнопка</span><span class="sxs-lookup"><span data-stu-id="bb11d-113">.ac-pushButton</span></span> | <span data-ttu-id="bb11d-114">действия, отображаемые как кнопки</span><span class="sxs-lookup"><span data-stu-id="bb11d-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="bb11d-115">. AC-linkButton</span><span class="sxs-lookup"><span data-stu-id="bb11d-115">.ac-linkButton</span></span>  | <span data-ttu-id="bb11d-116">действия, отображаемые как ссылки</span><span class="sxs-lookup"><span data-stu-id="bb11d-116">actions rendered like links</span></span> |
| <span data-ttu-id="bb11d-117">. AC-вход</span><span class="sxs-lookup"><span data-stu-id="bb11d-117">.ac-input</span></span> | <span data-ttu-id="bb11d-118">элементы управления для ввода</span><span class="sxs-lookup"><span data-stu-id="bb11d-118">input controls</span></span>|
| <span data-ttu-id="bb11d-119">. AC-textInput</span><span class="sxs-lookup"><span data-stu-id="bb11d-119">.ac-textInput</span></span>| <span data-ttu-id="bb11d-120">ввод текста</span><span class="sxs-lookup"><span data-stu-id="bb11d-120">text input</span></span> |
| <span data-ttu-id="bb11d-121">. AC — многострочный</span><span class="sxs-lookup"><span data-stu-id="bb11d-121">.ac-multiline</span></span> | <span data-ttu-id="bb11d-122">Многострочный ввод текста</span><span class="sxs-lookup"><span data-stu-id="bb11d-122">multiline text input</span></span> |
| <span data-ttu-id="bb11d-123">. AC-Нумберинпут</span><span class="sxs-lookup"><span data-stu-id="bb11d-123">.ac-numberInput</span></span> | <span data-ttu-id="bb11d-124">Ввод числа</span><span class="sxs-lookup"><span data-stu-id="bb11d-124">number input</span></span>|
| <span data-ttu-id="bb11d-125">. AC-Датеинпут</span><span class="sxs-lookup"><span data-stu-id="bb11d-125">.ac-dateInput</span></span> | <span data-ttu-id="bb11d-126">Ввод даты</span><span class="sxs-lookup"><span data-stu-id="bb11d-126">date input</span></span>|
| <span data-ttu-id="bb11d-127">. AC-Тимеинпут</span><span class="sxs-lookup"><span data-stu-id="bb11d-127">.ac-timeInput</span></span> | <span data-ttu-id="bb11d-128">входные данные времени</span><span class="sxs-lookup"><span data-stu-id="bb11d-128">time input</span></span> |
| <span data-ttu-id="bb11d-129">. AC-Мултичоицеинпут</span><span class="sxs-lookup"><span data-stu-id="bb11d-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="bb11d-130">многовариантный ввод</span><span class="sxs-lookup"><span data-stu-id="bb11d-130">multichoice input</span></span>|