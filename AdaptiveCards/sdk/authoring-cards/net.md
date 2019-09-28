---
title: Пакет SDK для .NET для адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 10400d5db3aac8ea60e5f03f5ab5d9b013211954
ms.sourcegitcommit: 4dd40521cd39313657f1dab642f49ff04098ba35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71343740"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="3e93b-102">Пакет SDK для .NET для создания карточек</span><span class="sxs-lookup"><span data-stu-id="3e93b-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="3e93b-103">Как описано на странице [Начало работы](../../authoring-cards/getting-started.md) , адаптивная карта является объектной моделью JSON.</span><span class="sxs-lookup"><span data-stu-id="3e93b-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="3e93b-104">Библиотека .NET значительно упрощает работу с этим JSON.</span><span class="sxs-lookup"><span data-stu-id="3e93b-104">The .NET library makes working with that JSON much easier.</span></span>


## <a name="nuget-install"></a><span data-ttu-id="3e93b-105">Установка NuGet</span><span class="sxs-lookup"><span data-stu-id="3e93b-105">NuGet Install</span></span>
<span data-ttu-id="3e93b-106">Пакет `AdaptiveCards` NuGet предоставляет типы для работы с адаптивными картами в .NET</span><span class="sxs-lookup"><span data-stu-id="3e93b-106">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="3e93b-107">[![Установка с помощью NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="3e93b-107">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="3e93b-108">Пример. Создание Адаптивекард и сериализация в JSON</span><span class="sxs-lookup"><span data-stu-id="3e93b-108">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="3e93b-109">В этом примере показано, как создать адаптивную карту с C# помощью стандартных объектов, а затем сериализовать ее в JSON для передачи по сети.</span><span class="sxs-lookup"><span data-stu-id="3e93b-109">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion(1, 0));

card.Body.Add(new AdaptiveTextBlock() 
{
    Text = "Hello",
    Size = AdaptiveTextSize.ExtraLarge
});

card.Body.Add(new AdaptiveImage() 
{
    Url = new Uri("http://adaptivecards.io/content/cats/1.png")
});

// serialize the card to JSON
string json = card.ToJson();
```

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="3e93b-110">Пример. Анализ Адаптивекард из JSON</span><span class="sxs-lookup"><span data-stu-id="3e93b-110">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="3e93b-111">В этом примере показано, как анализировать полезные данные JSON в адаптивную карту.</span><span class="sxs-lookup"><span data-stu-id="3e93b-111">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="3e93b-112">Это позволяет легко управлять объектной моделью или даже визуализировать адаптивные карты внутри приложения с помощью наших [пакетов SDK](../../rendering-cards/getting-started.md)для модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="3e93b-112">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient();
    var response = await client.GetAsync("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var json = await response.Content.ReadAsStringAsync();

    // Parse the JSON 
    AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

    // Get card from result
    AdaptiveCard card = result.Card;

    // Optional: check for any parse warnings
    // This includes things like unknown element "type"
    // or unknown properties on element
    IList<AdaptiveWarning> warnings = result.Warnings;
}
catch(AdaptiveSerializationException ex)
{
    // Failed to deserialize card 
    // This occurs from malformed JSON
    // or schema violations like required properties missing 
}
```
