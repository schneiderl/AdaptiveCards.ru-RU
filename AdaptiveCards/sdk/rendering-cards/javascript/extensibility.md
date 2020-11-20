---
title: Расширяемость — пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 07/16/2020
ms.topic: article
ms.openlocfilehash: 96da071980b8cf41b616297c44c70d181a4f6ac0
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001851"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="800ab-102">Расширяемость — JavaScript</span><span class="sxs-lookup"><span data-stu-id="800ab-102">Extensibility - JavaScript</span></span>

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a><span data-ttu-id="800ab-103">Расширяемость с помощью пакета SDK для JS версии 2,0 и выше</span><span class="sxs-lookup"><span data-stu-id="800ab-103">Extensibility with the JS SDK version 2.0 and greater</span></span>

### <a name="before-you-start"></a><span data-ttu-id="800ab-104">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="800ab-104">Before you start</span></span>

> <span data-ttu-id="800ab-105">**Важно**. в версии 2,0 и более поздних версиях пакета SDK для JS используются [декораторы TypeScript](https://www.typescriptlang.org/docs/handbook/decorators.html).</span><span class="sxs-lookup"><span data-stu-id="800ab-105">**IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html).</span></span> <span data-ttu-id="800ab-106">Декораторы по-прежнему являются экспериментальной функцией и должны быть явно включены в `tsconfig.js` файл:</span><span class="sxs-lookup"><span data-stu-id="800ab-106">Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:</span></span>

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
<span data-ttu-id="800ab-107">Версия 2,0 пакета SDK для JS вносит критические изменения в способ реализации и регистрации пользовательских элементов и действий.</span><span class="sxs-lookup"><span data-stu-id="800ab-107">Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered.</span></span> <span data-ttu-id="800ab-108">Пример реализации и регистрации элемента или действия с помощью предыдущих версий пакета SDK см. в разделе [расширяемость с помощью пакета SDK для JS до версии 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).</span><span class="sxs-lookup"><span data-stu-id="800ab-108">For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).</span></span>


### <a name="custom-elements"></a><span data-ttu-id="800ab-109">Настраиваемые элементы</span><span class="sxs-lookup"><span data-stu-id="800ab-109">Custom elements</span></span>
<span data-ttu-id="800ab-110">Порядок создания настраиваемого типа элемента адаптивной карты:</span><span class="sxs-lookup"><span data-stu-id="800ab-110">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="800ab-111">Создание нового класса, производного от `CardElement`</span><span class="sxs-lookup"><span data-stu-id="800ab-111">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="800ab-112">Создание схемы путем объявления определений статических свойств</span><span class="sxs-lookup"><span data-stu-id="800ab-112">Create its schema by declaring static property definitions</span></span>
- <span data-ttu-id="800ab-113">Реализуйте `getJsonTypeName` методы и `internalRender` .</span><span class="sxs-lookup"><span data-stu-id="800ab-113">Implement its `getJsonTypeName`, and `internalRender` methods</span></span>
- <span data-ttu-id="800ab-114">Зарегистрируйте его в глобальном реестре элементов или используйте пользовательский реестр для каждой карты.</span><span class="sxs-lookup"><span data-stu-id="800ab-114">Register it in the global element registry, or use a custom registry on a per-card basis</span></span>


<span data-ttu-id="800ab-115">Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:</span><span class="sxs-lookup"><span data-stu-id="800ab-115">Let's take an example and implement a simple Progress Bar element:</span></span>
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
<span data-ttu-id="800ab-116">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="800ab-116">That's it.</span></span> <span data-ttu-id="800ab-117">Теперь элемент ProgressBar необходимо зарегистрировать для распознавания пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="800ab-117">The ProgressBar element now needs to be registered in order to be recognized by the SDK.</span></span> <span data-ttu-id="800ab-118">Его можно зарегистрировать глобально:</span><span class="sxs-lookup"><span data-stu-id="800ab-118">You can register it globally:</span></span>

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

<span data-ttu-id="800ab-119">Кроме того, можно использовать отдельный реестр, который позволяет использовать разные реестра для разных карт в приложении:</span><span class="sxs-lookup"><span data-stu-id="800ab-119">Or you can use a per-card registry, which allows the use of different registries for different cards in your application:</span></span>

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### <a name="custom-inputs"></a><span data-ttu-id="800ab-120">Пользовательский ввод</span><span class="sxs-lookup"><span data-stu-id="800ab-120">Custom inputs</span></span>
<span data-ttu-id="800ab-121">Входные данные — это специальный тип элементов, предназначенных для сбора данных, вводимых конечным пользователем, которые впоследствии могут передаваться в качестве параметров действиям.</span><span class="sxs-lookup"><span data-stu-id="800ab-121">An input is a special type of element dedicated to collecting data entered by the end user that can subsequently be passed as parameter to actions.</span></span>

<span data-ttu-id="800ab-122">Версии 2. x в пакете SDK для адаптивных карт JS представляют два существенных изменения, когда речь идет о входных данных:</span><span class="sxs-lookup"><span data-stu-id="800ab-122">Versions 2.x of the Adaptive Cards JS SDK introduces two notable changes when it comes to inputs:</span></span>
- <span data-ttu-id="800ab-123">**Проверка входных данных.** теперь существует встроенный механизм проверки входных данных, который автоматически обрабатывает ошибки проверки, включая визуальные подсказки.</span><span class="sxs-lookup"><span data-stu-id="800ab-123">**Input validation:** there is now a built-in input validation mechanism that automatically handles validation errors including visual cues</span></span>
- <span data-ttu-id="800ab-124">**Улучшения специальных возможностей.** встроенные входные данные обеспечивают лучшую поддержку специальных возможностей.</span><span class="sxs-lookup"><span data-stu-id="800ab-124">**Accessibility improvements:** built-in inputs have better support for accessibility features</span></span>

<span data-ttu-id="800ab-125">Поэтому реализация пользовательских входных данных требует немного больше логики, чем реализация простых элементов.</span><span class="sxs-lookup"><span data-stu-id="800ab-125">Because of this, implementing custom inputs requires a little more logic than implementing simple elements.</span></span> <span data-ttu-id="800ab-126">В следующей таблице перечислены все методы, которые должна реализовать пользовательская реализация для партиоЦипате в механизме проверки входных данных и быть доступными:</span><span class="sxs-lookup"><span data-stu-id="800ab-126">The table below lists all the methods a custom input implementation should to implement in order to partiocipate in the input validation mechanism and be accessible:</span></span>

| <span data-ttu-id="800ab-127">Метод</span><span class="sxs-lookup"><span data-stu-id="800ab-127">Method</span></span> | <span data-ttu-id="800ab-128">Описание</span><span class="sxs-lookup"><span data-stu-id="800ab-128">Description</span></span> |
| --------- | ------------- |
| `protected updateInputControlAriaLabelledBy()` | <span data-ttu-id="800ab-129">Этот метод вызывается во время последовательности проверки входных данных.</span><span class="sxs-lookup"><span data-stu-id="800ab-129">This method  is called during the input validation sequence.</span></span> <span data-ttu-id="800ab-130">Если вход не проходит проверку, отображается соответствующее сообщение об ошибке, и необходимо обновить атрибут базового элемента управления вводом, чтобы `aria-labelledby` входные данные соответствовали требованиям специальных возможностей.</span><span class="sxs-lookup"><span data-stu-id="800ab-130">When an input fails validation, its associated error message is displayed and the underlying input control's `aria-labelledby` attribute needs to be updated in order for the input to comply with accessibility requirements.</span></span> <span data-ttu-id="800ab-131">Пользовательские входные данные должны переопределяться `updateInputControlAriaLabelledBy` для применения соответствующего `aria-labelledby` атрибута к базовому элементу управления вводом.</span><span class="sxs-lookup"><span data-stu-id="800ab-131">Custom inputs SHOULD override `updateInputControlAriaLabelledBy` to apply the appropriate `aria-labelledby` attribute to the underlying input control.</span></span> <span data-ttu-id="800ab-132">`getAllLabelIds(): string[]`Метод можно использовать для получения идентификаторов всех меток, которые должны быть указаны в `aria-labelledby` атрибуте.</span><span class="sxs-lookup"><span data-stu-id="800ab-132">The `getAllLabelIds(): string[]` method can be used to retrieve the Ids of all the labels that should be specified in the `aria-labelledby` attribute.</span></span>  |
| `protected internalRender(): HTMLElement` | <span data-ttu-id="800ab-133">Точно так же, как и для любого другого настраиваемого элемента адаптивной карты, `internalRender` необходимо переопределить, чтобы при необходимости отобразить входные данные.</span><span class="sxs-lookup"><span data-stu-id="800ab-133">Just like for any other Adaptive Card custom element, `internalRender` MUST be overridden to render your input as desired.</span></span> <span data-ttu-id="800ab-134">Здесь необходимо создать фактический базовый элемент управления вводом.</span><span class="sxs-lookup"><span data-stu-id="800ab-134">This is where you'll want to create the actual underlying input control.</span></span> |
| `protected get isNullable(): boolean` | <span data-ttu-id="800ab-135">Указывает, поддерживают ли входные данные неопределенные значения (например, input. Text делает, тогда как input. toggle — нет). Настраиваемые входы должны переопределять метод получения этого свойства, чтобы указать, поддерживают ли они неопределенные значения.</span><span class="sxs-lookup"><span data-stu-id="800ab-135">Indicates whether the input supports undefined values (for instance, Input.Text does, whereas Input.Toggle doesn't.) Custom inputs SHOULD override this property getter to indicate if they support undefined values.</span></span> <span data-ttu-id="800ab-136">Базовая реализация возвращает `true` .</span><span class="sxs-lookup"><span data-stu-id="800ab-136">The base implementation returns `true`.</span></span> |
| `public focus()` | <span data-ttu-id="800ab-137">При обнаружении ошибок проверки фокус автоматически помещается на первый вход, который не прошел проверку.</span><span class="sxs-lookup"><span data-stu-id="800ab-137">When validation errors are encountered, the focus is automatically placed on the first input that failed validation.</span></span> <span data-ttu-id="800ab-138">`focus`В некоторых случаях Базовая реализация будет работать только с пользовательскими входными данными.</span><span class="sxs-lookup"><span data-stu-id="800ab-138">The base implementation of `focus` will in some cases just work for custom inputs.</span></span> <span data-ttu-id="800ab-139">Если это не так, пользовательские элементы управления вводом должны переопределяться, `focus` чтобы явно перевести фокус на базовый элемент управления вводом.</span><span class="sxs-lookup"><span data-stu-id="800ab-139">When that isn't the case, custom input controls MUST override `focus` to explicitly put the focus on the underlying input control.</span></span>  |
| `public abstract isSet(): boolean` | <span data-ttu-id="800ab-140">Указывает, было ли значение входных данных задано пользователем.</span><span class="sxs-lookup"><span data-stu-id="800ab-140">Indicates whether the input's value has been set by the user.</span></span> <span data-ttu-id="800ab-141">Этот метод вызывается во время последовательности проверки входных данных, чтобы определить, пройдены ли входные или непройденные проверки.</span><span class="sxs-lookup"><span data-stu-id="800ab-141">This method is called during the input validation sequence to determine if the input passes or fails validation.</span></span> <span data-ttu-id="800ab-142">Пользовательские входные данные должны переопределяться `isSet` для участия в механизме проверки входных данных.</span><span class="sxs-lookup"><span data-stu-id="800ab-142">Custom inputs MUST override `isSet` in order to participate in the input validation mechanism.</span></span> |
| `public isValid(): boolean` | <span data-ttu-id="800ab-143">Указывает, является ли входное значение допустимым.</span><span class="sxs-lookup"><span data-stu-id="800ab-143">Indicates whether the value of the input is valid.</span></span> <span data-ttu-id="800ab-144">Этот метод вызывается во время последовательности проверки входных данных, чтобы определить, пройдены ли входные или непройденные проверки.</span><span class="sxs-lookup"><span data-stu-id="800ab-144">This method is called during the input validation sequence to determine if the input passes or fails validation.</span></span> <span data-ttu-id="800ab-145">Пользовательские входные данные должны переопределяться `isValid` для участия в механизме проверки входных данных.</span><span class="sxs-lookup"><span data-stu-id="800ab-145">Custom inputs SHOULD override `isValid` in order to participate in the input validation mechanism.</span></span> <span data-ttu-id="800ab-146">Базовая реализация возвращает `true` .</span><span class="sxs-lookup"><span data-stu-id="800ab-146">The base implementation returns `true`.</span></span> |
| `public abstract get value(): any` | <span data-ttu-id="800ab-147">Возвращает значение входных данных.</span><span class="sxs-lookup"><span data-stu-id="800ab-147">Returns the value of the input.</span></span> <span data-ttu-id="800ab-148">Настраиваемые входы должны переопределять это, чтобы значение входных данных извлекаться из базового элемента управления вводом.</span><span class="sxs-lookup"><span data-stu-id="800ab-148">Custom inputs MUST override this so that the value of the input is retrieved from the underlying input control.</span></span> |


### <a name="custom-actions"></a><span data-ttu-id="800ab-149">Настраиваемые действия</span><span class="sxs-lookup"><span data-stu-id="800ab-149">Custom actions</span></span>
<span data-ttu-id="800ab-150">Действия по реализации пользовательского действия одинаковы для элементов.</span><span class="sxs-lookup"><span data-stu-id="800ab-150">The steps to implementing a custom action are the same as those for elements.</span></span> <span data-ttu-id="800ab-151">Единственное отличие заключается в том, что действия регистрируются в реестрах действий, а не в реестрах элементов.</span><span class="sxs-lookup"><span data-stu-id="800ab-151">The only difference is that actions are registered in action registries, and not in element registries.</span></span>

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

<span data-ttu-id="800ab-152">Зарегистрируйте новое действие глобально:</span><span class="sxs-lookup"><span data-stu-id="800ab-152">Register the new action globally:</span></span>
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

<span data-ttu-id="800ab-153">Или используйте реестр для каждой карты:</span><span class="sxs-lookup"><span data-stu-id="800ab-153">Or use a per-card registry:</span></span>
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a><span data-ttu-id="800ab-154">Расширяемость с помощью пакета SDK для JS до версии 2,0</span><span class="sxs-lookup"><span data-stu-id="800ab-154">Extensibility with the JS SDK prior to version 2.0</span></span>

### <a name="custom-elements"></a><span data-ttu-id="800ab-155">Настраиваемые элементы</span><span class="sxs-lookup"><span data-stu-id="800ab-155">Custom elements</span></span>

### <a name="before-you-start"></a><span data-ttu-id="800ab-156">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="800ab-156">Before you start</span></span>

> <span data-ttu-id="800ab-157">**Важно**. в версии 2,0 и более поздних версиях пакета SDK для JS используются [декораторы TypeScript](https://www.typescriptlang.org/docs/handbook/decorators.html).</span><span class="sxs-lookup"><span data-stu-id="800ab-157">**IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html).</span></span> <span data-ttu-id="800ab-158">Декораторы по-прежнему являются экспериментальной функцией и должны быть явно включены в `tsconfig.js` файл:</span><span class="sxs-lookup"><span data-stu-id="800ab-158">Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:</span></span>

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
<span data-ttu-id="800ab-159">Версия 2,0 пакета SDK для JS вносит критические изменения в способ реализации и регистрации пользовательских элементов и действий.</span><span class="sxs-lookup"><span data-stu-id="800ab-159">Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered.</span></span> <span data-ttu-id="800ab-160">Пример реализации и регистрации элемента или действия с помощью предыдущих версий пакета SDK см. в разделе [расширяемость с помощью пакета SDK для JS до версии 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).</span><span class="sxs-lookup"><span data-stu-id="800ab-160">For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).</span></span>


### <a name="custom-elements"></a><span data-ttu-id="800ab-161">Настраиваемые элементы</span><span class="sxs-lookup"><span data-stu-id="800ab-161">Custom elements</span></span>
<span data-ttu-id="800ab-162">Порядок создания настраиваемого типа элемента адаптивной карты:</span><span class="sxs-lookup"><span data-stu-id="800ab-162">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="800ab-163">Создание нового класса, производного от `CardElement`</span><span class="sxs-lookup"><span data-stu-id="800ab-163">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="800ab-164">Создание схемы путем объявления определений статических свойств</span><span class="sxs-lookup"><span data-stu-id="800ab-164">Create its schema by declaring static property definitions</span></span>
- <span data-ttu-id="800ab-165">Реализуйте `getJsonTypeName` методы и `internalRender` .</span><span class="sxs-lookup"><span data-stu-id="800ab-165">Implement its `getJsonTypeName`, and `internalRender` methods</span></span>
- <span data-ttu-id="800ab-166">Зарегистрируйте его в глобальном реестре элементов или используйте пользовательский реестр для каждой карты.</span><span class="sxs-lookup"><span data-stu-id="800ab-166">Register it in the global element registry, or use a custom registry on a per-card basis</span></span>


<span data-ttu-id="800ab-167">Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:</span><span class="sxs-lookup"><span data-stu-id="800ab-167">Let's take an example and implement a simple Progress Bar element:</span></span>
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
<span data-ttu-id="800ab-168">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="800ab-168">That's it.</span></span> <span data-ttu-id="800ab-169">Теперь элемент ProgressBar необходимо зарегистрировать для распознавания пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="800ab-169">The ProgressBar element now needs to be registered in order to be recognized by the SDK.</span></span> <span data-ttu-id="800ab-170">Его можно зарегистрировать глобально:</span><span class="sxs-lookup"><span data-stu-id="800ab-170">You can register it globally:</span></span>

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

<span data-ttu-id="800ab-171">Кроме того, можно использовать отдельный реестр, который позволяет использовать разные реестра для разных карт в приложении:</span><span class="sxs-lookup"><span data-stu-id="800ab-171">Or you can use a per-card registry, which allows the use of different registries for different cards in your application:</span></span>

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### <a name="custom-actions"></a><span data-ttu-id="800ab-172">Настраиваемые действия</span><span class="sxs-lookup"><span data-stu-id="800ab-172">Custom actions</span></span>
<span data-ttu-id="800ab-173">Действия по реализации пользовательского действия одинаковы для элементов.</span><span class="sxs-lookup"><span data-stu-id="800ab-173">The steps to implementing a custom action are the same as those for elements.</span></span> <span data-ttu-id="800ab-174">Единственное отличие заключается в том, что действия регистрируются в реестрах действий, а не в реестрах элементов.</span><span class="sxs-lookup"><span data-stu-id="800ab-174">The only difference is that actions are registered in action registries, and not in element registries.</span></span>

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

<span data-ttu-id="800ab-175">Зарегистрируйте новое действие глобально:</span><span class="sxs-lookup"><span data-stu-id="800ab-175">Register the new action globally:</span></span>
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

<span data-ttu-id="800ab-176">Или используйте реестр для каждой карты:</span><span class="sxs-lookup"><span data-stu-id="800ab-176">Or use a per-card registry:</span></span>
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a><span data-ttu-id="800ab-177">Расширяемость с помощью пакета SDK для JS до версии 2,0</span><span class="sxs-lookup"><span data-stu-id="800ab-177">Extensibility with the JS SDK prior to version 2.0</span></span>

### <a name="custom-elements"></a><span data-ttu-id="800ab-178">Настраиваемые элементы</span><span class="sxs-lookup"><span data-stu-id="800ab-178">Custom elements</span></span>

<span data-ttu-id="800ab-179">Порядок создания настраиваемого типа элемента адаптивной карты:</span><span class="sxs-lookup"><span data-stu-id="800ab-179">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="800ab-180">Создание нового класса, производного от `CardElement`</span><span class="sxs-lookup"><span data-stu-id="800ab-180">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="800ab-181">Реализуйте `getJsonTypeName` методы,, `parse` `toJSON` `internalRender` и `renderSpeech`</span><span class="sxs-lookup"><span data-stu-id="800ab-181">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="800ab-182">Зарегистрируйте его, добавив в реестр элементов модуля подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="800ab-182">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="800ab-183">Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:</span><span class="sxs-lookup"><span data-stu-id="800ab-183">Let's take an example and implement a simple Progress Bar element:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class ProgressBar extends Adaptive.CardElement {
    private _title: string;
    private _value: number = 0;
    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new Adaptive.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return "ProgressBar";
    }

    toJSON(): any {
        let result = super.toJSON();

        Adaptive.setProperty(result, "title", this.title);
        Adaptive.setProperty(result, "value", this.value);

        return result;
    }

    parse(json: any, errors?: Array<Adaptive.IValidationError>) {
        super.parse(json, errors);

        this.title = Adaptive.getStringValueOrDefault(json["title"], undefined);
        this.value = Adaptive.getValueOrDefault(json["value"], this._value);
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (Adaptive.isNullOrEmpty(this.title)) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }

    renderSpeech(): string {
        return (Adaptive.isNullOrEmpty(this.title) ? "Progress" : this.title) + " " + Math.ceil(this.value) + "%";
    }

    get title(): string {
        return this._title;
    }

    set title(value: string) {
        if (this._title !== value) {
            this._title = value;

            this.updateLayout();
        }
    }

    get value(): number {
        return this._value;
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this._value !== adjustedValue) {
            this._value = adjustedValue;

            this.updateLayout();
        }
    }
}
```

<span data-ttu-id="800ab-184">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="800ab-184">That's it.</span></span> <span data-ttu-id="800ab-185">Теперь просто зарегистрируйте класс индикатора выполнения с помощью модуля подготовки отчетов:</span><span class="sxs-lookup"><span data-stu-id="800ab-185">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a><span data-ttu-id="800ab-186">Настраиваемые действия</span><span class="sxs-lookup"><span data-stu-id="800ab-186">Custom actions</span></span>

<span data-ttu-id="800ab-187">Действия по созданию настраиваемого действия адаптивной карты по сути являются такими же, как и для пользовательских элементов.</span><span class="sxs-lookup"><span data-stu-id="800ab-187">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="800ab-188">Ниже приведен простой пример действия оповещения, которое просто отображает окно сообщения с настраиваемым текстом:</span><span class="sxs-lookup"><span data-stu-id="800ab-188">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class AlertAction extends Adaptive.Action {
    text: string;

    getJsonTypeName(): string {
        return "Action.ALert";
    }

    execute() {
        alert(this.text);
    }

    parse(json: any) {
        super.parse(json);

        this.text = Adaptive.getStringValueOrDefault(json["text"], "Alert!");
    }

    toJSON() {
        let result = super.toJSON();

        Adaptive.setProperty(result, "text", this.text);

        return result;
    }
}
```

<span data-ttu-id="800ab-189">Теперь Зарегистрируйте новое действие:</span><span class="sxs-lookup"><span data-stu-id="800ab-189">Now register the new action:</span></span>

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="800ab-190">Пример</span><span class="sxs-lookup"><span data-stu-id="800ab-190">Example</span></span>

<span data-ttu-id="800ab-191">Ниже приведен пример карточки, в которой используются как элемент ProgressBar, так и действие Алертактион:</span><span class="sxs-lookup"><span data-stu-id="800ab-191">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "Custom ProgressBar element"
        },
        {
            "type": "ProgressBar",
            "title": "Please wait...",
            "value": 10
        }
    ],
    "actions": [
        {
            "type": "Action.Alert",
            "title": "Click me",
            "text": "Hello world!"
        }
    ]
}
```

<span data-ttu-id="800ab-192">И вот как это выглядит: ![ Image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="800ab-192">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
