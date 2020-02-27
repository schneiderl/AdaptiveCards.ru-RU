---
title: Действия
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454947"
---
# <a name="actions"></a>Действия

По умолчанию действия отображаются в виде кнопок на карточке, но приложение может сделать их поведение таким, каким вам требуется. Каждый пакет SDK содержит эквивалент события `OnAction`, которое необходимо обрабатывать.

* **Action.OpenUrl**: открытие указанного `url`.  
* **Action.Submit**: получение результата отправки и его пересылка в источник. Способ отправки в источник карточки полностью зависит от вас.
* **Action.ShowCard**: вызывает диалоговое окно и отображает в нем вложенную карточку. Обратите внимание на то, что это действие нужно обрабатывать, только если параметр `ShowCardActionMode` имеет значение `popup`.