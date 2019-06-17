---
title: Расширение среды
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: b6d303e15f8d51aa3f1f944304b1fa4f11f9c206
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138117"
---
# <a name="extensibility"></a><span data-ttu-id="b9105-102">Расширение среды</span><span class="sxs-lookup"><span data-stu-id="b9105-102">Extensibility</span></span>

<span data-ttu-id="b9105-103">Каждый пакет SDK позволяет переопределять способ отрисовки любого элемента, или даже добавить поддержку совершенно новых элементов, определенных вами.</span><span class="sxs-lookup"><span data-stu-id="b9105-103">Each SDK allows you to override the rendering of any element, or even add support for entirely new elements that you define.</span></span>  <span data-ttu-id="b9105-104">Например, можно изменить `Input.Date` модуля подготовки отчетов, создавать собственный пользовательский элемент управления не теряя остальной части выходных данных модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="b9105-104">For example, you can change the `Input.Date` renderer to emit your own custom control while still retaining the rest of the output of the renderer.</span></span> <span data-ttu-id="b9105-105">Или можно добавить поддержку для пользовательской `Rating` элемент вам определить.</span><span class="sxs-lookup"><span data-stu-id="b9105-105">Or you can add support for a custom `Rating` element to you define.</span></span>

<span data-ttu-id="b9105-106">Пример кода, разверните **SDK** "->" узел слева **визуализации карт** -> **SDK, вы бы хотели использовать**  ->   **Расширяемость**</span><span class="sxs-lookup"><span data-stu-id="b9105-106">For example code, please expand the **SDK** node on the left -> **Rendering Cards** -> **the SDK you'd like to use** -> **Extensibility**</span></span>
