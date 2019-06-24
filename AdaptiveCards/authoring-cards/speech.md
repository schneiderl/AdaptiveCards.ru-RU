---
title: Речь и дополнительная настройка
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 19e77b86da9d163f5fcf6a6074071a4638a8d793
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "59552616"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="b883a-102">Речь и дополнительная настройка</span><span class="sxs-lookup"><span data-stu-id="b883a-102">Speech and advanced customization</span></span>
<span data-ttu-id="b883a-103">В наше время стало привычным речевое взаимодействие с устройствами с помощью таких служб, как Кортана.</span><span class="sxs-lookup"><span data-stu-id="b883a-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="b883a-104">Адаптивные карточки изначально поддерживают функцию речи и позволяют реализовывать разные сценарии речевого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b883a-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="b883a-105">С помощью тега `speak` адаптивную карточку можно оптимизировать для использования на устройствах, экран которых не является основным пользовательским интерфейсом, например на приборной панели автомобиля при езде.</span><span class="sxs-lookup"><span data-stu-id="b883a-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="b883a-106">Свойство speak</span><span class="sxs-lookup"><span data-stu-id="b883a-106">Speak property</span></span>
<span data-ttu-id="b883a-107">Свойство `speak` обеспечивает поддержку речи и содержит текст, который озвучивается пользователю.</span><span class="sxs-lookup"><span data-stu-id="b883a-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="b883a-108">Параметры текста можно настраивать с помощью языка разметки синтеза речи ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span><span class="sxs-lookup"><span data-stu-id="b883a-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="b883a-109">SSML задает скорость, тональность и интонацию речи.</span><span class="sxs-lookup"><span data-stu-id="b883a-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="b883a-110">Он также поддерживает потоковую передачу звука и преобразование в речь текста из других служб, обеспечивая гибкие возможности настройки.</span><span class="sxs-lookup"><span data-stu-id="b883a-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="b883a-111">Существуют две модели использования свойства speak в целевом приложении:</span><span class="sxs-lookup"><span data-stu-id="b883a-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="b883a-112">**При доставке**. Получив карточку, пользователь может использовать свойство speak для описания карты в целом.</span><span class="sxs-lookup"><span data-stu-id="b883a-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="b883a-113">**По запросу** Для расширения модели специальных возможностей предусмотрена поддержка тега speak отдельными элементами карточки.</span><span class="sxs-lookup"><span data-stu-id="b883a-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="b883a-114">Пользователь может может использовать свойства speak, заданные отдельным элементам карточки.</span><span class="sxs-lookup"><span data-stu-id="b883a-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="b883a-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="b883a-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="b883a-116">Оформление содержимого речи</span><span class="sxs-lookup"><span data-stu-id="b883a-116">Speech content design</span></span>

<span data-ttu-id="b883a-117">Содержимое, предназначенное для озвучивания, отличается от содержимого для визуального отображения.</span><span class="sxs-lookup"><span data-stu-id="b883a-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="b883a-118">При создании карточки необходимо учитывать визуальный аспект ее восприятия получателем.</span><span class="sxs-lookup"><span data-stu-id="b883a-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="b883a-119">Если карточка поддерживает функцию речи, следует продумать, как описать ее содержимое удобным для пользователя способом.</span><span class="sxs-lookup"><span data-stu-id="b883a-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
