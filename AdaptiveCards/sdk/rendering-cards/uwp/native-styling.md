---
title: Собственные стили - пакета SDK для универсальной платформы Windows
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3b95dc53c55c81fbbbbed6ee7605f86eb427a9
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552526"
---
# <a name="native-styling---uwp"></a>Собственные стили - универсальной платформы Windows

Во время конфигурации узла можно получить большинство определенным способом существует на каждой платформе, вполне вероятно, что необходимо сделать некоторые собственные стили на каждой платформе. 

UWP упрощает это, позволяя передавать ResourceDictionary для точного стилей, поведение, анимации, и т.д.

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
```
