---
title: Действия — пакет SDK для .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f577c0bab73e2bd1f75bb22dd7a41a7dbfd63307
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454577"
---
# <a name="actions---net-html"></a><span data-ttu-id="24cff-102">Действия — HTML-код .NET</span><span class="sxs-lookup"><span data-stu-id="24cff-102">Actions - .NET HTML</span></span>

<span data-ttu-id="24cff-103">`actions` карт верхнего уровня будет отображаться как `<button>`HTML.</span><span class="sxs-lookup"><span data-stu-id="24cff-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="24cff-104">Так как это библиотека на стороне сервера, вы можете подключать обработчики событий на стороне клиента при нажатии кнопок.</span><span class="sxs-lookup"><span data-stu-id="24cff-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="24cff-105">Каждый `<button>` в HTML будет иметь атрибуты, которые можно использовать для подключения надлежащего поведения.</span><span class="sxs-lookup"><span data-stu-id="24cff-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="24cff-106">Некоторые элементы имеют свойство `selectAction` (контейнер, столбцы, изображение), что делает их недоступными для вызова.</span><span class="sxs-lookup"><span data-stu-id="24cff-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="24cff-107">Если элемент имеет `selectAction` модуль подготовки отчетов добавит класс CSS `ac-selectable`, а также приведенные ниже атрибуты.</span><span class="sxs-lookup"><span data-stu-id="24cff-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="24cff-108">Тип действия</span><span class="sxs-lookup"><span data-stu-id="24cff-108">Action Type</span></span> | <span data-ttu-id="24cff-109">Класс CSS</span><span class="sxs-lookup"><span data-stu-id="24cff-109">CSS class</span></span> | <span data-ttu-id="24cff-110">Дополнительные атрибуты</span><span class="sxs-lookup"><span data-stu-id="24cff-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="24cff-111">`data-ac-url` (свойство `url` из карточки)</span><span class="sxs-lookup"><span data-stu-id="24cff-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="24cff-112">`data-ac-data` (свойство `data` из карточки)</span><span class="sxs-lookup"><span data-stu-id="24cff-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="24cff-113">`data-ac-showcardid` (`id` `<div>`, содержащего внутреннюю карточку)</span><span class="sxs-lookup"><span data-stu-id="24cff-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>