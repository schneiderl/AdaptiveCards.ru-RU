---
title: Класс Адаптивекард — Xamarin. пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 0f64bf635023271d8b40bf55fce079300aae7652
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146088"
---
# <a name="adaptivecard"></a>AdaptiveCard (адаптивная карточка)

```csharp
public class AdaptiveCard : Java.Lang.Object 
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a>Сводка

| Атрибуты | |
| ---- | --- |
| Действия | Действия, отображаемые на панели действий карточки. |
| BackgroundImage | Задает фоновое изображение карточки. |
| Body | Элементы карточки, отображаемые в основном регионе карты. |
| {2&gt;ElementType&lt;2} | Должно быть "Адаптивекард". |
| фаллбакктекст | Текст, отображаемый, когда клиент не поддерживает указанную версию (может содержать Markdown). |
| Высота | |
| инпутнецесситиндикаторс | |
| "Язык" | 2-буквенный язык ISO-639-1, используемый в карточке. Используется для локализации любых функций даты и времени. |
| MinHeight | Задает минимальную высоту карточки. |
| селектактион | Действие, которое будет вызываться при нажатии или выборе карточки. Action. Шовкард не поддерживается. |
| Speak | Указывает, что следует проголосовать за всю карточку. Это простой текст или фрагмент SSML. |
| "Стиль", | |
| Версия | Версия схемы, необходимая для этой карточки. Если клиент меньше этой версии, Фаллбакктекст будет подготовлен к просмотру. Примечание. версия не требуется для карточек в действии. Шовкард. Однако он необходим для карты верхнего уровня. |
| VerticalContentAlignment | Определяет, как содержимое должно выравниваться по вертикали в пределах контейнера. Относится только к картам фиксированной высоты или картам с указанным minHeight. |

&nbsp;

**Открытые конструкторы**

---

<a href="#ctor0"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor1"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

<a href="#ctor2"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor3"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

&nbsp;
| Открытые методы | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## <a name="public-constructors"></a>Открытые конструкторы
---

### <a id="ctor0"></a>адаптивекард
<p style='text-align:right'>Добавлено в версии 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight) 
```

| Параметры | |
| --- | --- |
| Версия | ```string``` |
| фаллбакктекст | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| Стиль | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a>адаптивекард
<p style='text-align:right'>Добавлено в версии 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body, 
                    BaseActionElementVector actions)
```

| Параметры | |
| --- | --- |
| Версия | ```string``` |
| фаллбакктекст | ```string``` |
| backgroundImage | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| Стиль | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| body | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| действия | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a>адаптивекард
<p style='text-align:right'>Добавлено в версии 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight) 
```

| Параметры | |
| --- | --- |
| Версия | ```string``` |
| фаллбакктекст | ```string``` |
| backgroundImage | ```string``` |
| Стиль | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a>адаптивекард
<p style='text-align:right'>Добавлено в версии 0,1</p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body,
                    BaseActionElementVector actions)

```

| Параметры | |
| --- | --- |
| Версия | ```string``` |
| фаллбакктекст | ```string``` |
| backgroundImage | ```string``` |
| Стиль | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| speak | ```string``` |
| language | ```string``` |
| verticalContentAlignment | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| height | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| minHeight | ```long``` |
| body | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| действия | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## <a name="public-methods"></a>Открытые методы
---
### <a id="deserializefromstring0"></a>десериализефромстринг
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

Десериализует заданную адаптивную карту как строку JSON для указанной версии модуля подготовки отчетов.

| Параметры | |
| --- | --- |
| жсонстринг | ```string``` |
| рендерерверсион | ```string``` |

| Возвращает | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a>Пример

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromstring1"></a>десериализефромстринг
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

Десериализует заданную адаптивную карту как строку JSON для указанной версии модуля подготовки отчетов, используя объект [парсеконтекст]() для обработки анализа настраиваемого элемента.

| Параметры | |
| --- | --- |
| жсонстринг | ```string``` |
| рендерерверсион | ```string``` |
| context | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| Возвращает | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a>Пример

```csharp
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a>макефаллбакктексткард
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

Десериализует заданную адаптивную карту как строку JSON для указанной версии модуля подготовки отчетов.

| Параметры | |
| --- | --- |
| фаллбакктекст | ```string``` |
| language | ```string``` |
| speak | ```string``` |

| Возвращает | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | Адаптивная карта, содержащая резервный текст для карточки унрендереабле |

#### <a name="sample"></a>Пример

```csharp
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a>Сериализуются
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public string Serialize ()
```

Сериализует адаптивную карту в форму строки JSON.

| Возвращает | |
| --- | --- |
| ```string``` | Адаптивная карта в виде строки JSON |

#### <a name="sample"></a>Пример

```csharp
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a>сериализетожсонвалуе
<p style='text-align:right'>Добавлено в версии 0.1.0</p>

```csharp
public JsonValue SerializeToJsonValue ()
```

Сериализует адаптивную карту в объект значения JSON.

| Возвращает | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### <a name="sample"></a>Пример

```csharp
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```