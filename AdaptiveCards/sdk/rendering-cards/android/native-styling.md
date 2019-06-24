---
title: Собственные стили — пакет SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: ebb033c68b9aedcaacb1989ffb1bec48707a9026
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134242"
---
# <a name="native-styling---android"></a><span data-ttu-id="4d15f-102">Собственные стили — Android</span><span class="sxs-lookup"><span data-stu-id="4d15f-102">Native styling - Android</span></span>

<span data-ttu-id="4d15f-103">Собственные стили не поддерживаются средством визуализации для Android. В версии 1.2 появилась поддержка некоторых свойств стилей:</span><span class="sxs-lookup"><span data-stu-id="4d15f-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="4d15f-104">Характер действия</span><span class="sxs-lookup"><span data-stu-id="4d15f-104">Action Sentiment</span></span>

<span data-ttu-id="4d15f-105">Поддержка характера действия добавлена в **версии 1.2**. Хотя в ней не поддерживается столько стилей, как в других версиях, она позволяет задавать стили для действий *негативного* или *позитивного* характера. Чтобы применить для этих действий требуемый стиль, необходимо добавить следующую строку в файл проекта styles.xml.</span><span class="sxs-lookup"><span data-stu-id="4d15f-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="4d15f-106">Встроенное действие</span><span class="sxs-lookup"><span data-stu-id="4d15f-106">Inline Action</span></span>

<span data-ttu-id="4d15f-107">Текстовые входные данные и встроенное действие позволяют задавать стиль для визуализации действия.</span><span class="sxs-lookup"><span data-stu-id="4d15f-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="4d15f-108">Действие можно визуализировать в виде кнопки (adaptiveInlineAction) или изображения (adaptiveInlineActionImage).</span><span class="sxs-lookup"><span data-stu-id="4d15f-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="4d15f-109">Все имена элементов должны быть такими же, как в этом примере, так как средство визуализации распознает именно их.</span><span class="sxs-lookup"><span data-stu-id="4d15f-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>
