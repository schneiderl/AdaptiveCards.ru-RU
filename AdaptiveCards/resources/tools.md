---
title: Средства адаптивной карты
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 35ce89653a6cf2a313518be0f221a166e1eb7711
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552506"
---
# <a name="card-designer"></a>Конструктор карточек 

Необходимости в средстве для разработки карт? Нет ничего лучше конструктор на основе веб-обозревателя инструмент adaptive Cards в [https://adaptivecards.io/designer](https://adaptivecards.io/designer)

[![Снимок экрана конструктора](media/tools/designer.jpg)](https://adaptivecards.io/designer)

## <a name="embed-the-designer-into-your-app"></a>Внедрение конструктора в приложении

Но почему отправить этим пользователям существует в том случае, когда вы можете **внедрять конструкторе карты непосредственно в веб-** приложения с помощью нашей библиотеке JavaScript. 

Ознакомьтесь с [adaptivecards конструктор](https://npmjs.com/adaptivecards-designer) пакета, чтобы приступить к работе.

# <a name="schema-validation"></a>Проверка схемы

Проверка схемы — это эффективное средство, упрощает создание и включение средств.

## <a name="json-schema"></a>Схема JSON
Мы предоставили полный [файла схемы JSON](http://adaptivecards.io/schemas/adaptive-card.json) для редактирования и проверке адаптивной карты в формате json.

В Visual Studio и Visual Studio Code можно получить автоматическое Intellisense, включая `$schema` ссылки.

![Неправильный](media/tools/invalidjson1.png)

![Автозаполнение](media/tools/autocomplete.png)

### <a name="example"></a>Пример

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "0.5",
    "body": []
}
```

# <a name="tools-and-samples"></a>Средства и примеры
Существует несколько средств и примеров в дереве исходного кода, которые полезные ссылки, а также полезные средства.

## <a name="visual-studio-code-extension"></a>Расширение Visual Studio Code
Мы создали расширение Visual Studio code, который позволяет визуализировать карты, редактируемого в режиме реального времени в самом редакторе. 

![Расширение](media/tools/vscode-extension.png)

Чтобы установить, откройте расширения Marketplace и выполните поиск **адаптивные средства просмотра карты**.

![магазин](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a>Использование

При редактировании JSON-файл с инструмент Adaptive Cards `$schema` свойство, можно просмотреть с помощью `Ctrl+Shift+V A`.
```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a>Параметры

Следующий параметр Visual Studio Code доступен для средства просмотра AdaptiveCards. Это можно задать в параметрах пользователя или параметры рабочей области.

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a>Пример визуализатора WPF
[Пример проекта визуализатор WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) позволяет визуализировать карты, использующие WPF/Xaml на компьютере Windows.  Объект `hostconfig` встроенной в редактор для редактирования и просмотра параметров конфигурации узла. Сохраните эти параметры в формате JSON, чтобы использовать их при подготовке к просмотру в приложении.

![визуализатор WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a>Пример ImageRender WPF
[ImageRender пример проекта](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) превращает всех карт в PNG из командной строки с помощью WPF. 
