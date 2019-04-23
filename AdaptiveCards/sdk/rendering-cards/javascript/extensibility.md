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
# <a name="extensibility---javascript"></a>Расширяемость – JavaScript

## <a name="implement-and-register-a-custom-element"></a>Реализовывать и регистрировать настраиваемый элемент

Приведены инструкции по созданию пользовательского типа элемента инструмент Adaptive cards.
- Создайте новый класс, обеспечивая тем самым из `CardElement`
- Реализуйте его `getJsonTypeName`, `parse`, `toJSON`, `internalRender` и `renderSpeech` методы
- Зарегистрировать его, добавив ее в модуль подготовки отчетов элемент реестра

Давайте рассмотрим в качестве примера и реализовать простой элемент индикатор хода выполнения:

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

Вот и все. Теперь просто Зарегистрируйте класс индикатор хода выполнения с помощью модуля подготовки отчетов:

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="implement-and-register-a-custom-action"></a>Реализация и регистрация настраиваемого действия

Действия по созданию настраиваемого действия инструмент Adaptive Cards по сути те же для пользовательских элементов. Ниже приведен простой пример действие оповещения, который просто отображает окно сообщения с текстом, можно настроить:

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

Зарегистрируйте новое действие:

```
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a>Пример

Ниже приведен пример карточки, использующего элемент ProgressBar и AlertAction действие.
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

А вот подготовкой к просмотру: ![образа](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)