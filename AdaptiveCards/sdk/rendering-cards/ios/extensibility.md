---
title: Расширяемость — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 13245ced3f4f657e13793bfdf1d212e44d2b6a41
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454767"
---
# <a name="extensibility---ios"></a>Расширяемость — iOS

## <a name="changing-per-element-rendering"></a>Изменение отрисовки на элемент

Разработчики могут настраивать внешний вид элементов рендерред Адаптивекардс, таких как TextBlock.
В следующем примере показано, как можно изменить цвет фона Нумберинпут.

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## <a name="additional-property"></a>Дополнительное свойство

 Разработчики также могут передавать дополнительные свойства в рамках полезных данных JSON.
Например, в дополнение к "расстоянию" и "ID" полезных данных JSON для Басекарделемент можно добавить радиус для углов TextBlock в свои полезные данные JSON.

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```

 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```
 ## <a name="custom-parsing"></a>Пользовательский синтаксический анализ

Разработчики также могут иметь пользовательский синтаксический анализ и добавить новый элемент пользовательского интерфейса в карточку адпативе, например индикатор выполнения. Дополнительные сведения можно узнать в CustomProgressBarRenderer.mm.
Пользовательское средство синтаксического анализа должно реализовать протокол Акоибасекарделементпарсер. метод Десериализетокустомелемент должен анализировать заданную полезную нагрузку JSON, заданную как NSData, и возвращать указатель на объект UIView, который будет добавлен в объект Адаптивекард для просмотра.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c