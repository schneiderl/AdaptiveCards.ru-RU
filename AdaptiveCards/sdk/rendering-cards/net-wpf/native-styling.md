---
title: Собственный стиль — пакет SDK для .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ee5bec1a11f39ad69d40e57410c105b50ba45981
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552726"
---
# <a name="native-styling---net-wpf"></a>Собственный стиль — .NET WPF

Несмотря на то, что конфигурация узла будет наиболее актуальна на каждой платформе, вполне вероятно, что на каждой платформе придется выполнять некоторые собственные стили. 

WPF упрощает эту задачу, позволяя передавать ResourceDictionary для детализированного стиля, поведения, анимации и т. д.

| Элемент | Имена стилей |
|---|---|
| адаптивекард | Адаптивный адаптер| 
| Action. OpenUrl  | Адаптивный. Action. OpenUrl  |
| Action. Шовкард | Адаптивный. Action. Шовкард |
| Действие. Отправка  | Адаптивный. Action. Submit  |
| Column | Адаптивный. столбец, адаптивный. действие. TAP |
| ColumnSet | Адаптивный. столбец, адаптивный. Вертикалсепаратор |
| Контейнер | Адаптивный контейнер|
| Input. Choice | Адаптивный. input. Choice, адаптивный вход. Choice. ComboBox, адаптивный вход. Choice. CheckBox, адаптивный. input. Choice. Radio, адаптивный. input. Choice. Комбобокситем |
| Input. Date | Адаптивный. input. Text. Date
| Input. Number | Адаптивный. input. Text. Number |
| Input. Text | Адаптивный. input. Text |
| Входной. время | Адаптивный. input. Text. Time |
| Input. toggle| Адаптивный. input. toggle|
| Image  | Адаптивное изображение |
| ImageSet  | Адаптивный. Imageing |
| FactSet | Адаптивный факт, адаптивный факт. Title, адаптивный. факт. Value |
| TextBlock  | Адаптивный. TextBlock |

Этот пример словаря ресурсов XAML, который задает для фона всех элементов TextBlock значение голубого языка. Вам, возможно, потребуется нечто более сложное, чем это😁

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> **Примечание о создании образа на стороне сервера** Модуль подготовки отчетов WPF предоставляет `RenderCardToImageAsync` метод, который можно использовать для создания образа на стороне сервера. `ResourcesPath` Свойство следует использовать только в том случае, если оно используется в этой среде. Дополнительные сведения см. в документации по [рендерингу изображений](../net-image/getting-started.md) .