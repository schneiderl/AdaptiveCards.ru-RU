---
title: Обработка речи
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: daea48607376c84f0e0f0af9450cac7dcdf67c0e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552486"
---
# <a name="handling-speech"></a><span data-ttu-id="92ef0-102">Обработка речи</span><span class="sxs-lookup"><span data-stu-id="92ef0-102">Handling speech</span></span>

<span data-ttu-id="92ef0-103">Для поддержки речи, содержит Адаптивная карты `speak` свойство, которое содержит сведения о как карточки должны считываться вслух пользователю.</span><span class="sxs-lookup"><span data-stu-id="92ef0-103">To support speech adaptive Cards has the `speak` property which contains information on how a card shoudl be read aloud to a user.</span></span>

<span data-ttu-id="92ef0-104">Тег аннотируются с помощью [разметку SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="92ef0-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="92ef0-105">SSML дает возможность управления скорость, тон, перегиба речи.</span><span class="sxs-lookup"><span data-stu-id="92ef0-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="92ef0-106">Он даже позволяет потока аудио-или отрисовка TTS аудиопоток из собственной службы, обеспечивая высокую степень настройки.</span><span class="sxs-lookup"><span data-stu-id="92ef0-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="92ef0-107">Существуют 2 шаблоны для использования свойства произнести ведущим приложением:</span><span class="sxs-lookup"><span data-stu-id="92ef0-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="92ef0-108">**При доставке** — при доставке карточки клиента может предпочесть чтение свойства произношения для карты для описания карты в целом.</span><span class="sxs-lookup"><span data-stu-id="92ef0-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="92ef0-109">**по запросу** — для поддержки более мощную модель специальных возможностей каждого элемента тега speak поддерживает схемы.</span><span class="sxs-lookup"><span data-stu-id="92ef0-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="92ef0-110">Это позволяет клиентам читать каждый элемент получателям с требований по специальным возможностям.</span><span class="sxs-lookup"><span data-stu-id="92ef0-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

