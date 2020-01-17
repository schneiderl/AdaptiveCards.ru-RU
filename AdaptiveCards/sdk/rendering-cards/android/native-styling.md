---
title: Собственные стили — пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: d0c6b56e0497b78aa149f73dc1d32537689c0386
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145484"
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
