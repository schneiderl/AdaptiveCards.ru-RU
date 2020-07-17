---
title: Собственные стили — пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 8d5dd9bbf17800c55aae1d416b7e6d80ac697b25
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417611"
---
# <a name="native-styling---android"></a><span data-ttu-id="10efe-102">Собственные стили — Android</span><span class="sxs-lookup"><span data-stu-id="10efe-102">Native styling - Android</span></span>

<span data-ttu-id="10efe-103">Собственные стили не поддерживаются средством визуализации для Android. В версии 1.2 появилась поддержка некоторых свойств стилей:</span><span class="sxs-lookup"><span data-stu-id="10efe-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="10efe-104">Характер действия</span><span class="sxs-lookup"><span data-stu-id="10efe-104">Action Sentiment</span></span>

<span data-ttu-id="10efe-105">Поддержка характера действия добавлена в **версии 1.2**. Хотя в ней не поддерживается столько стилей, как в других версиях, она позволяет задавать стили для действий *негативного* или *позитивного* характера. Чтобы применить для этих действий требуемый стиль, необходимо добавить следующую строку в файл проекта styles.xml.</span><span class="sxs-lookup"><span data-stu-id="10efe-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="10efe-106">Встроенное действие</span><span class="sxs-lookup"><span data-stu-id="10efe-106">Inline Action</span></span>

<span data-ttu-id="10efe-107">Текстовые входные данные и встроенное действие позволяют задавать стиль для визуализации действия.</span><span class="sxs-lookup"><span data-stu-id="10efe-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="10efe-108">Действие можно визуализировать в виде кнопки (adaptiveInlineAction) или изображения (adaptiveInlineActionImage).</span><span class="sxs-lookup"><span data-stu-id="10efe-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="10efe-109">Все имена элементов должны быть такими же, как в этом примере, так как средство визуализации распознает именно их.</span><span class="sxs-lookup"><span data-stu-id="10efe-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>

## <a name="actionshowcard"></a><span data-ttu-id="10efe-110">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="10efe-110">Action.ShowCard</span></span>

<span data-ttu-id="10efe-111">Action. Шовкард можно отформатировать, добавив стили в тему в styles.xml.</span><span class="sxs-lookup"><span data-stu-id="10efe-111">Action.ShowCard can be styled by adding styles to your theme in styles.xml.</span></span>

```styles.xml
 <item name="adaptiveShowCardAction">@style/adaptiveShowCardAction</item>
```