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
# <a name="extensibility---javascript"></a>Расширяемость — JavaScript

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a>Расширяемость с помощью пакета SDK для JS версии 2,0 и выше

### <a name="before-you-start"></a>Перед началом работы

> **Важно**. в версии 2,0 и более поздних версиях пакета SDK для JS используются [декораторы TypeScript](https://www.typescriptlang.org/docs/handbook/decorators.html). Декораторы по-прежнему являются экспериментальной функцией и должны быть явно включены в `tsconfig.js` файл:

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
Версия 2,0 пакета SDK для JS вносит критические изменения в способ реализации и регистрации пользовательских элементов и действий. Пример реализации и регистрации элемента или действия с помощью предыдущих версий пакета SDK см. в разделе [расширяемость с помощью пакета SDK для JS до версии 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).


### <a name="custom-elements"></a>Настраиваемые элементы
Порядок создания настраиваемого типа элемента адаптивной карты:
- Создание нового класса, производного от `CardElement`
- Создание схемы путем объявления определений статических свойств
- Реализуйте `getJsonTypeName` методы и `internalRender` .
- Зарегистрируйте его в глобальном реестре элементов или используйте пользовательский реестр для каждой карты.


Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:
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
Вот и все. Теперь элемент ProgressBar необходимо зарегистрировать для распознавания пакетом SDK. Его можно зарегистрировать глобально:

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

Кроме того, можно использовать отдельный реестр, который позволяет использовать разные реестра для разных карт в приложении:

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

### <a name="custom-inputs"></a>Пользовательский ввод
Входные данные — это специальный тип элементов, предназначенных для сбора данных, вводимых конечным пользователем, которые впоследствии могут передаваться в качестве параметров действиям.

Версии 2. x в пакете SDK для адаптивных карт JS представляют два существенных изменения, когда речь идет о входных данных:
- **Проверка входных данных.** теперь существует встроенный механизм проверки входных данных, который автоматически обрабатывает ошибки проверки, включая визуальные подсказки.
- **Улучшения специальных возможностей.** встроенные входные данные обеспечивают лучшую поддержку специальных возможностей.

Поэтому реализация пользовательских входных данных требует немного больше логики, чем реализация простых элементов. В следующей таблице перечислены все методы, которые должна реализовать пользовательская реализация для партиоЦипате в механизме проверки входных данных и быть доступными:

| Метод | Описание |
| --------- | ------------- |
| `protected updateInputControlAriaLabelledBy()` | Этот метод вызывается во время последовательности проверки входных данных. Если вход не проходит проверку, отображается соответствующее сообщение об ошибке, и необходимо обновить атрибут базового элемента управления вводом, чтобы `aria-labelledby` входные данные соответствовали требованиям специальных возможностей. Пользовательские входные данные должны переопределяться `updateInputControlAriaLabelledBy` для применения соответствующего `aria-labelledby` атрибута к базовому элементу управления вводом. `getAllLabelIds(): string[]`Метод можно использовать для получения идентификаторов всех меток, которые должны быть указаны в `aria-labelledby` атрибуте.  |
| `protected internalRender(): HTMLElement` | Точно так же, как и для любого другого настраиваемого элемента адаптивной карты, `internalRender` необходимо переопределить, чтобы при необходимости отобразить входные данные. Здесь необходимо создать фактический базовый элемент управления вводом. |
| `protected get isNullable(): boolean` | Указывает, поддерживают ли входные данные неопределенные значения (например, input. Text делает, тогда как input. toggle — нет). Настраиваемые входы должны переопределять метод получения этого свойства, чтобы указать, поддерживают ли они неопределенные значения. Базовая реализация возвращает `true` . |
| `public focus()` | При обнаружении ошибок проверки фокус автоматически помещается на первый вход, который не прошел проверку. `focus`В некоторых случаях Базовая реализация будет работать только с пользовательскими входными данными. Если это не так, пользовательские элементы управления вводом должны переопределяться, `focus` чтобы явно перевести фокус на базовый элемент управления вводом.  |
| `public abstract isSet(): boolean` | Указывает, было ли значение входных данных задано пользователем. Этот метод вызывается во время последовательности проверки входных данных, чтобы определить, пройдены ли входные или непройденные проверки. Пользовательские входные данные должны переопределяться `isSet` для участия в механизме проверки входных данных. |
| `public isValid(): boolean` | Указывает, является ли входное значение допустимым. Этот метод вызывается во время последовательности проверки входных данных, чтобы определить, пройдены ли входные или непройденные проверки. Пользовательские входные данные должны переопределяться `isValid` для участия в механизме проверки входных данных. Базовая реализация возвращает `true` . |
| `public abstract get value(): any` | Возвращает значение входных данных. Настраиваемые входы должны переопределять это, чтобы значение входных данных извлекаться из базового элемента управления вводом. |


### <a name="custom-actions"></a>Настраиваемые действия
Действия по реализации пользовательского действия одинаковы для элементов. Единственное отличие заключается в том, что действия регистрируются в реестрах действий, а не в реестрах элементов.

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

Зарегистрируйте новое действие глобально:
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

Или используйте реестр для каждой карты:
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

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a>Расширяемость с помощью пакета SDK для JS до версии 2,0

### <a name="custom-elements"></a>Настраиваемые элементы

### <a name="before-you-start"></a>Перед началом работы

> **Важно**. в версии 2,0 и более поздних версиях пакета SDK для JS используются [декораторы TypeScript](https://www.typescriptlang.org/docs/handbook/decorators.html). Декораторы по-прежнему являются экспериментальной функцией и должны быть явно включены в `tsconfig.js` файл:

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
Версия 2,0 пакета SDK для JS вносит критические изменения в способ реализации и регистрации пользовательских элементов и действий. Пример реализации и регистрации элемента или действия с помощью предыдущих версий пакета SDK см. в разделе [расширяемость с помощью пакета SDK для JS до версии 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).


### <a name="custom-elements"></a>Настраиваемые элементы
Порядок создания настраиваемого типа элемента адаптивной карты:
- Создание нового класса, производного от `CardElement`
- Создание схемы путем объявления определений статических свойств
- Реализуйте `getJsonTypeName` методы и `internalRender` .
- Зарегистрируйте его в глобальном реестре элементов или используйте пользовательский реестр для каждой карты.


Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:
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
Вот и все. Теперь элемент ProgressBar необходимо зарегистрировать для распознавания пакетом SDK. Его можно зарегистрировать глобально:

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

Кроме того, можно использовать отдельный реестр, который позволяет использовать разные реестра для разных карт в приложении:

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

### <a name="custom-actions"></a>Настраиваемые действия
Действия по реализации пользовательского действия одинаковы для элементов. Единственное отличие заключается в том, что действия регистрируются в реестрах действий, а не в реестрах элементов.

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

Зарегистрируйте новое действие глобально:
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

Или используйте реестр для каждой карты:
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

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a>Расширяемость с помощью пакета SDK для JS до версии 2,0

### <a name="custom-elements"></a>Настраиваемые элементы

Порядок создания настраиваемого типа элемента адаптивной карты:
- Создание нового класса, производного от `CardElement`
- Реализуйте `getJsonTypeName` методы,, `parse` `toJSON` `internalRender` и `renderSpeech`
- Зарегистрируйте его, добавив в реестр элементов модуля подготовки отчетов

Давайте рассмотрим пример и реализую простой элемент индикатора выполнения:

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

Вот и все. Теперь просто зарегистрируйте класс индикатора выполнения с помощью модуля подготовки отчетов:

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a>Настраиваемые действия

Действия по созданию настраиваемого действия адаптивной карты по сути являются такими же, как и для пользовательских элементов. Ниже приведен простой пример действия оповещения, которое просто отображает окно сообщения с настраиваемым текстом:

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

Теперь Зарегистрируйте новое действие:

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a>Пример

Ниже приведен пример карточки, в которой используются как элемент ProgressBar, так и действие Алертактион:
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

И вот как это выглядит: ![ Image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)
