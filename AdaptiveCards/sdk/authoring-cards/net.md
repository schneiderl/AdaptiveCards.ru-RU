---
title: Пакет SDK для .NET для адаптивных карт
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: fb1a79da288cbce77c4f684b384982feb96e7a8c
ms.sourcegitcommit: f8de9c02b92cd8927a18e59e5650c92b2b78db06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523842"
---
# <a name="net-sdk-for-authoring-cards"></a>Пакет SDK для .NET для создания карточек

Как описано на странице [Начало работы](../../authoring-cards/getting-started.md) , адаптивная карта является объектной моделью JSON. Библиотека .NET значительно упрощает работу с этим JSON.


## <a name="nuget-install"></a>Установка NuGet
Пакет `AdaptiveCards` NuGet предоставляет типы для работы с адаптивными картами в .NET

[![Установка NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a>Пример. Создание Адаптивекард и сериализация в JSON

В этом примере показано, как создать адаптивную карту с C# помощью стандартных объектов, а затем сериализовать ее в JSON для передачи по сети.

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

## <a name="example-parse-an-adaptivecard-from-json"></a>Пример. Анализ Адаптивекард из JSON

В этом примере показано, как анализировать полезные данные JSON в адаптивную карту. Это позволяет легко управлять объектной моделью или даже визуализировать адаптивные карты внутри приложения с помощью наших [пакетов SDK](../../rendering-cards/getting-started.md)для модуля подготовки отчетов.

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
