---
title: Визуализации карт - .NET SDK для визуализации изображения
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ae32007d75abe4fb452ee48e32dd4e9bea8dfa4f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552496"
---
# <a name="render-a-card---net-image"></a><span data-ttu-id="dabbb-102">Визуализации карт - образа .NET</span><span class="sxs-lookup"><span data-stu-id="dabbb-102">Render a card - .NET Image</span></span>

<span data-ttu-id="dabbb-103">Вот способ визуализации карт, с помощью пакета SDK для .NET образа.</span><span class="sxs-lookup"><span data-stu-id="dabbb-103">Here's how to render a card using the .NET Image SDK.</span></span>

```csharp
try
{
    // A URL that returns an Adaptive Card JSON payload
    var cardUrl = "http://adaptivecards.io/payloads/ActivityUpdate.json";

    // Timeout after 30 seconds
    var cts = new CancellationTokenSource(TimeSpan.FromSeconds(30));

    // Get the JSON from the card URL
    var client = new HttpClient();
    var response = await client.GetAsync(cardUrl, cts.Token);
    var json = await response.Content.ReadAsStringAsync();

    // Parse the Adaptive Card JSON
    AdaptiveCardParseResult parseResult = AdaptiveCard.FromJson(json);
    AdaptiveCard card = parseResult.Card;

    // Create a host config with no interactivity 
    // (buttons in images would be deceiving)
    AdaptiveHostConfig hostConfig = new AdaptiveHostConfig()
    {
        SupportsInteractivity = false
    };

    // Create a renderer
    AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(hostConfig);

    // Set any XAML resource Dictionary if you have one
    //renderer.ResourcesPath = <path-to-your-resourcedictionary.xaml>;

    // Render the card to png
    // Set createStaThread to true if running from a server
    RenderedAdaptiveCardImage renderedCard =
        await renderer.RenderCardToImageAsync(card, createStaThread: true, cancellationToken: cts.Token);
}
catch (OperationCanceledException)
{
    // Timed out
}
catch (Exception ex)
{
    // Log failure
}
```