---
title: Действия — пакет SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 99bf6121489391c207a71b45264dc68aa2c6116e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553316"
---
# <a name="actions---net-html"></a><span data-ttu-id="0c49d-102">Действия — .NET HTML</span><span class="sxs-lookup"><span data-stu-id="0c49d-102">Actions - .NET HTML</span></span>

<span data-ttu-id="0c49d-103">Верхнего уровня карты `actions` отрисовывается как HTML `<button>`.</span><span class="sxs-lookup"><span data-stu-id="0c49d-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="0c49d-104">Так как это библиотека на стороне сервера именно возможность связывать обработчики событий на стороне клиента, при нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="0c49d-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="0c49d-105">Каждый `<button>` в HTML будет иметь атрибуты, которые можно использовать для подключения соответствующее поведение.</span><span class="sxs-lookup"><span data-stu-id="0c49d-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="0c49d-106">Некоторые элементы имеют `selectAction` свойство (образ контейнера, столбцы,), что делает их вызываемый объект.</span><span class="sxs-lookup"><span data-stu-id="0c49d-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="0c49d-107">Если элемент имеет `selectAction` модуль подготовки отчетов добавит класс CSS элемента `ac-selectable`, вместе с ниже атрибуты.</span><span class="sxs-lookup"><span data-stu-id="0c49d-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="0c49d-108">Тип действия</span><span class="sxs-lookup"><span data-stu-id="0c49d-108">Action Type</span></span> | <span data-ttu-id="0c49d-109">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="0c49d-109">CSS class</span></span> | <span data-ttu-id="0c49d-110">Дополнительные атрибуты</span><span class="sxs-lookup"><span data-stu-id="0c49d-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="0c49d-111">`data-ac-url` ( `url` свойство из карточки)</span><span class="sxs-lookup"><span data-stu-id="0c49d-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="0c49d-112">`data-ac-data` ( `data` свойство из карточки)</span><span class="sxs-lookup"><span data-stu-id="0c49d-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="0c49d-113">`data-ac-showcardid` ( `id` из `<div>` содержащий карточке внутреннее)</span><span class="sxs-lookup"><span data-stu-id="0c49d-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>