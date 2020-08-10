---
title: Инструменты адаптивных карточек
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 819788313d78b4057fb5d3dc4d5a9be658566642
ms.sourcegitcommit: 996fc604e59f72ba1dd96c29f4b517862a5264e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87566028"
---
# <a name="tools-and-samples"></a>Инструменты и примеры

## <a name="card-designer"></a>Конструктор карточек 

Вам нужен инструмент для проектирования карточек? Можете больше не искать! Вот удобный браузерный конструктор адаптивных карточек: [https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![снимок экрана конструктора](media/tools/designer.jpg)](https://adaptivecards.io/designer)

### <a name="embed-the-designer-into-your-app"></a>Внедрение конструктора в приложение

Но зачем отправлять пользователей куда-то, если можно **внедрить конструктор карточек непосредственно в свое веб-приложение** с помощью нашей библиотеки JavaScript. 

Чтобы приступить к работе, ознакомьтесь с пакетом [adaptivecards-designer](https://npmjs.com/adaptivecards-designer).

## <a name="schema-validation"></a>Проверка схемы

Проверка схемы — это эффективный способ упрощения процесса разработки и добавления инструментов.

Мы предоставили полный [JSON-файл](https://adaptivecards.io/schemas/1.2.0/adaptive-card.json) для редактирования и проверки адаптивных карт на основе JSON. Обратите внимание на то, что URL-адрес схемы соответствует версии, поэтому более новые версии адаптивных карточек будут иметь соответствующий URL-адрес.

В Visual Studio и Visual Studio Code можно включить автоматическую функцию IntelliSense, добавив ссылку `$schema`.

![Неправильное значение](media/tools/invalidjson1.png)

![Автозаполнение](media/tools/autocomplete.png)

## <a name="example"></a>Пример

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extensions"></a>Расширения Visual Studio Code

### <a name="adaptive-cards-studio"></a>**Студия адаптивных карточек**

![магазин](https://madewithcards.blob.core.windows.net/uploads/29bb3d02-2158-40b8-8420-4dd1f15da34c-acstudio.png)

С помощью Студии адаптивных карточек можно создавать карточки непосредственно в Visual Studio Code. Расширение автоматически обнаруживает все адаптивные карточки в рабочем пространстве и позволяет легко изменять шаблон карточки, а также примеры данных.

[Дополнительные сведения и установка из Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=madewithcardsio.adaptivecardsstudiobeta)


### <a name="adaptive-card-viewer"></a>**Средство просмотра адаптивных карточек**

Мы создали расширение Visual Studio Code, которое позволяет визуализировать редактируемую карту в реальном времени в самом редакторе. 

![Расширение](media/tools/vscode-extension.png)

Чтобы установить его, откройте Marketplace для расширений и выполните поиск **Adaptive Card Viewer**.

![магазин](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Использование

При редактировании JSON-файла со свойством адаптивной карточки `$schema` его можно просмотреть с помощью `Ctrl+Shift+V A`.
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Параметры

Следующий параметр Visual Studio Code доступен для Adaptive Card Viewer. Его можно задать в разделе "Параметры пользователя" или "Параметры рабочей области".

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Пример визуализатора WPF

[Пример проекта визуализатора WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карточки с использованием WPF или XAML на компьютере с Windows.  Доступен встроенный редактор `hostconfig`, в котором можно редактировать и просматривать параметры HostConfig. Сохраните эти параметры в JSON-файл, чтобы использовать их для отрисовки в своем приложении.

![Визуализатор WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Пример ImageRender для WPF

[Пример проекта ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) превращает любую карточку в PNG-файл из командной строки с помощью WPF. 
