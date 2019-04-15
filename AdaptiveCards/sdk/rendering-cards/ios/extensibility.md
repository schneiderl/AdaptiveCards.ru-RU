---
title: Расширяемость – пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c3dcae7ef2347201b5f7ce02baf3204db7ee27d6
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553566"
---
# <a name="extensibility---ios"></a>Расширяемость – iOS

## <a name="changing-per-element-rendering"></a>Изменение каждого элемента визуализации

Разработчики могут настраивать внешний вид элементов AdaptiveCards renderred, таких как TextBlock.
Пример показывает, каким образом могут изменять цвет фона NumberInput.

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

 Разработчики также могут отправлять в дополнительных свойствах, как часть полезных данных json.
Например помимо «интервал» и «идентификатор» для полезных данных json для BaseCardElement, может добавить radius для углов TextBlock его полезные данные json.

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
 ## <a name="custom-parsing"></a>Custom синтаксического анализа

Разработчики могут также иметь пользовательского анализа и имеют новый элемент пользовательского интерфейса, добавляемый adpative карты, например индикатор хода выполнения. Проверьте CustomProgressBarRenderer.mm детализации.
Настраиваемое средство синтаксического анализа необходимо реализовать протокол ACOIBaseCardElementParser. метод deserializeToCustomElement следует анализирует, учитывая полезные данные json, заданной в качестве NSData и возвращают указатель на объект UIView, который добавляется к объекту AdaptiveCard к просмотру.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c