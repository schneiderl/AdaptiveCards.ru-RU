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
# <a name="actions"></a>Действия

По умолчанию действия будет отображаться в виде кнопок на карте, но он работает в приложение, чтобы сделать их ожиданиям. Каждый пакет SDK входит эквивалент `OnAction` событие, которое необходимо обработать.

* **Action.OpenUrl** -открыть указанный `url`.  
* **Action.Submit** - принимающей результат отправки с последующей отправкой к источнику. Как можно отправлять в источник карты — полностью на ваше усмотрение.
* **Action.ShowCard** — вызывает диалоговое окно и отображает карточке вложенные в этот диалог. Обратите внимание, что достаточно для обработки этого, если `ShowCardActionMode` присваивается `popup`.