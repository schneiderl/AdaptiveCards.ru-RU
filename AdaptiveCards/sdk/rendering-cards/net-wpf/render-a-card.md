---
title: Визуализации карт - пакета SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 6bc476c79c6d06c7ecb770fb1c3e89eb55e81b9a
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553476"
---
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="d205f-102">Визуализации карт - .NET WPF</span><span class="sxs-lookup"><span data-stu-id="d205f-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="d205f-103">Вот способ визуализации карт, с помощью пакета SDK для .NET WPF.</span><span class="sxs-lookup"><span data-stu-id="d205f-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="d205f-104">**`Media` с помощью URL-адреса HTTPS не будет работать в WPF**</span><span class="sxs-lookup"><span data-stu-id="d205f-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="d205f-105">Из-за [ошибки в элементе управления WPF MediaElement](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) мы не может отобразить носители, которые обрабатываются с помощью HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d205f-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="d205f-106">Следует использовать URL-адреса HTTP в `Media` элемент, пока эта проблема устранена.</span><span class="sxs-lookup"><span data-stu-id="d205f-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="d205f-107">Создать экземпляр модуля подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="d205f-107">Instantiate a renderer</span></span>

<span data-ttu-id="d205f-108">Создайте экземпляр библиотеки модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="d205f-108">Create an instance of the renderer library.</span></span> 

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

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="d205f-109">Отображение карточки в XAML</span><span class="sxs-lookup"><span data-stu-id="d205f-109">Render a card to XAML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard()
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
    // Or the card exceeded the maxmimum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```

