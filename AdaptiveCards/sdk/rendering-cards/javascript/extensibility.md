---
title: Расширяемость — пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 07/16/2020
ms.topic: article
ms.openlocfilehash: 81c60e200d2fcbc844a3ae3f4fdefa0ddaa399d3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417540"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="4ecc5-102">Расширяемость — JavaScript</span><span class="sxs-lookup"><span data-stu-id="4ecc5-102">Extensibility - JavaScript</span></span>

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a><span data-ttu-id="4ecc5-103">Расширяемость с помощью пакета SDK для JS версии 2,0 и выше</span><span class="sxs-lookup"><span data-stu-id="4ecc5-103">Extensibility with the JS SDK version 2.0 and greater</span></span>

### <a name="before-you-start"></a><span data-ttu-id="4ecc5-104">Перед началом работы</span><span class="sxs-lookup"><span data-stu-id="4ecc5-104">Before you start</span></span>

> <span data-ttu-id="4ecc5-105">**Важно**. в версии 2,0 и более поздних версиях пакета SDK для JS используются [декораторы TypeScript](https://www.typescriptlang.org/docs/handbook/decorators.html).</span><span class="sxs-lookup"><span data-stu-id="4ecc5-105">**IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html).</span></span> <span data-ttu-id="4ecc5-106">Декораторы по-прежнему являются экспериментальной функцией и должны быть явно включены в `tsconfig.js` файл:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-106">Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:</span></span>

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
<span data-ttu-id="4ecc5-107">Версия 2,0 пакета SDK для JS вносит критические изменения в способ реализации и регистрации пользовательских элементов и действий.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-107">Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered.</span></span> <span data-ttu-id="4ecc5-108">Пример реализации и регистрации элемента или действия с помощью предыдущих версий пакета SDK см. в разделе [расширяемость с помощью пакета SDK для JS до версии 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).</span><span class="sxs-lookup"><span data-stu-id="4ecc5-108">For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).</span></span>


### <a name="custom-elements"></a><span data-ttu-id="4ecc5-109">Настраиваемые элементы</span><span class="sxs-lookup"><span data-stu-id="4ecc5-109">Custom elements</span></span>
<span data-ttu-id="4ecc5-110">Порядок создания настраиваемого типа элемента адаптивной карты:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-110">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="4ecc5-111">Создание нового класса, производного от`CardElement`</span><span class="sxs-lookup"><span data-stu-id="4ecc5-111">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="4ecc5-112">Создание схемы путем объявления определений статических свойств</span><span class="sxs-lookup"><span data-stu-id="4ecc5-112">Create its schema by declaring static property definitions</span></span>
- <span data-ttu-id="4ecc5-113">Реализуйте `getJsonTypeName` методы и `internalRender` .</span><span class="sxs-lookup"><span data-stu-id="4ecc5-113">Implement its `getJsonTypeName`, and `internalRender` methods</span></span>
- <span data-ttu-id="4ecc5-114">Зарегистрируйте его в глобальном реестре элементов или используйте пользовательский реестр для каждой карты.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-114">Register it in the global element registry, or use a custom registry on a per-card basis</span></span>


<span data-ttu-id="4ecc5-115">Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-115">Let's take an example and implement a simple Progress Bar element:</span></span>
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
<span data-ttu-id="4ecc5-116">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-116">That's it.</span></span> <span data-ttu-id="4ecc5-117">Теперь элемент ProgressBar необходимо зарегистрировать для распознавания пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-117">The ProgressBar element now needs to be registered in order to be recognized by the SDK.</span></span> <span data-ttu-id="4ecc5-118">Его можно зарегистрировать глобально:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-118">You can register it globally:</span></span>

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

<span data-ttu-id="4ecc5-119">Кроме того, можно использовать отдельный реестр, который позволяет использовать разные реестра для разных карт в приложении:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-119">Or you can use a per-card registry, which allows the use of different registries for different cards in your application:</span></span>

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

### <a name="custom-actions"></a><span data-ttu-id="4ecc5-120">Настраиваемые действия</span><span class="sxs-lookup"><span data-stu-id="4ecc5-120">Custom actions</span></span>
<span data-ttu-id="4ecc5-121">Действия по реализации пользовательского действия одинаковы для элементов.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-121">The steps to implementing a custom action are the same as those for elements.</span></span> <span data-ttu-id="4ecc5-122">Единственное отличие заключается в том, что действия регистрируются в реестрах действий, а не в реестрах элементов.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-122">The only difference is that actions are registered in action registries, and not in element registries.</span></span>

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

<span data-ttu-id="4ecc5-123">Зарегистрируйте новое действие глобально:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-123">Register the new action globally:</span></span>
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

<span data-ttu-id="4ecc5-124">Или используйте реестр для каждой карты:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-124">Or use a per-card registry:</span></span>
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

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a><span data-ttu-id="4ecc5-125">Расширяемость с помощью пакета SDK для JS до версии 2,0</span><span class="sxs-lookup"><span data-stu-id="4ecc5-125">Extensibility with the JS SDK prior to version 2.0</span></span>

### <a name="custom-elements"></a><span data-ttu-id="4ecc5-126">Настраиваемые элементы</span><span class="sxs-lookup"><span data-stu-id="4ecc5-126">Custom elements</span></span>

<span data-ttu-id="4ecc5-127">Порядок создания настраиваемого типа элемента адаптивной карты:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-127">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="4ecc5-128">Создание нового класса, производного от`CardElement`</span><span class="sxs-lookup"><span data-stu-id="4ecc5-128">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="4ecc5-129">Реализуйте `getJsonTypeName` методы,, `parse` `toJSON` `internalRender` и `renderSpeech`</span><span class="sxs-lookup"><span data-stu-id="4ecc5-129">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="4ecc5-130">Зарегистрируйте его, добавив в реестр элементов модуля подготовки отчетов</span><span class="sxs-lookup"><span data-stu-id="4ecc5-130">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="4ecc5-131">Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-131">Let's take an example and implement a simple Progress Bar element:</span></span>

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

<span data-ttu-id="4ecc5-132">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-132">That's it.</span></span> <span data-ttu-id="4ecc5-133">Теперь просто зарегистрируйте класс индикатора выполнения с помощью модуля подготовки отчетов:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-133">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a><span data-ttu-id="4ecc5-134">Настраиваемые действия</span><span class="sxs-lookup"><span data-stu-id="4ecc5-134">Custom actions</span></span>

<span data-ttu-id="4ecc5-135">Действия по созданию настраиваемого действия адаптивной карты по сути являются такими же, как и для пользовательских элементов.</span><span class="sxs-lookup"><span data-stu-id="4ecc5-135">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="4ecc5-136">Ниже приведен простой пример действия оповещения, которое просто отображает окно сообщения с настраиваемым текстом:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-136">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

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

<span data-ttu-id="4ecc5-137">Теперь Зарегистрируйте новое действие:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-137">Now register the new action:</span></span>

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="4ecc5-138">Пример</span><span class="sxs-lookup"><span data-stu-id="4ecc5-138">Example</span></span>

<span data-ttu-id="4ecc5-139">Ниже приведен пример карточки, в которой используются как элемент ProgressBar, так и действие Алертактион:</span><span class="sxs-lookup"><span data-stu-id="4ecc5-139">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
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

<span data-ttu-id="4ecc5-140">И вот как это выглядит: ![ Image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="4ecc5-140">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
