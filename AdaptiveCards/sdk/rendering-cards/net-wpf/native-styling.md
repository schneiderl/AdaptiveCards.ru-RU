---
title: Собственные стили - пакета SDK для .NET WPF
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
# <a name="native-styling---net-wpf"></a>Собственные стили - .NET WPF

Во время конфигурации узла можно получить большинство определенным способом существует на каждой платформе, вполне вероятно, что необходимо сделать некоторые собственные стили на каждой платформе. 

WPF упрощает это, позволяя передавать ResourceDictionary для точного стилей, поведение, анимации, и т.д.

| Элемент | Имена стилей |
|---|---|
| AdaptiveCard | Adaptive.Card| 
| Action.OpenUrl  | Adaptive.Action.OpenUrl  |
| Action.ShowCard | Adaptive.Action.ShowCard |
| Action.Submit  | Adaptive.Action.Submit  |
| Column | Adaptive.Column Adaptive.Action.Tap |
| Набор столбцов | Adaptive.ColumnSet, Adaptive.VerticalSeparator |
| Контейнер | Adaptive.Container|
| Input.ChoiceSet | Adaptive.Input.ChoiceSet, Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox, Adaptive.Input.ChoiceSet.Radio, Adaptive.Input.ChoiceSet.ComboBoxItem |
| Input.Date | Adaptive.Input.Text.Date
| Input.Number | Adaptive.Input.Text.Number |
| Input.Text | Adaptive.Input.Text |
| Input.Time | Adaptive.Input.Text.Time |
| Input.Toggle| Adaptive.Input.Toggle|
| Изображение  | Adaptive.Image |
| ImageSet  | Adaptive.ImageSet |
| FactSet | Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value |
| TextBlock  | Adaptive.TextBlock |

Словарь ресурсов XAML, задает голубой фон все блоки TextBlock. Возможно, вы захотите, что что-то более сложные превышает это 😁

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
> **Примечание о создании образов на сервере** визуализатор WPF предоставляет `RenderCardToImageAsync` метод, который может использоваться для создания изображений на стороне сервера. Необходимо использовать только `ResourcesPath` свойства, если используется в этой среде. См. в разделе [визуализация изображений](../net-image/getting-started.md) документы для получения дополнительных сведений