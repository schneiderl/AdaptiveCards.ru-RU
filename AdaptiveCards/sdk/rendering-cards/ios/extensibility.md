---
title: Расширяемость — пакет SDK для iOS
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
# <a name="extensibility---ios"></a><span data-ttu-id="598b3-102">Расширяемость — iOS</span><span class="sxs-lookup"><span data-stu-id="598b3-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="598b3-103">Изменение отрисовки на элемент</span><span class="sxs-lookup"><span data-stu-id="598b3-103">Changing per element rendering</span></span>

<span data-ttu-id="598b3-104">Разработчики могут настраивать внешний вид элементов рендерред Адаптивекардс, таких как TextBlock.</span><span class="sxs-lookup"><span data-stu-id="598b3-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="598b3-105">В следующем примере показано, как можно изменить цвет фона Нумберинпут.</span><span class="sxs-lookup"><span data-stu-id="598b3-105">Following example shows how one can change background color of NumberInput.</span></span>

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

 ## <a name="additional-property"></a><span data-ttu-id="598b3-106">Дополнительное свойство</span><span class="sxs-lookup"><span data-stu-id="598b3-106">Additional Property</span></span>

 <span data-ttu-id="598b3-107">Разработчики также могут передавать дополнительные свойства в рамках полезных данных JSON.</span><span class="sxs-lookup"><span data-stu-id="598b3-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="598b3-108">Например, в дополнение к "расстоянию" и "ID" полезных данных JSON для Басекарделемент можно добавить радиус для углов TextBlock в свои полезные данные JSON.</span><span class="sxs-lookup"><span data-stu-id="598b3-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

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
 ## <a name="custom-parsing"></a><span data-ttu-id="598b3-109">Пользовательский синтаксический анализ</span><span class="sxs-lookup"><span data-stu-id="598b3-109">Custom Parsing</span></span>

<span data-ttu-id="598b3-110">Разработчики также могут иметь пользовательский синтаксический анализ и добавить новый элемент пользовательского интерфейса в карточку адпативе, например индикатор выполнения.</span><span class="sxs-lookup"><span data-stu-id="598b3-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="598b3-111">Дополнительные сведения можно узнать в CustomProgressBarRenderer.mm.</span><span class="sxs-lookup"><span data-stu-id="598b3-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="598b3-112">Пользовательское средство синтаксического анализа должно реализовать протокол Акоибасекарделементпарсер.</span><span class="sxs-lookup"><span data-stu-id="598b3-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="598b3-113">метод Десериализетокустомелемент должен анализировать заданную полезную нагрузку JSON, заданную как NSData, и возвращать указатель на объект UIView, который будет добавлен в объект Адаптивекард для просмотра.</span><span class="sxs-lookup"><span data-stu-id="598b3-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c