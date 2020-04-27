---
title: Действия
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454947"
---
# <a name="actions"></a><span data-ttu-id="ff94f-102">Действия</span><span class="sxs-lookup"><span data-stu-id="ff94f-102">Actions</span></span>

<span data-ttu-id="ff94f-103">По умолчанию действия отображаются в виде кнопок на карточке, но приложение может сделать их поведение таким, каким вам требуется.</span><span class="sxs-lookup"><span data-stu-id="ff94f-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="ff94f-104">Каждый пакет SDK содержит эквивалент события `OnAction`, которое необходимо обрабатывать.</span><span class="sxs-lookup"><span data-stu-id="ff94f-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="ff94f-105">**Action.OpenUrl**: открытие указанного `url`.</span><span class="sxs-lookup"><span data-stu-id="ff94f-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="ff94f-106">**Action.Submit**: получение результата отправки и его пересылка в источник.</span><span class="sxs-lookup"><span data-stu-id="ff94f-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="ff94f-107">Способ отправки в источник карточки полностью зависит от вас.</span><span class="sxs-lookup"><span data-stu-id="ff94f-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="ff94f-108">**Action.ShowCard**: вызывает диалоговое окно и отображает в нем вложенную карточку.</span><span class="sxs-lookup"><span data-stu-id="ff94f-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="ff94f-109">Обратите внимание на то, что это действие нужно обрабатывать, только если параметр `ShowCardActionMode` имеет значение `popup`.</span><span class="sxs-lookup"><span data-stu-id="ff94f-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>