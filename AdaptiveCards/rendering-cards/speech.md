---
title: Обработка речи
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 64eeaefbc2ac775b69bd48cc853beb729cb2c37f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137997"
---
# <a name="handling-speech"></a><span data-ttu-id="490d5-102">Обработка речи</span><span class="sxs-lookup"><span data-stu-id="490d5-102">Handling speech</span></span>

<span data-ttu-id="490d5-103">Для поддержки речи у адаптивных карточек есть свойство `speak`, которое содержит сведения о том, как карточка должна быть прочитана вслух для пользователя.</span><span class="sxs-lookup"><span data-stu-id="490d5-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="490d5-104">Тег речи можно добавить с помощью [разметки SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="490d5-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="490d5-105">Язык SSML дает возможность управлять скоростью, тональностью и интонацией речи.</span><span class="sxs-lookup"><span data-stu-id="490d5-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="490d5-106">Он также поддерживает потоковую передачу звука и преобразование в речь текста из вашей службы, обеспечивая гибкие возможности настройки.</span><span class="sxs-lookup"><span data-stu-id="490d5-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="490d5-107">Существуют две модели использования свойства speak в ведущем приложении.</span><span class="sxs-lookup"><span data-stu-id="490d5-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="490d5-108">**При доставке**. Получив карточку, пользователь может использовать свойство speak для описания карточки в целом.</span><span class="sxs-lookup"><span data-stu-id="490d5-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="490d5-109">**По запросу**. Для расширения модели специальных возможностей предусмотрена поддержка схемой тега speak для отдельных элементов карточки.</span><span class="sxs-lookup"><span data-stu-id="490d5-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="490d5-110">Это позволяет клиентам читать каждый элемент для получателей, требующих применения специальных возможностей.</span><span class="sxs-lookup"><span data-stu-id="490d5-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

