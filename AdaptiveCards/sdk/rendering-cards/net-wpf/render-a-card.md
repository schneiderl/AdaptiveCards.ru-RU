---
title: Визуализация карточки — пакет SDK .NET для WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f847b83a17456dbf80f869ef8ef0df699e57f50e
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134300"
---
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="2348d-102">Визуализация карточки — .NET WPF</span><span class="sxs-lookup"><span data-stu-id="2348d-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="2348d-103">Преобразовать карточку для просмотра можно с помощью пакета SDK .NET для WPF следующим образом.</span><span class="sxs-lookup"><span data-stu-id="2348d-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="2348d-104">**`Media` с URL-адресами HTTPS не будет работать в WPF**.</span><span class="sxs-lookup"><span data-stu-id="2348d-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="2348d-105">Из-за [ошибки в элементе управления WPF MediaElement](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) мультимедийное содержимое, доступное по протоколу HTTPS, не отображается.</span><span class="sxs-lookup"><span data-stu-id="2348d-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="2348d-106">В элементе `Media` следует использовать URL-адреса HTTP, пока эта проблема не будет устранена.</span><span class="sxs-lookup"><span data-stu-id="2348d-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="2348d-107">Создание экземпляра средства визуализации</span><span class="sxs-lookup"><span data-stu-id="2348d-107">Instantiate a renderer</span></span>

<span data-ttu-id="2348d-108">На этом шаге необходимо создать экземпляр библиотеки средства визуализации.</span><span class="sxs-lookup"><span data-stu-id="2348d-108">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Wpf;
// ...

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// If using the Xceed package, enable the enhanced input
renderer.UseXceedElementRenderers();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion;
```

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="2348d-109">Визуализация карточки в формате XAML</span><span class="sxs-lookup"><span data-stu-id="2348d-109">Render a card to XAML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard("1.0")
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the FrameworkElement
    // Add this to your app's UI somewhere
    FrameworkElement fe = renderedCard.FrameworkElement;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```

