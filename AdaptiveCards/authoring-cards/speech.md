---
title: Речи и дополнительная настройка
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 19e77b86da9d163f5fcf6a6074071a4638a8d793
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552616"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="74916-102">Речи и дополнительная настройка</span><span class="sxs-lookup"><span data-stu-id="74916-102">Speech and advanced customization</span></span>
<span data-ttu-id="74916-103">Мы живем в эру взаимодействия речи с помощью служб, таких как Cortana.</span><span class="sxs-lookup"><span data-stu-id="74916-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="74916-104">Адаптивная карты, позволяют с первого же дня речи, "холодный" новых сценариев, в руки full.</span><span class="sxs-lookup"><span data-stu-id="74916-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="74916-105">`speak` Тег позволяет инструмент adaptive Cards доставляются в среде, где визуального представления не первичный, такие как на панели мониторинга автомобиль рулем.</span><span class="sxs-lookup"><span data-stu-id="74916-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="74916-106">Произнесите свойство</span><span class="sxs-lookup"><span data-stu-id="74916-106">Speak property</span></span>
<span data-ttu-id="74916-107">Для поддержки речи, у нас есть `speak` свойство, которое содержит текст для озвучивания для пользователя.</span><span class="sxs-lookup"><span data-stu-id="74916-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="74916-108">Текст можно обозначить с помощью языка разметки синтеза речи ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span><span class="sxs-lookup"><span data-stu-id="74916-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="74916-109">SSML контролирует скорость, тон и перегиба речи.</span><span class="sxs-lookup"><span data-stu-id="74916-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="74916-110">Он даже позволяет потока аудио-или отрисовка TTS аудиопоток из собственной службы, они предоставляют большую гибкость для настройки.</span><span class="sxs-lookup"><span data-stu-id="74916-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="74916-111">Существуют две модели для использования свойства произнести ведущим приложением:</span><span class="sxs-lookup"><span data-stu-id="74916-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="74916-112">**При доставке** — при доставке карточки, клиент может предпочесть чтение свойства произношения для карты для описания карты в целом.</span><span class="sxs-lookup"><span data-stu-id="74916-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="74916-113">**По запросу** — для поддержки более мощную модель специальных возможностей, поддерживает схемы, speak тега для каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="74916-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="74916-114">Клиент может считывать свойства произношения для каждого элемента в карте.</span><span class="sxs-lookup"><span data-stu-id="74916-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="74916-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="74916-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="74916-116">Конструктор содержимого речи</span><span class="sxs-lookup"><span data-stu-id="74916-116">Speech content design</span></span>

<span data-ttu-id="74916-117">Содержимое, разработанное для распознавания речи отличается от содержимого, разработанного для визуального отображения элементов.</span><span class="sxs-lookup"><span data-stu-id="74916-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="74916-118">При создании карточки, вы разрабатываете всего качество для представления сведений пользователю способом, который delights их.</span><span class="sxs-lookup"><span data-stu-id="74916-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="74916-119">При разработке для распознавания речи, следует подумать о том, как словесно информацию способом, который delights пользователя.</span><span class="sxs-lookup"><span data-stu-id="74916-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
