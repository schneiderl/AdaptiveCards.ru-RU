---
title: Собственный стиль — пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 6f086d268abcaeb7fa159b74708597e89aafaf53
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552896"
---
# <a name="native-styling---javascript"></a><span data-ttu-id="68eb9-102">Собственный стиль — JavaScript</span><span class="sxs-lookup"><span data-stu-id="68eb9-102">Native styling - JavaScript</span></span>

<span data-ttu-id="68eb9-103">Используйте CSS для точного структурирования HTML-кода карточки.</span><span class="sxs-lookup"><span data-stu-id="68eb9-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="68eb9-104">Следующие классы CSS будут добавлены в различные элементы.</span><span class="sxs-lookup"><span data-stu-id="68eb9-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="68eb9-105">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="68eb9-105">CSS class</span></span> | <span data-ttu-id="68eb9-106">Использование</span><span class="sxs-lookup"><span data-stu-id="68eb9-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="68eb9-107">. AC-контейнер</span><span class="sxs-lookup"><span data-stu-id="68eb9-107">.ac-container</span></span> | <span data-ttu-id="68eb9-108">контейнера</span><span class="sxs-lookup"><span data-stu-id="68eb9-108">containers</span></span> |
| <span data-ttu-id="68eb9-109">. AC — выбираемый</span><span class="sxs-lookup"><span data-stu-id="68eb9-109">.ac-selectable</span></span>  | <span data-ttu-id="68eb9-110">элементы с`selectAction`</span><span class="sxs-lookup"><span data-stu-id="68eb9-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="68eb9-111">. AC-образ</span><span class="sxs-lookup"><span data-stu-id="68eb9-111">.ac-image</span></span> | <span data-ttu-id="68eb9-112">image</span><span class="sxs-lookup"><span data-stu-id="68eb9-112">image</span></span> |
| <span data-ttu-id="68eb9-113">. AC-кнопка</span><span class="sxs-lookup"><span data-stu-id="68eb9-113">.ac-pushButton</span></span> | <span data-ttu-id="68eb9-114">действия, отображаемые как кнопки</span><span class="sxs-lookup"><span data-stu-id="68eb9-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="68eb9-115">. AC-linkButton</span><span class="sxs-lookup"><span data-stu-id="68eb9-115">.ac-linkButton</span></span>  | <span data-ttu-id="68eb9-116">действия, отображаемые как ссылки</span><span class="sxs-lookup"><span data-stu-id="68eb9-116">actions rendered like links</span></span> |
| <span data-ttu-id="68eb9-117">. AC-вход</span><span class="sxs-lookup"><span data-stu-id="68eb9-117">.ac-input</span></span> | <span data-ttu-id="68eb9-118">элементы управления вводом</span><span class="sxs-lookup"><span data-stu-id="68eb9-118">input controls</span></span>|
| <span data-ttu-id="68eb9-119">. AC-textInput</span><span class="sxs-lookup"><span data-stu-id="68eb9-119">.ac-textInput</span></span>| <span data-ttu-id="68eb9-120">Ввод текста</span><span class="sxs-lookup"><span data-stu-id="68eb9-120">text input</span></span> |
| <span data-ttu-id="68eb9-121">. AC — многострочный</span><span class="sxs-lookup"><span data-stu-id="68eb9-121">.ac-multiline</span></span> | <span data-ttu-id="68eb9-122">Многострочный ввод текста</span><span class="sxs-lookup"><span data-stu-id="68eb9-122">multiline text input</span></span> |
| <span data-ttu-id="68eb9-123">. AC-Нумберинпут</span><span class="sxs-lookup"><span data-stu-id="68eb9-123">.ac-numberInput</span></span> | <span data-ttu-id="68eb9-124">Ввод числа</span><span class="sxs-lookup"><span data-stu-id="68eb9-124">number input</span></span>|
| <span data-ttu-id="68eb9-125">. AC-Датеинпут</span><span class="sxs-lookup"><span data-stu-id="68eb9-125">.ac-dateInput</span></span> | <span data-ttu-id="68eb9-126">Ввод даты</span><span class="sxs-lookup"><span data-stu-id="68eb9-126">date input</span></span>|
| <span data-ttu-id="68eb9-127">. AC-Тимеинпут</span><span class="sxs-lookup"><span data-stu-id="68eb9-127">.ac-timeInput</span></span> | <span data-ttu-id="68eb9-128">входные данные времени</span><span class="sxs-lookup"><span data-stu-id="68eb9-128">time input</span></span> |
| <span data-ttu-id="68eb9-129">. AC-Мултичоицеинпут</span><span class="sxs-lookup"><span data-stu-id="68eb9-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="68eb9-130">многовариантный ввод</span><span class="sxs-lookup"><span data-stu-id="68eb9-130">multichoice input</span></span>|