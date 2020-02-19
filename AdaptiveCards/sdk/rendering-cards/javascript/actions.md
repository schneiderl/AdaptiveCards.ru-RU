---
title: Действия — пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: bd88a0d5a98dd892887da897ad2a3ae214222e2b
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454737"
---
# <a name="actions---javascript"></a><span data-ttu-id="cc945-102">Действия — JavaScript</span><span class="sxs-lookup"><span data-stu-id="cc945-102">Actions - JavaScript</span></span>

```js
// Set the adaptive card's event handlers. onExecuteAction is invoked
// whenever an action is clicked in the card
adaptiveCard.onExecuteAction = function(action) { alert("Ow!"); }
```