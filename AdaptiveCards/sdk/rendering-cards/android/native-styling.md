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

## <a name="actionshowcard"></a>Action.ShowCard

Action. Шовкард можно отформатировать, добавив стили в тему в styles.xml.

```styles.xml
 <item name="adaptiveShowCardAction">@style/adaptiveShowCardAction</item>
```