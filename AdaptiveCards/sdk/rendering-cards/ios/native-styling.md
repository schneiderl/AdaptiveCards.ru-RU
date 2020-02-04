---
title: Собственный стиль — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f9ed839a19ac778381fa36361ad37e95b7ab5e08
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727470"
---
# <a name="native-styling---ios"></a><span data-ttu-id="a987e-102">Собственный стиль — iOS</span><span class="sxs-lookup"><span data-stu-id="a987e-102">Native styling - iOS</span></span>

<span data-ttu-id="a987e-103">Используйте XIB для точной детализации стилей.</span><span class="sxs-lookup"><span data-stu-id="a987e-103">Use XIB for fine-grained styling.</span></span>

<span data-ttu-id="a987e-104">Существует следующий XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-104">The following XIBs exist</span></span>

| <span data-ttu-id="a987e-105">XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-105">XIB</span></span> | <span data-ttu-id="a987e-106">Использование</span><span class="sxs-lookup"><span data-stu-id="a987e-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="a987e-107">Акрбуттон. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-107">ACRButton.xib</span></span> | <span data-ttu-id="a987e-108">кнопки</span><span class="sxs-lookup"><span data-stu-id="a987e-108">buttons</span></span> |
| <span data-ttu-id="a987e-109">Акрцеллфоркомпактмоде. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-109">ACRCellForCompactMode.xib</span></span>   | <span data-ttu-id="a987e-110">Компактный режим "Choice"</span><span class="sxs-lookup"><span data-stu-id="a987e-110">ChoiceSet compact mode</span></span>|
| <span data-ttu-id="a987e-111">Акрдатепиккер. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-111">ACRDatePicker.xib</span></span> | <span data-ttu-id="a987e-112">DatePicker для input. Date</span><span class="sxs-lookup"><span data-stu-id="a987e-112">DatePicker for Input.Date</span></span> |
| <span data-ttu-id="a987e-113">Акрдатетекстфиелд. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-113">ACRDateTextField.xib</span></span>  | <span data-ttu-id="a987e-114">TextField для input. Date</span><span class="sxs-lookup"><span data-stu-id="a987e-114">TextField for Input.Date</span></span> |
| <span data-ttu-id="a987e-115">Акринпуттаблевиев. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-115">ACRInputTableView.xib</span></span>   | <span data-ttu-id="a987e-116">Контейнер для входных данных</span><span class="sxs-lookup"><span data-stu-id="a987e-116">Container for Inputs</span></span> |
| <span data-ttu-id="a987e-117">Акрлабелвиев. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-117">ACRLabelView.xib</span></span>  | <span data-ttu-id="a987e-118">TextBlock</span><span class="sxs-lookup"><span data-stu-id="a987e-118">TextBlock</span></span> |
| <span data-ttu-id="a987e-119">Акрпиккервиев. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-119">ACRPickerView.xib</span></span> | <span data-ttu-id="a987e-120">Choice</span><span class="sxs-lookup"><span data-stu-id="a987e-120">ChoiceSet</span></span> |
| <span data-ttu-id="a987e-121">Акркуиккактионмултилиневиев. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-121">ACRQuickActionMultilineView.xib</span></span>  | <span data-ttu-id="a987e-122">Быстрые действия с многострочными</span><span class="sxs-lookup"><span data-stu-id="a987e-122">Quick Actions with multilines</span></span> |
| <span data-ttu-id="a987e-123">Акркуиккактионвиев. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-123">ACRQuickActionView.xib</span></span> | <span data-ttu-id="a987e-124">Быстрые действия</span><span class="sxs-lookup"><span data-stu-id="a987e-124">Quick Actions</span></span> |
| <span data-ttu-id="a987e-125">Акртекстфиелд. XIB</span><span class="sxs-lookup"><span data-stu-id="a987e-125">ACRTextField.xib</span></span> | <span data-ttu-id="a987e-126">Ввод</span><span class="sxs-lookup"><span data-stu-id="a987e-126">Input</span></span> |

<span data-ttu-id="a987e-127">XIB можно редактировать через XCode.</span><span class="sxs-lookup"><span data-stu-id="a987e-127">XIB can be edited through XCode IB.</span></span>
<span data-ttu-id="a987e-128">После изменения XIB в спецификацию.</span><span class="sxs-lookup"><span data-stu-id="a987e-128">Once XIBs are edited to the specification.</span></span>
<span data-ttu-id="a987e-129">Из терминала</span><span class="sxs-lookup"><span data-stu-id="a987e-129">From a terminal</span></span>
```
ibtool --compile name.nib name.xib 
```

<span data-ttu-id="a987e-130">Например, чтобы присвоить стилю кнопку</span><span class="sxs-lookup"><span data-stu-id="a987e-130">For example, to style a button</span></span>
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

<span data-ttu-id="a987e-131">Созданные файлы NIB можно затем заменить на Адаптивекардс. Framework</span><span class="sxs-lookup"><span data-stu-id="a987e-131">The generated nib files can be then replaced at AdaptiveCards.framework</span></span>
