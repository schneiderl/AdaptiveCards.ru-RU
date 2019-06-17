---
title: Обработка речи
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 64eeaefbc2ac775b69bd48cc853beb729cb2c37f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137997"
---
# <a name="handling-speech"></a><span data-ttu-id="69641-102">Обработка речи</span><span class="sxs-lookup"><span data-stu-id="69641-102">Handling speech</span></span>

<span data-ttu-id="69641-103">Для поддержки речи, содержит Адаптивная карты `speak` свойство, которое содержит сведения о как карточки должны считываться вслух пользователю.</span><span class="sxs-lookup"><span data-stu-id="69641-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="69641-104">Тег аннотируются с помощью [разметку SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="69641-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="69641-105">SSML дает возможность управления скорость, тон, перегиба речи.</span><span class="sxs-lookup"><span data-stu-id="69641-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="69641-106">Он даже позволяет потока аудио-или отрисовка TTS аудиопоток из собственной службы, обеспечивая высокую степень настройки.</span><span class="sxs-lookup"><span data-stu-id="69641-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="69641-107">Существуют 2 шаблоны для использования свойства произнести ведущим приложением:</span><span class="sxs-lookup"><span data-stu-id="69641-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="69641-108">**При доставке** — при доставке карточки клиента может предпочесть чтение свойства произношения для карты для описания карты в целом.</span><span class="sxs-lookup"><span data-stu-id="69641-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="69641-109">**по запросу** — для поддержки более мощную модель специальных возможностей каждого элемента тега speak поддерживает схемы.</span><span class="sxs-lookup"><span data-stu-id="69641-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="69641-110">Это позволяет клиентам читать каждый элемент получателям с требований по специальным возможностям.</span><span class="sxs-lookup"><span data-stu-id="69641-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

