---
title: Визуализации карт - пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 625701e38389cc1a54682b72ce2315c14180e576
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552476"
---
# <a name="render-a-card---ios"></a>Визуализации карт - iOS

Вот как отобразить карту с помощью пакета SDK.

## <a name="create-a-card-from-a-json-string"></a>Создание карточки из строки JSON

AdaptiveCard создается из строки JSON

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a>Визуализации карт

Rederer принимает инструмент adaptive Cards и конфигурации узла. HostConfig может быть пустым, и если nil, будет использоваться значение по умолчанию.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### <a name="example"></a>Пример

```objective-c
ACRRenderResult *renderResult;
ACOHostConfigParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
ACOAdaptiveCardsParseResult *cardParseResult       = [ACOAdaptiveCards FromJson:jsonStr];

// checking parse result
if(hostconfigParseResult.IsValid == YES && cardParseResult.IsValid == YES)
{
    renderResult = [ACRRenderer render:cardParseResult.card
                                config:hostconfigParseResult.config
                       widthConstraint:300.0];
}   
    
if(renderResult.Suceeded == YES)
{
    // access returned UIView object
    ACRView *adaptiveView = renderResult.view;
    [self.view addSubview:adcVc.view];
}
```

### <a name="render-a-card-as-uiviewcontroller"></a>Отображать карту в виде UIViewController

Модуль подготовки отчетов AdaptiveCard также может возвращать UIViewController.

```objective-c
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];

renderResult.viewif(renderResult.Suceeded == YES)
{
    ACRViewController *adaptiveViewController = renderResult.viewcontroller;
    [self addChildViewController:adaptiveViewController];
    [self.view addSubview:adaptiveViewController.view];
    [adaptiveViewController didMoveToParentViewController:self];
    ...
}
```

Возвращено UIView использует Автомакет. Ширина будет ограничение, чтобы значение, заданное параметром widthConstraint. Если используется значение 0, он не будет привязан.
Высота не привязан и при возврате, он будет иметь высоту суммы значений отображается все содержимое. Привязать просмотреть измерение, используйте NSLayoutConstraint. Точные измерения доступен из контексте viewDidLayoutSubview viewcontroller его суперпредставления или его метод с тем же именем, если используется ACRViewController.


### <a name="compact-style-inputchoiceset"></a>Input.ChoiceSet компактной стиле

Представление пользовательского интерфейса Input.ChoiceSet имеет UINavigationController, и он должен быть представлены в настоящее время active UIViewController переходить в UIView, разрешающее Выбор пользователя.

Чтобы сделать это, реализуйте didFecthSecondaryView из ACRActionDelegate.

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

Если делегат, ссылающийся не был подключен, сделайте это.

```objective-c
adaptiveView.acrActionDelegate = self
```