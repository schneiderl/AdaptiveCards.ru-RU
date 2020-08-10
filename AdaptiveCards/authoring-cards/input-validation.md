---
title: Проверка входных данных
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
ms.openlocfilehash: 4c8aa73a218946944b25557eae141e231e8a6ac5
ms.sourcegitcommit: 2a394b75439b382d7bc3134078ecff02429617b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544970"
---
# <a name="input-validation"></a><span data-ttu-id="a93b1-102">Проверка входных данных</span><span class="sxs-lookup"><span data-stu-id="a93b1-102">Input Validation</span></span>

<span data-ttu-id="a93b1-103">В версии схемы 1.3 и более поздних версиях адаптивные карточки поддерживают проверку входных данных типов Input на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="a93b1-103">In versions 1.3 and later of the schema, AdaptiveCards supports client side input validation of Input types.</span></span>

### <a name="validation-properties"></a><span data-ttu-id="a93b1-104">Свойства проверки</span><span class="sxs-lookup"><span data-stu-id="a93b1-104">Validation Properties</span></span>

<span data-ttu-id="a93b1-105">Адаптивные карточки поддерживают следующие свойства для проверки:</span><span class="sxs-lookup"><span data-stu-id="a93b1-105">The following properties are supported for validation in AdaptiveCards:</span></span>

| <span data-ttu-id="a93b1-106">Входные данные</span><span class="sxs-lookup"><span data-stu-id="a93b1-106">Input</span></span> | <span data-ttu-id="a93b1-107">Свойства</span><span class="sxs-lookup"><span data-stu-id="a93b1-107">Properties</span></span> |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

<span data-ttu-id="a93b1-108">Свойство `errorMessage` доступно для входных данных всех типов. Оно позволяет указать, какое сообщение об ошибке должно отобразиться для пользователя, если он вводит недопустимое значение.</span><span class="sxs-lookup"><span data-stu-id="a93b1-108">An `errorMessage` property is available on all input types to specify what error a user should be shown if they enter an invalid value.</span></span> 

> [!NOTE]
>
> <span data-ttu-id="a93b1-109">Свойства min и max (включая maxLength) на некоторых платформах могут принудительно применяться непосредственно элементом управления.</span><span class="sxs-lookup"><span data-stu-id="a93b1-109">Min and max properties (including maxLength) on some platforms may be enforced directly by the control.</span></span> <span data-ttu-id="a93b1-110">Например, можно принудительно применить свойство min для Input.Date, запретив пользователям выбирать даты, предшествующие минимальному значению, в управляющем элементе выбора даты.</span><span class="sxs-lookup"><span data-stu-id="a93b1-110">For example, a min property on Input.Date may be enforced by not allowing users to select a date before the minimum in a date picker.</span></span> <span data-ttu-id="a93b1-111">В таком случае сообщение об ошибке может не отображаться.</span><span class="sxs-lookup"><span data-stu-id="a93b1-111">In that case, the error message may not be shown.</span></span>

## <a name="fields-to-be-validated-and-submitted"></a><span data-ttu-id="a93b1-112">Поля для проверки и отправки</span><span class="sxs-lookup"><span data-stu-id="a93b1-112">Fields to be validated and submitted</span></span>

<span data-ttu-id="a93b1-113">Входные данные будут проверены, когда пользователь щелкнет действие Action.Submit на карточке.</span><span class="sxs-lookup"><span data-stu-id="a93b1-113">Inputs will be validated when the user clicks on an Action.Submit action in the card.</span></span> <span data-ttu-id="a93b1-114">Для определенного действия Action.Submit будут проверяться и отправляться следующие входные данные:</span><span class="sxs-lookup"><span data-stu-id="a93b1-114">Those inputs which will be validated and submitted for a given Action.Submit action are:</span></span>

 - <span data-ttu-id="a93b1-115">входные данные, содержащиеся в карточке, на которой выбрано действие Action.Submit;</span><span class="sxs-lookup"><span data-stu-id="a93b1-115">Inputs on the same card as the Action.Submit</span></span>
 - <span data-ttu-id="a93b1-116">входные данные во всех родительских карточках той карточки, на которой выбрано действие Action.Submit, при использовании Action.ShowCard.</span><span class="sxs-lookup"><span data-stu-id="a93b1-116">Inputs on any parent cards of the card containing the Action.Submit in the case of a card under an Action.ShowCard</span></span>

<span data-ttu-id="a93b1-117">Если эти входные данные проходят проверку, значения в их полях будут возвращены клиенту.</span><span class="sxs-lookup"><span data-stu-id="a93b1-117">If those inputs pass validation, the values in their fields will be passed back to the client.</span></span> <span data-ttu-id="a93b1-118">Если данные не проходят проверку, для недопустимых входных данных отобразятся сообщения об ошибках и отправка не будет выполнена.</span><span class="sxs-lookup"><span data-stu-id="a93b1-118">If they do not pass validation, the error messages for the invalid inputs will be shown, and the submit will not be sent.</span></span>

> [!NOTE]
>
> <span data-ttu-id="a93b1-119">Входные данные **не** будут проверяться или отправляться, если они содержатся в карточке, которая является дочерней или родственной для карточки, на которой выбрано действие Action.Submit.</span><span class="sxs-lookup"><span data-stu-id="a93b1-119">Inputs will **not** be validated or submitted if they are on a card that is a child or sibling card of the card containing the Action.Submit.</span></span> <span data-ttu-id="a93b1-120">Сюда входят карточки, охватываемые Action.ShowCards в ActionSets в тексте карточки.</span><span class="sxs-lookup"><span data-stu-id="a93b1-120">This includes cards from Action.ShowCards in ActionSets in the body of that card.</span></span> <span data-ttu-id="a93b1-121">Это изменение в поведении наблюдается, начиная с версии отрисовщика 2.0. Оно характерно для карточек со всеми версиями схемы, независимо от того, используются ли свойства проверки входных данных.</span><span class="sxs-lookup"><span data-stu-id="a93b1-121">This is a change in behavior from renderer versions prior to 2.0, and applies to cards of all schema versions, regardless of whether input validation properties are used.</span></span> 

## <a name="other-considerations-and-known-issues"></a><span data-ttu-id="a93b1-122">Другие рекомендации и известные проблемы</span><span class="sxs-lookup"><span data-stu-id="a93b1-122">Other Considerations and Known Issues</span></span>

 - <span data-ttu-id="a93b1-123">Не рекомендуем создавать входные данные со свойствами проверки, которые не всегда могут быть видимыми из-за взаимодействия с Action.ToggleVisibility.</span><span class="sxs-lookup"><span data-stu-id="a93b1-123">It is not recommended to create inputs with validation properties that may not always be visible due to interaction with Action.ToggleVisibility.</span></span> <span data-ttu-id="a93b1-124">Сообщения об ошибках и визуальные индикаторы того, что входные данные недопустимы, не будут отображаться, если входные данные сейчас не видны. Это может вызвать замешательство у пользователей, которые не будут понимать, почему их отправка заблокирована.</span><span class="sxs-lookup"><span data-stu-id="a93b1-124">Error messages and visual indications that the input is invalid will not be shown if the input is not currently visible, which may cause confusion for users as to why their submit is blocked.</span></span>

 - <span data-ttu-id="a93b1-125">Поведение при проверке входных данных для основных элементов, использующих всплывающее окно для отображения карточек (значение `"actions":"showCard":"actionMode":"popup"` в конфигурации), недостаточно хорошо определено.</span><span class="sxs-lookup"><span data-stu-id="a93b1-125">Behavior of input validation for hosts using popup show cards using the  `"actions":"showCard":"actionMode":"popup"` value in their host config is not well defined.</span></span> <span data-ttu-id="a93b1-126">Возможно, в следующем выпуске всплывающее окно для отображения карточек будет отмечено как нерекомендуемое.</span><span class="sxs-lookup"><span data-stu-id="a93b1-126">Popup show cards may be deprecated in a future release.</span></span>

