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
# <a name="net-sdk-for-authoring-cards"></a>Пакет SDK для .NET для создания карт

Как было описано в [Приступая к работе](../../authoring-cards/getting-started.md) страницы, инструмент Adaptive Cards — это объектная модель JSON. Библиотека .NET значительно упрощает работу с код JSON.

> [!IMPORTANT]
> **Критические изменения из v0.5**
> 
> 1. Пакет переименован из `Microsoft.AdaptiveCards` для `AdaptiveCards`
> 1. Из-за конфликтов часто имен типов framework все классы модели иметь префикс с «Adaptive». Например `TextBlock` теперь `AdaptiveTextBlock`
> 1. Все свойства «uri» были изменены из типа `string` для `Uri`
> 1. Также были внесены некоторые изменения схемы из v0.5 предварительной версии, которые являются [описанную в этой статье](https://github.com/Microsoft/AdaptiveCards/pull/633)


## <a name="nuget-install"></a>Программа установки NuGet
`AdaptiveCards` Пакет NuGet предоставляет типы для работы с адаптивной карточек в .NET

[![Программа установки NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a>Пример. Создание AdaptiveCard и сериализации в JSON

В этом примере показано, как построить инструмент Adaptive Cards с использованием стандарта C# объектов и затем выполнить его сериализацию в JSON для передачи по сети.

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

## <a name="example-parse-an-adaptivecard-from-json"></a>Пример. Синтаксический анализ AdaptiveCard из JSON

В этом примере показано, как выполнить синтаксический анализ полезных данных JSON в инструмент Adaptive cards. Это позволяет легко управлять объектной моделью или даже отображаться адаптивной карты внутри приложения с помощью наших [модуль подготовки отчетов пакеты SDK](../../rendering-cards/getting-started.md).

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
