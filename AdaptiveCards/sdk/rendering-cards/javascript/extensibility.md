---
title: Расширяемость – пакет SDK для JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 464fda8c83f9943d316f43fec811511ab9696916
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552636"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="97753-102">Расширяемость – JavaScript</span><span class="sxs-lookup"><span data-stu-id="97753-102">Extensibility - JavaScript</span></span>

## <a name="implement-and-register-a-custom-element"></a><span data-ttu-id="97753-103">Реализовывать и регистрировать настраиваемый элемент</span><span class="sxs-lookup"><span data-stu-id="97753-103">Implement and register a custom element</span></span>

<span data-ttu-id="97753-104">Приведены инструкции по созданию пользовательского типа элемента инструмент Adaptive cards.</span><span class="sxs-lookup"><span data-stu-id="97753-104">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="97753-105">Создайте новый класс, обеспечивая тем самым из `CardElement`</span><span class="sxs-lookup"><span data-stu-id="97753-105">Create a new class driving from `CardElement`</span></span>
- <span data-ttu-id="97753-106">Реализуйте его `getJsonTypeName`, `parse`, `toJSON`, `internalRender` и `renderSpeech` методы</span><span class="sxs-lookup"><span data-stu-id="97753-106">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="97753-107">Зарегистрировать его, добавив ее в модуль подготовки отчетов элемент реестра</span><span class="sxs-lookup"><span data-stu-id="97753-107">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="97753-108">Давайте рассмотрим в качестве примера и реализовать простой элемент индикатор хода выполнения:</span><span class="sxs-lookup"><span data-stu-id="97753-108">Let's take an example and implement a simple Progress Bar element:</span></span>

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

<span data-ttu-id="97753-109">Вот и все.</span><span class="sxs-lookup"><span data-stu-id="97753-109">That's it.</span></span> <span data-ttu-id="97753-110">Теперь просто Зарегистрируйте класс индикатор хода выполнения с помощью модуля подготовки отчетов:</span><span class="sxs-lookup"><span data-stu-id="97753-110">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="implement-and-register-a-custom-action"></a><span data-ttu-id="97753-111">Реализация и регистрация настраиваемого действия</span><span class="sxs-lookup"><span data-stu-id="97753-111">Implement and register a custom action</span></span>

<span data-ttu-id="97753-112">Действия по созданию настраиваемого действия инструмент Adaptive Cards по сути те же для пользовательских элементов.</span><span class="sxs-lookup"><span data-stu-id="97753-112">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="97753-113">Ниже приведен простой пример действие оповещения, который просто отображает окно сообщения с текстом, можно настроить:</span><span class="sxs-lookup"><span data-stu-id="97753-113">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

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

<span data-ttu-id="97753-114">Зарегистрируйте новое действие:</span><span class="sxs-lookup"><span data-stu-id="97753-114">Now register the new action:</span></span>

```
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="97753-115">Пример</span><span class="sxs-lookup"><span data-stu-id="97753-115">Example</span></span>

<span data-ttu-id="97753-116">Ниже приведен пример карточки, использующего элемент ProgressBar и AlertAction действие.</span><span class="sxs-lookup"><span data-stu-id="97753-116">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
```
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

<span data-ttu-id="97753-117">А вот подготовкой к просмотру: ![образа](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="97753-117">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
