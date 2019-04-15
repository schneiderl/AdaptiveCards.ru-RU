---
title: Собственные стили - пакет SDK для JavaScript
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
# <a name="native-styling---javascript"></a><span data-ttu-id="e9c81-102">Собственный стиль — JavaScript</span><span class="sxs-lookup"><span data-stu-id="e9c81-102">Native styling - JavaScript</span></span>

<span data-ttu-id="e9c81-103">Используйте CSS для точного стилей карточки HTML.</span><span class="sxs-lookup"><span data-stu-id="e9c81-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="e9c81-104">Следующие классы CSS будут добавляться к различным элементам.</span><span class="sxs-lookup"><span data-stu-id="e9c81-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="e9c81-105">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="e9c81-105">CSS class</span></span> | <span data-ttu-id="e9c81-106">Использование</span><span class="sxs-lookup"><span data-stu-id="e9c81-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="e9c81-107">.AC контейнера</span><span class="sxs-lookup"><span data-stu-id="e9c81-107">.ac-container</span></span> | <span data-ttu-id="e9c81-108">Контейнеры</span><span class="sxs-lookup"><span data-stu-id="e9c81-108">containers</span></span> |
| <span data-ttu-id="e9c81-109">можно выбрать .ac</span><span class="sxs-lookup"><span data-stu-id="e9c81-109">.ac-selectable</span></span>  | <span data-ttu-id="e9c81-110">элементы с `selectAction`</span><span class="sxs-lookup"><span data-stu-id="e9c81-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="e9c81-111">.AC-image</span><span class="sxs-lookup"><span data-stu-id="e9c81-111">.ac-image</span></span> | <span data-ttu-id="e9c81-112">image</span><span class="sxs-lookup"><span data-stu-id="e9c81-112">image</span></span> |
| <span data-ttu-id="e9c81-113">.AC pushButton</span><span class="sxs-lookup"><span data-stu-id="e9c81-113">.ac-pushButton</span></span> | <span data-ttu-id="e9c81-114">действия при подготовке к просмотру как кнопки</span><span class="sxs-lookup"><span data-stu-id="e9c81-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="e9c81-115">.AC linkButton</span><span class="sxs-lookup"><span data-stu-id="e9c81-115">.ac-linkButton</span></span>  | <span data-ttu-id="e9c81-116">действия при подготовке к просмотру как ссылки</span><span class="sxs-lookup"><span data-stu-id="e9c81-116">actions rendered like links</span></span> |
| <span data-ttu-id="e9c81-117">входные данные .ac</span><span class="sxs-lookup"><span data-stu-id="e9c81-117">.ac-input</span></span> | <span data-ttu-id="e9c81-118">Элементы управления для ввода</span><span class="sxs-lookup"><span data-stu-id="e9c81-118">input controls</span></span>|
| <span data-ttu-id="e9c81-119">.AC textInput</span><span class="sxs-lookup"><span data-stu-id="e9c81-119">.ac-textInput</span></span>| <span data-ttu-id="e9c81-120">Ввод текста</span><span class="sxs-lookup"><span data-stu-id="e9c81-120">text input</span></span> |
| <span data-ttu-id="e9c81-121">.AC / многострочной</span><span class="sxs-lookup"><span data-stu-id="e9c81-121">.ac-multiline</span></span> | <span data-ttu-id="e9c81-122">Многострочное текстовое поле</span><span class="sxs-lookup"><span data-stu-id="e9c81-122">multiline text input</span></span> |
| <span data-ttu-id="e9c81-123">.AC numberInput</span><span class="sxs-lookup"><span data-stu-id="e9c81-123">.ac-numberInput</span></span> | <span data-ttu-id="e9c81-124">Введенный номер</span><span class="sxs-lookup"><span data-stu-id="e9c81-124">number input</span></span>|
| <span data-ttu-id="e9c81-125">.AC dateInput</span><span class="sxs-lookup"><span data-stu-id="e9c81-125">.ac-dateInput</span></span> | <span data-ttu-id="e9c81-126">Дата ввода</span><span class="sxs-lookup"><span data-stu-id="e9c81-126">date input</span></span>|
| <span data-ttu-id="e9c81-127">.AC timeInput</span><span class="sxs-lookup"><span data-stu-id="e9c81-127">.ac-timeInput</span></span> | <span data-ttu-id="e9c81-128">время ввода</span><span class="sxs-lookup"><span data-stu-id="e9c81-128">time input</span></span> |
| <span data-ttu-id="e9c81-129">.ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="e9c81-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="e9c81-130">multichoice входных данных</span><span class="sxs-lookup"><span data-stu-id="e9c81-130">multichoice input</span></span>|