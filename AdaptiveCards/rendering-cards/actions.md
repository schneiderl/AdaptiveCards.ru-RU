---
title: Действия
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 42ba1ca4ba2ecd508bdee2f04061293d48349aab
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553376"
---
# <a name="actions"></a><span data-ttu-id="3ebe5-102">Действия</span><span class="sxs-lookup"><span data-stu-id="3ebe5-102">Actions</span></span>

<span data-ttu-id="3ebe5-103">По умолчанию действия будет отображаться в виде кнопок на карте, но он работает в приложение, чтобы сделать их ожиданиям.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="3ebe5-104">Каждый пакет SDK входит эквивалент `OnAction` событие, которое необходимо обработать.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="3ebe5-105">**Action.OpenUrl** -открыть указанный `url`.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="3ebe5-106">**Action.Submit** - принимающей результат отправки с последующей отправкой к источнику.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="3ebe5-107">Как можно отправлять в источник карты — полностью на ваше усмотрение.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="3ebe5-108">**Action.ShowCard** — вызывает диалоговое окно и отображает карточке вложенные в этот диалог.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="3ebe5-109">Обратите внимание, что достаточно для обработки этого, если `ShowCardActionMode` присваивается `popup`.</span><span class="sxs-lookup"><span data-stu-id="3ebe5-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>