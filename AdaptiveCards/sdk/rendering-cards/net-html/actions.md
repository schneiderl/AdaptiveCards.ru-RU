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
# <a name="actions---net-html"></a>Действия — HTML-код .NET

`actions` карт верхнего уровня будет отображаться как `<button>`HTML. Так как это библиотека на стороне сервера, вы можете подключать обработчики событий на стороне клиента при нажатии кнопок. Каждый `<button>` в HTML будет иметь атрибуты, которые можно использовать для подключения надлежащего поведения.

Некоторые элементы имеют свойство `selectAction` (контейнер, столбцы, изображение), что делает их недоступными для вызова. Если элемент имеет `selectAction` модуль подготовки отчетов добавит класс CSS `ac-selectable`, а также приведенные ниже атрибуты.

Тип действия | Класс CSS | Дополнительные атрибуты
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` (свойство `url` из карточки)
`Action.Submit` | `ac-action-submit` | `data-ac-data` (свойство `data` из карточки)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` (`id` `<div>`, содержащего внутреннюю карточку)