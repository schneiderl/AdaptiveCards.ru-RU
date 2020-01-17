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
# <a name="adaptivecard"></a><span data-ttu-id="8323f-102">AdaptiveCard (адаптивная карточка)</span><span class="sxs-lookup"><span data-stu-id="8323f-102">AdaptiveCard</span></span>

```csharp
public class AdaptiveCard : Java.Lang.Object 
```

<span data-ttu-id="8323f-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="8323f-103">**Namespace**</span></span>

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a><span data-ttu-id="8323f-104">Сводка</span><span class="sxs-lookup"><span data-stu-id="8323f-104">Summary</span></span>

| <span data-ttu-id="8323f-105">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8323f-105">Attributes</span></span> | |
| ---- | --- |
| <span data-ttu-id="8323f-106">Действия</span><span class="sxs-lookup"><span data-stu-id="8323f-106">Actions</span></span> | <span data-ttu-id="8323f-107">Действия, отображаемые на панели действий карточки.</span><span class="sxs-lookup"><span data-stu-id="8323f-107">The Actions to show in the card’s action bar.</span></span> |
| <span data-ttu-id="8323f-108">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="8323f-108">BackgroundImage</span></span> | <span data-ttu-id="8323f-109">Задает фоновое изображение карточки.</span><span class="sxs-lookup"><span data-stu-id="8323f-109">Specifies the background image of the card.</span></span> |
| <span data-ttu-id="8323f-110">Body</span><span class="sxs-lookup"><span data-stu-id="8323f-110">Body</span></span> | <span data-ttu-id="8323f-111">Элементы карточки, отображаемые в основном регионе карты.</span><span class="sxs-lookup"><span data-stu-id="8323f-111">The card elements to show in the primary card region.</span></span> |
| <span data-ttu-id="8323f-112">{2&gt;ElementType&lt;2}</span><span class="sxs-lookup"><span data-stu-id="8323f-112">ElementType</span></span> | <span data-ttu-id="8323f-113">Должно быть "Адаптивекард".</span><span class="sxs-lookup"><span data-stu-id="8323f-113">Must be "AdaptiveCard".</span></span> |
| <span data-ttu-id="8323f-114">фаллбакктекст</span><span class="sxs-lookup"><span data-stu-id="8323f-114">FallbackText</span></span> | <span data-ttu-id="8323f-115">Текст, отображаемый, когда клиент не поддерживает указанную версию (может содержать Markdown).</span><span class="sxs-lookup"><span data-stu-id="8323f-115">Text shown when the client doesn’t support the version specified (may contain markdown).</span></span> |
| <span data-ttu-id="8323f-116">Высота</span><span class="sxs-lookup"><span data-stu-id="8323f-116">Height</span></span> | |
| <span data-ttu-id="8323f-117">инпутнецесситиндикаторс</span><span class="sxs-lookup"><span data-stu-id="8323f-117">InputNecessityIndicators</span></span> | |
| <span data-ttu-id="8323f-118">"Язык"</span><span class="sxs-lookup"><span data-stu-id="8323f-118">Language</span></span> | <span data-ttu-id="8323f-119">2-буквенный язык ISO-639-1, используемый в карточке.</span><span class="sxs-lookup"><span data-stu-id="8323f-119">The 2-letter ISO-639-1 language used in the card.</span></span> <span data-ttu-id="8323f-120">Используется для локализации любых функций даты и времени.</span><span class="sxs-lookup"><span data-stu-id="8323f-120">Used to localize any date/time functions.</span></span> |
| <span data-ttu-id="8323f-121">MinHeight</span><span class="sxs-lookup"><span data-stu-id="8323f-121">MinHeight</span></span> | <span data-ttu-id="8323f-122">Задает минимальную высоту карточки.</span><span class="sxs-lookup"><span data-stu-id="8323f-122">Specifies the minimum height of the card.</span></span> |
| <span data-ttu-id="8323f-123">селектактион</span><span class="sxs-lookup"><span data-stu-id="8323f-123">SelectAction</span></span> | <span data-ttu-id="8323f-124">Действие, которое будет вызываться при нажатии или выборе карточки.</span><span class="sxs-lookup"><span data-stu-id="8323f-124">An Action that will be invoked when the card is tapped or selected.</span></span> <span data-ttu-id="8323f-125">Action. Шовкард не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="8323f-125">Action.ShowCard is not supported.</span></span> |
| <span data-ttu-id="8323f-126">Speak</span><span class="sxs-lookup"><span data-stu-id="8323f-126">Speak</span></span> | <span data-ttu-id="8323f-127">Указывает, что следует проголосовать за всю карточку.</span><span class="sxs-lookup"><span data-stu-id="8323f-127">Specifies what should be spoken for this entire card.</span></span> <span data-ttu-id="8323f-128">Это простой текст или фрагмент SSML.</span><span class="sxs-lookup"><span data-stu-id="8323f-128">This is simple text or SSML fragment.</span></span> |
| <span data-ttu-id="8323f-129">"Стиль",</span><span class="sxs-lookup"><span data-stu-id="8323f-129">Style</span></span> | |
| <span data-ttu-id="8323f-130">Версия</span><span class="sxs-lookup"><span data-stu-id="8323f-130">Version</span></span> | <span data-ttu-id="8323f-131">Версия схемы, необходимая для этой карточки.</span><span class="sxs-lookup"><span data-stu-id="8323f-131">Schema version that this card requires.</span></span> <span data-ttu-id="8323f-132">Если клиент меньше этой версии, Фаллбакктекст будет подготовлен к просмотру.</span><span class="sxs-lookup"><span data-stu-id="8323f-132">If a client is lower than this version, the fallbackText will be rendered.</span></span> <span data-ttu-id="8323f-133">Примечание. версия не требуется для карточек в действии. Шовкард.</span><span class="sxs-lookup"><span data-stu-id="8323f-133">NOTE: Version is not required for cards within an Action.ShowCard.</span></span> <span data-ttu-id="8323f-134">Однако он необходим для карты верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="8323f-134">However, it is required for the top-level card.</span></span> |
| <span data-ttu-id="8323f-135">VerticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="8323f-135">VerticalContentAlignment</span></span> | <span data-ttu-id="8323f-136">Определяет, как содержимое должно выравниваться по вертикали в пределах контейнера.</span><span class="sxs-lookup"><span data-stu-id="8323f-136">Defines how the content should be aligned vertically within the container.</span></span> <span data-ttu-id="8323f-137">Относится только к картам фиксированной высоты или картам с указанным minHeight.</span><span class="sxs-lookup"><span data-stu-id="8323f-137">Only relevant for fixed-height cards, or cards with a minHeight specified.</span></span> |

&nbsp;

<span data-ttu-id="8323f-138">**Открытые конструкторы**</span><span class="sxs-lookup"><span data-stu-id="8323f-138">**Public Constructors**</span></span>

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
| <span data-ttu-id="8323f-139">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="8323f-139">Public methods</span></span> | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## <a name="public-constructors"></a><span data-ttu-id="8323f-140">Открытые конструкторы</span><span class="sxs-lookup"><span data-stu-id="8323f-140">Public Constructors</span></span>
---

### <a id="ctor0"></a><span data-ttu-id="8323f-141">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="8323f-141">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-142">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="8323f-142">Added in version 0.1</span></span></p>

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

| <span data-ttu-id="8323f-143">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-143">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-144">Версия</span><span class="sxs-lookup"><span data-stu-id="8323f-144">version</span></span> | ```string``` |
| <span data-ttu-id="8323f-145">фаллбакктекст</span><span class="sxs-lookup"><span data-stu-id="8323f-145">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="8323f-146">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="8323f-146">backgroundImage</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| <span data-ttu-id="8323f-147">Стиль</span><span class="sxs-lookup"><span data-stu-id="8323f-147">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="8323f-148">speak</span><span class="sxs-lookup"><span data-stu-id="8323f-148">speak</span></span> | ```string``` |
| <span data-ttu-id="8323f-149">language</span><span class="sxs-lookup"><span data-stu-id="8323f-149">language</span></span> | ```string``` |
| <span data-ttu-id="8323f-150">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="8323f-150">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="8323f-151">height</span><span class="sxs-lookup"><span data-stu-id="8323f-151">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="8323f-152">minHeight</span><span class="sxs-lookup"><span data-stu-id="8323f-152">minHeight</span></span> | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a><span data-ttu-id="8323f-153">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="8323f-153">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-154">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="8323f-154">Added in version 0.1</span></span></p>

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

| <span data-ttu-id="8323f-155">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-155">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-156">Версия</span><span class="sxs-lookup"><span data-stu-id="8323f-156">version</span></span> | ```string``` |
| <span data-ttu-id="8323f-157">фаллбакктекст</span><span class="sxs-lookup"><span data-stu-id="8323f-157">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="8323f-158">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="8323f-158">backgroundImage</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| <span data-ttu-id="8323f-159">Стиль</span><span class="sxs-lookup"><span data-stu-id="8323f-159">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="8323f-160">speak</span><span class="sxs-lookup"><span data-stu-id="8323f-160">speak</span></span> | ```string``` |
| <span data-ttu-id="8323f-161">language</span><span class="sxs-lookup"><span data-stu-id="8323f-161">language</span></span> | ```string``` |
| <span data-ttu-id="8323f-162">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="8323f-162">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="8323f-163">height</span><span class="sxs-lookup"><span data-stu-id="8323f-163">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="8323f-164">minHeight</span><span class="sxs-lookup"><span data-stu-id="8323f-164">minHeight</span></span> | ```long``` |
| <span data-ttu-id="8323f-165">body</span><span class="sxs-lookup"><span data-stu-id="8323f-165">body</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| <span data-ttu-id="8323f-166">действия</span><span class="sxs-lookup"><span data-stu-id="8323f-166">actions</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a><span data-ttu-id="8323f-167">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="8323f-167">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-168">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="8323f-168">Added in version 0.1</span></span></p>

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

| <span data-ttu-id="8323f-169">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-169">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-170">Версия</span><span class="sxs-lookup"><span data-stu-id="8323f-170">version</span></span> | ```string``` |
| <span data-ttu-id="8323f-171">фаллбакктекст</span><span class="sxs-lookup"><span data-stu-id="8323f-171">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="8323f-172">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="8323f-172">backgroundImage</span></span> | ```string``` |
| <span data-ttu-id="8323f-173">Стиль</span><span class="sxs-lookup"><span data-stu-id="8323f-173">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="8323f-174">speak</span><span class="sxs-lookup"><span data-stu-id="8323f-174">speak</span></span> | ```string``` |
| <span data-ttu-id="8323f-175">language</span><span class="sxs-lookup"><span data-stu-id="8323f-175">language</span></span> | ```string``` |
| <span data-ttu-id="8323f-176">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="8323f-176">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="8323f-177">height</span><span class="sxs-lookup"><span data-stu-id="8323f-177">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="8323f-178">minHeight</span><span class="sxs-lookup"><span data-stu-id="8323f-178">minHeight</span></span> | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a><span data-ttu-id="8323f-179">адаптивекард</span><span class="sxs-lookup"><span data-stu-id="8323f-179">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-180">Добавлено в версии 0,1</span><span class="sxs-lookup"><span data-stu-id="8323f-180">Added in version 0.1</span></span></p>

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

| <span data-ttu-id="8323f-181">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-181">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-182">Версия</span><span class="sxs-lookup"><span data-stu-id="8323f-182">version</span></span> | ```string``` |
| <span data-ttu-id="8323f-183">фаллбакктекст</span><span class="sxs-lookup"><span data-stu-id="8323f-183">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="8323f-184">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="8323f-184">backgroundImage</span></span> | ```string``` |
| <span data-ttu-id="8323f-185">Стиль</span><span class="sxs-lookup"><span data-stu-id="8323f-185">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="8323f-186">speak</span><span class="sxs-lookup"><span data-stu-id="8323f-186">speak</span></span> | ```string``` |
| <span data-ttu-id="8323f-187">language</span><span class="sxs-lookup"><span data-stu-id="8323f-187">language</span></span> | ```string``` |
| <span data-ttu-id="8323f-188">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="8323f-188">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="8323f-189">height</span><span class="sxs-lookup"><span data-stu-id="8323f-189">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="8323f-190">minHeight</span><span class="sxs-lookup"><span data-stu-id="8323f-190">minHeight</span></span> | ```long``` |
| <span data-ttu-id="8323f-191">body</span><span class="sxs-lookup"><span data-stu-id="8323f-191">body</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| <span data-ttu-id="8323f-192">действия</span><span class="sxs-lookup"><span data-stu-id="8323f-192">actions</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## <a name="public-methods"></a><span data-ttu-id="8323f-193">Открытые методы</span><span class="sxs-lookup"><span data-stu-id="8323f-193">Public Methods</span></span>
---
### <a id="deserializefromstring0"></a><span data-ttu-id="8323f-194">десериализефромстринг</span><span class="sxs-lookup"><span data-stu-id="8323f-194">DeserializeFromString</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-195">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="8323f-195">Added in version 0.1.0</span></span></p>

```csharp
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

<span data-ttu-id="8323f-196">Десериализует заданную адаптивную карту как строку JSON для указанной версии модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="8323f-196">Deserializes the given adaptive card as a json string for the specified renderer version.</span></span>

| <span data-ttu-id="8323f-197">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-197">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-198">жсонстринг</span><span class="sxs-lookup"><span data-stu-id="8323f-198">jsonString</span></span> | ```string``` |
| <span data-ttu-id="8323f-199">рендерерверсион</span><span class="sxs-lookup"><span data-stu-id="8323f-199">rendererVersion</span></span> | ```string``` |

| <span data-ttu-id="8323f-200">Возвращает</span><span class="sxs-lookup"><span data-stu-id="8323f-200">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a><span data-ttu-id="8323f-201">Пример</span><span class="sxs-lookup"><span data-stu-id="8323f-201">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromstring1"></a><span data-ttu-id="8323f-202">десериализефромстринг</span><span class="sxs-lookup"><span data-stu-id="8323f-202">DeserializeFromString</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-203">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="8323f-203">Added in version 0.1.0</span></span></p>

```csharp
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

<span data-ttu-id="8323f-204">Десериализует заданную адаптивную карту как строку JSON для указанной версии модуля подготовки отчетов, используя объект [парсеконтекст]() для обработки анализа настраиваемого элемента.</span><span class="sxs-lookup"><span data-stu-id="8323f-204">Deserializes the given adaptive card as a json string for the specified renderer version using a [ParseContext]() object to handle custom element parsing.</span></span>

| <span data-ttu-id="8323f-205">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-205">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-206">жсонстринг</span><span class="sxs-lookup"><span data-stu-id="8323f-206">jsonString</span></span> | ```string``` |
| <span data-ttu-id="8323f-207">рендерерверсион</span><span class="sxs-lookup"><span data-stu-id="8323f-207">rendererVersion</span></span> | ```string``` |
| <span data-ttu-id="8323f-208">context</span><span class="sxs-lookup"><span data-stu-id="8323f-208">context</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| <span data-ttu-id="8323f-209">Возвращает</span><span class="sxs-lookup"><span data-stu-id="8323f-209">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a><span data-ttu-id="8323f-210">Пример</span><span class="sxs-lookup"><span data-stu-id="8323f-210">Sample</span></span>

```csharp
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a><span data-ttu-id="8323f-211">макефаллбакктексткард</span><span class="sxs-lookup"><span data-stu-id="8323f-211">MakeFallbackTextCard</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-212">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="8323f-212">Added in version 0.1.0</span></span></p>

```csharp
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

<span data-ttu-id="8323f-213">Десериализует заданную адаптивную карту как строку JSON для указанной версии модуля подготовки отчетов.</span><span class="sxs-lookup"><span data-stu-id="8323f-213">Deserializes the given adaptive card as a json string for the specified renderer version.</span></span>

| <span data-ttu-id="8323f-214">Параметры</span><span class="sxs-lookup"><span data-stu-id="8323f-214">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="8323f-215">фаллбакктекст</span><span class="sxs-lookup"><span data-stu-id="8323f-215">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="8323f-216">language</span><span class="sxs-lookup"><span data-stu-id="8323f-216">language</span></span> | ```string``` |
| <span data-ttu-id="8323f-217">speak</span><span class="sxs-lookup"><span data-stu-id="8323f-217">speak</span></span> | ```string``` |

| <span data-ttu-id="8323f-218">Возвращает</span><span class="sxs-lookup"><span data-stu-id="8323f-218">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | <span data-ttu-id="8323f-219">Адаптивная карта, содержащая резервный текст для карточки унрендереабле</span><span class="sxs-lookup"><span data-stu-id="8323f-219">Adaptive card that contains the fallback text for an unrendereable card</span></span> |

#### <a name="sample"></a><span data-ttu-id="8323f-220">Пример</span><span class="sxs-lookup"><span data-stu-id="8323f-220">Sample</span></span>

```csharp
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a><span data-ttu-id="8323f-221">Сериализуются</span><span class="sxs-lookup"><span data-stu-id="8323f-221">Serialize</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-222">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="8323f-222">Added in version 0.1.0</span></span></p>

```csharp
public string Serialize ()
```

<span data-ttu-id="8323f-223">Сериализует адаптивную карту в форму строки JSON.</span><span class="sxs-lookup"><span data-stu-id="8323f-223">Serializes the adaptive card into it's json string form.</span></span>

| <span data-ttu-id="8323f-224">Возвращает</span><span class="sxs-lookup"><span data-stu-id="8323f-224">Returns</span></span> | |
| --- | --- |
| ```string``` | <span data-ttu-id="8323f-225">Адаптивная карта в виде строки JSON</span><span class="sxs-lookup"><span data-stu-id="8323f-225">Adaptive card as a json string</span></span> |

#### <a name="sample"></a><span data-ttu-id="8323f-226">Пример</span><span class="sxs-lookup"><span data-stu-id="8323f-226">Sample</span></span>

```csharp
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a><span data-ttu-id="8323f-227">сериализетожсонвалуе</span><span class="sxs-lookup"><span data-stu-id="8323f-227">SerializeToJsonValue</span></span>
<p style='text-align:right'><span data-ttu-id="8323f-228">Добавлено в версии 0.1.0</span><span class="sxs-lookup"><span data-stu-id="8323f-228">Added in version 0.1.0</span></span></p>

```csharp
public JsonValue SerializeToJsonValue ()
```

<span data-ttu-id="8323f-229">Сериализует адаптивную карту в объект значения JSON.</span><span class="sxs-lookup"><span data-stu-id="8323f-229">Serializes the adaptive card into a json value object.</span></span>

| <span data-ttu-id="8323f-230">Возвращает</span><span class="sxs-lookup"><span data-stu-id="8323f-230">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### <a name="sample"></a><span data-ttu-id="8323f-231">Пример</span><span class="sxs-lookup"><span data-stu-id="8323f-231">Sample</span></span>

```csharp
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```