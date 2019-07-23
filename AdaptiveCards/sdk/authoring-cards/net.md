---
title: Пакет SDK для .NET для адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: fa86d83a8f20490ec286b69653099ac8cd81b8ef
ms.sourcegitcommit: 4d80c553ab574befa8c84706fd85d22077915745
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387345"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="dfb60-102">Пакет SDK для .NET для создания карточек</span><span class="sxs-lookup"><span data-stu-id="dfb60-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="dfb60-103">Как описано на странице [Начало работы](../../authoring-cards/getting-started.md) , адаптивная карта является объектной моделью JSON.</span><span class="sxs-lookup"><span data-stu-id="dfb60-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="dfb60-104">Библиотека .NET значительно упрощает работу с этим JSON.</span><span class="sxs-lookup"><span data-stu-id="dfb60-104">The .NET library makes working with that JSON much easier.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfb60-105">**Критические изменения с версии 0,5**</span><span class="sxs-lookup"><span data-stu-id="dfb60-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="dfb60-106">Пакет переименован из `Microsoft.AdaptiveCards` в`AdaptiveCards`</span><span class="sxs-lookup"><span data-stu-id="dfb60-106">Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`</span></span>
> 1. <span data-ttu-id="dfb60-107">Из-за частого конфликта имен с типами платформы все классы модели имеют префикс "адаптивно".</span><span class="sxs-lookup"><span data-stu-id="dfb60-107">Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive".</span></span> <span data-ttu-id="dfb60-108">Например, `TextBlock` теперь`AdaptiveTextBlock`</span><span class="sxs-lookup"><span data-stu-id="dfb60-108">E.g., `TextBlock` is now `AdaptiveTextBlock`</span></span>
> 1. <span data-ttu-id="dfb60-109">Все свойства "URI" были изменены с типа `string` на`Uri`</span><span class="sxs-lookup"><span data-stu-id="dfb60-109">All "uri" properties were changed from type `string` to `Uri`</span></span>
> 1. <span data-ttu-id="dfb60-110">Также были внесены некоторые изменения в схему из версии v 0,5 Preview, которые описаны [здесь](https://github.com/Microsoft/AdaptiveCards/pull/633) .</span><span class="sxs-lookup"><span data-stu-id="dfb60-110">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>


## <a name="nuget-install"></a><span data-ttu-id="dfb60-111">Установка NuGet</span><span class="sxs-lookup"><span data-stu-id="dfb60-111">NuGet Install</span></span>
<span data-ttu-id="dfb60-112">Пакет `AdaptiveCards` NuGet предоставляет типы для работы с адаптивными картами в .NET</span><span class="sxs-lookup"><span data-stu-id="dfb60-112">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="dfb60-113">[![Установка NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="dfb60-113">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="dfb60-114">Пример. Создание Адаптивекард и сериализация в JSON</span><span class="sxs-lookup"><span data-stu-id="dfb60-114">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="dfb60-115">В этом примере показано, как создать адаптивную карту с C# помощью стандартных объектов, а затем сериализовать ее в JSON для передачи по сети.</span><span class="sxs-lookup"><span data-stu-id="dfb60-115">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

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

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="dfb60-116">Пример. Анализ Адаптивекард из JSON</span><span class="sxs-lookup"><span data-stu-id="dfb60-116">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="dfb60-117">В этом примере показано, как анализировать полезные данные JSON в адаптивную карту.</span><span class="sxs-lookup"><span data-stu-id="dfb60-117">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="dfb60-118">Это позволяет легко управлять объектной моделью или даже визуализировать адаптивные карты внутри приложения с помощью наших [пакетов SDK](../../rendering-cards/getting-started.md)для модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="dfb60-118">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

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
