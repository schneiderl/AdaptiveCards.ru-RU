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
# <a name="actions---net-html"></a>Действия — .NET HTML

Верхнего уровня карты `actions` отрисовывается как HTML `<button>`. Так как это библиотека на стороне сервера именно возможность связывать обработчики событий на стороне клиента, при нажатии кнопки. Каждый `<button>` в HTML будет иметь атрибуты, которые можно использовать для подключения соответствующее поведение.

Некоторые элементы имеют `selectAction` свойство (образ контейнера, столбцы,), что делает их вызываемый объект. Если элемент имеет `selectAction` модуль подготовки отчетов добавит класс CSS элемента `ac-selectable`, вместе с ниже атрибуты.

Тип действия | Класс CSS | Дополнительные атрибуты
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` ( `url` свойство из карточки)
`Action.Submit` | `ac-action-submit` | `data-ac-data` ( `data` свойство из карточки)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` ( `id` из `<div>` содержащий карточке внутреннее)