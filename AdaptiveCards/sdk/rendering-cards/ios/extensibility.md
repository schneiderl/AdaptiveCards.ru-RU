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
# <a name="extensibility---ios"></a><span data-ttu-id="32dba-102">Расширяемость – iOS</span><span class="sxs-lookup"><span data-stu-id="32dba-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="32dba-103">Изменение каждого элемента визуализации</span><span class="sxs-lookup"><span data-stu-id="32dba-103">Changing per element rendering</span></span>

<span data-ttu-id="32dba-104">Разработчики могут настраивать внешний вид элементов AdaptiveCards renderred, таких как TextBlock.</span><span class="sxs-lookup"><span data-stu-id="32dba-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="32dba-105">Пример показывает, каким образом могут изменять цвет фона NumberInput.</span><span class="sxs-lookup"><span data-stu-id="32dba-105">Following example shows how one can change background color of NumberInput.</span></span>

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

 ## <a name="additional-property"></a><span data-ttu-id="32dba-106">Дополнительное свойство</span><span class="sxs-lookup"><span data-stu-id="32dba-106">Additional Property</span></span>

 <span data-ttu-id="32dba-107">Разработчики также могут отправлять в дополнительных свойствах, как часть полезных данных json.</span><span class="sxs-lookup"><span data-stu-id="32dba-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="32dba-108">Например помимо «интервал» и «идентификатор» для полезных данных json для BaseCardElement, может добавить radius для углов TextBlock его полезные данные json.</span><span class="sxs-lookup"><span data-stu-id="32dba-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

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
 ## <a name="custom-parsing"></a><span data-ttu-id="32dba-109">Custom синтаксического анализа</span><span class="sxs-lookup"><span data-stu-id="32dba-109">Custom Parsing</span></span>

<span data-ttu-id="32dba-110">Разработчики могут также иметь пользовательского анализа и имеют новый элемент пользовательского интерфейса, добавляемый adpative карты, например индикатор хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="32dba-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="32dba-111">Проверьте CustomProgressBarRenderer.mm детализации.</span><span class="sxs-lookup"><span data-stu-id="32dba-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="32dba-112">Настраиваемое средство синтаксического анализа необходимо реализовать протокол ACOIBaseCardElementParser.</span><span class="sxs-lookup"><span data-stu-id="32dba-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="32dba-113">метод deserializeToCustomElement следует анализирует, учитывая полезные данные json, заданной в качестве NSData и возвращают указатель на объект UIView, который добавляется к объекту AdaptiveCard к просмотру.</span><span class="sxs-lookup"><span data-stu-id="32dba-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c