---
title: Пакет SDK для .NET для адаптивной карт
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 37dec7651a574194eb00d46014431dfb5764f9b7
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553746"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="a1a0e-102">Пакет SDK для .NET для создания карт</span><span class="sxs-lookup"><span data-stu-id="a1a0e-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="a1a0e-103">Как было описано в [Приступая к работе](../../authoring-cards/getting-started.md) страницы, инструмент Adaptive Cards — это объектная модель JSON.</span><span class="sxs-lookup"><span data-stu-id="a1a0e-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="a1a0e-104">Библиотека .NET значительно упрощает работу с код JSON.</span><span class="sxs-lookup"><span data-stu-id="a1a0e-104">The .NET library makes working with that JSON much easier.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1a0e-105">**Критические изменения из v0.5**</span><span class="sxs-lookup"><span data-stu-id="a1a0e-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="a1a0e-106">Пакет переименован из `Microsoft.AdaptiveCards` для `AdaptiveCards`</span><span class="sxs-lookup"><span data-stu-id="a1a0e-106">Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`</span></span>
> 1. <span data-ttu-id="a1a0e-107">Из-за конфликтов часто имен типов framework все классы модели иметь префикс с «Adaptive».</span><span class="sxs-lookup"><span data-stu-id="a1a0e-107">Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive".</span></span> <span data-ttu-id="a1a0e-108">Например `TextBlock` теперь `AdaptiveTextBlock`</span><span class="sxs-lookup"><span data-stu-id="a1a0e-108">E.g., `TextBlock` is now `AdaptiveTextBlock`</span></span>
> 1. <span data-ttu-id="a1a0e-109">Все свойства «uri» были изменены из типа `string` для `Uri`</span><span class="sxs-lookup"><span data-stu-id="a1a0e-109">All "uri" properties were changed from type `string` to `Uri`</span></span>
> 1. <span data-ttu-id="a1a0e-110">Также были внесены некоторые изменения схемы из v0.5 предварительной версии, которые являются [описанную в этой статье](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="a1a0e-110">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>


## <a name="nuget-install"></a><span data-ttu-id="a1a0e-111">Программа установки NuGet</span><span class="sxs-lookup"><span data-stu-id="a1a0e-111">NuGet Install</span></span>
<span data-ttu-id="a1a0e-112">`AdaptiveCards` Пакет NuGet предоставляет типы для работы с адаптивной карточек в .NET</span><span class="sxs-lookup"><span data-stu-id="a1a0e-112">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="a1a0e-113">[![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="a1a0e-113">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="a1a0e-114">Пример. Создание AdaptiveCard и сериализации в JSON</span><span class="sxs-lookup"><span data-stu-id="a1a0e-114">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="a1a0e-115">В этом примере показано, как построить инструмент Adaptive Cards с использованием стандарта C# объектов и затем выполнить его сериализацию в JSON для передачи по сети.</span><span class="sxs-lookup"><span data-stu-id="a1a0e-115">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard();

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

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="a1a0e-116">Пример. Синтаксический анализ AdaptiveCard из JSON</span><span class="sxs-lookup"><span data-stu-id="a1a0e-116">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="a1a0e-117">В этом примере показано, как выполнить синтаксический анализ полезных данных JSON в инструмент Adaptive cards.</span><span class="sxs-lookup"><span data-stu-id="a1a0e-117">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="a1a0e-118">Это позволяет легко управлять объектной моделью или даже отображаться адаптивной карты внутри приложения с помощью наших [модуль подготовки отчетов пакеты SDK](../../rendering-cards/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="a1a0e-118">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var response = await client.GetAsync(cardUrl);
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
