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
# <a name="native-styling---android"></a>Собственные стили — Android

Собственные стили не поддерживаются средством визуализации для Android. В версии 1.2 появилась поддержка некоторых свойств стилей:

## <a name="action-sentiment"></a>Характер действия

Поддержка характера действия добавлена в **версии 1.2**. Хотя в ней не поддерживается столько стилей, как в других версиях, она позволяет задавать стили для действий *негативного* или *позитивного* характера. Чтобы применить для этих действий требуемый стиль, необходимо добавить следующую строку в файл проекта styles.xml.

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>Встроенное действие

Текстовые входные данные и встроенное действие позволяют задавать стиль для визуализации действия. Действие можно визуализировать в виде кнопки (adaptiveInlineAction) или изображения (adaptiveInlineActionImage).

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> Все имена элементов должны быть такими же, как в этом примере, так как средство визуализации распознает именно их.
