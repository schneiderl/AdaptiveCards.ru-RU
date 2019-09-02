---
title: Действия
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 42ba1ca4ba2ecd508bdee2f04061293d48349aab
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553376"
---
# <a name="actions"></a>Действия

По умолчанию действия отображаются в виде кнопок на карточке, но приложение может сделать их поведение таким, каким вам требуется. Каждый пакет SDK содержит эквивалент события `OnAction`, которое необходимо обрабатывать.

* **Action.OpenUrl**: открытие указанного `url`.  
* **Action.Submit**: получение результата отправки и его пересылка в источник. Способ отправки в источник карточки полностью зависит от вас.
* **Action.ShowCard**: вызывает диалоговое окно и отображает в нем вложенную карточку. Обратите внимание на то, что это действие нужно обрабатывать, только если параметр `ShowCardActionMode` имеет значение `popup`.