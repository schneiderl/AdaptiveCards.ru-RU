---
title: Расширение среды
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 9359db59201d3ddb27f7cb31bdf22985b73d29d1
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552576"
---
# <a name="extensibility"></a><span data-ttu-id="624e7-102">Расширение среды</span><span class="sxs-lookup"><span data-stu-id="624e7-102">Extensibility</span></span>

<span data-ttu-id="624e7-103">Каждый пакет SDK позволяет переопределять способ отрисовки любого элемента, или даже добавить поддержку совершенно новых элементов, определенных вами.</span><span class="sxs-lookup"><span data-stu-id="624e7-103">Each SDK allows you to override the rendering of any element, or even add support for entirely new elements that you define.</span></span>  <span data-ttu-id="624e7-104">Например, можно изменить `Input.Date` модуля подготовки отчетов, создавать собственный пользовательский элемент управления не теряя остальной части выходных данных модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="624e7-104">For example, you can change the `Input.Date` renderer to emit your own custom control while still retaining the rest of the output of the renderer.</span></span> <span data-ttu-id="624e7-105">Или можно добавить поддержку для пользовательской `Rating` элемент вам определить.</span><span class="sxs-lookup"><span data-stu-id="624e7-105">Or you can add support for a custom `Rating` element to you define.</span></span>