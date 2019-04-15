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
# <a name="render-a-card---ios"></a><span data-ttu-id="14747-102">Визуализации карт - iOS</span><span class="sxs-lookup"><span data-stu-id="14747-102">Render a card - iOS</span></span>

<span data-ttu-id="14747-103">Вот как отобразить карту с помощью пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="14747-103">Here's how to render a card using the iOS SDK.</span></span>

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="14747-104">Создание карточки из строки JSON</span><span class="sxs-lookup"><span data-stu-id="14747-104">Create a card from a JSON string</span></span>

<span data-ttu-id="14747-105">AdaptiveCard создается из строки JSON</span><span class="sxs-lookup"><span data-stu-id="14747-105">AdaptiveCard is generated from JSON string</span></span>

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a><span data-ttu-id="14747-106">Визуализации карт</span><span class="sxs-lookup"><span data-stu-id="14747-106">Render a Card</span></span>

<span data-ttu-id="14747-107">Rederer принимает инструмент adaptive Cards и конфигурации узла. HostConfig может быть пустым, и если nil, будет использоваться значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="14747-107">Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.</span></span>

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### <a name="example"></a><span data-ttu-id="14747-108">Пример</span><span class="sxs-lookup"><span data-stu-id="14747-108">Example</span></span>

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

### <a name="render-a-card-as-uiviewcontroller"></a><span data-ttu-id="14747-109">Отображать карту в виде UIViewController</span><span class="sxs-lookup"><span data-stu-id="14747-109">Render a Card as UIViewController</span></span>

<span data-ttu-id="14747-110">Модуль подготовки отчетов AdaptiveCard также может возвращать UIViewController.</span><span class="sxs-lookup"><span data-stu-id="14747-110">AdaptiveCard renderer can also return UIViewController.</span></span>

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

<span data-ttu-id="14747-111">Возвращено UIView использует Автомакет.</span><span class="sxs-lookup"><span data-stu-id="14747-111">Returned UIView uses autolayout.</span></span> <span data-ttu-id="14747-112">Ширина будет ограничение, чтобы значение, заданное параметром widthConstraint.</span><span class="sxs-lookup"><span data-stu-id="14747-112">Width will be constraint to the value set by widthConstraint.</span></span> <span data-ttu-id="14747-113">Если используется значение 0, он не будет привязан.</span><span class="sxs-lookup"><span data-stu-id="14747-113">If 0 value is used, it won't be bound.</span></span>
<span data-ttu-id="14747-114">Высота не привязан и при возврате, он будет иметь высоту суммы значений отображается все содержимое.</span><span class="sxs-lookup"><span data-stu-id="14747-114">Height is not bound, and when returned it will have the height of sums of all contents rendered.</span></span> <span data-ttu-id="14747-115">Привязать просмотреть измерение, используйте NSLayoutConstraint.</span><span class="sxs-lookup"><span data-stu-id="14747-115">To bound the view dimension, please use NSLayoutConstraint.</span></span> <span data-ttu-id="14747-116">Точные измерения доступен из контексте viewDidLayoutSubview viewcontroller его суперпредставления или его метод с тем же именем, если используется ACRViewController.</span><span class="sxs-lookup"><span data-stu-id="14747-116">The exact dimension is accessible from the context of viewDidLayoutSubview of its superview's viewcontroller or its method with the same name if ACRViewController is used.</span></span>


### <a name="compact-style-inputchoiceset"></a><span data-ttu-id="14747-117">Input.ChoiceSet компактной стиле</span><span class="sxs-lookup"><span data-stu-id="14747-117">Compact Style Input.ChoiceSet</span></span>

<span data-ttu-id="14747-118">Представление пользовательского интерфейса Input.ChoiceSet имеет UINavigationController, и он должен быть представлены в настоящее время active UIViewController переходить в UIView, разрешающее Выбор пользователя.</span><span class="sxs-lookup"><span data-stu-id="14747-118">UI representation of Input.ChoiceSet has UINavigationController, and it needs to be presented to a presently active UIViewController to transition into UIView that allows user selection.</span></span>

<span data-ttu-id="14747-119">Чтобы сделать это, реализуйте didFecthSecondaryView из ACRActionDelegate.</span><span class="sxs-lookup"><span data-stu-id="14747-119">To accomplish that, please implement didFecthSecondaryView of ACRActionDelegate.</span></span>

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

<span data-ttu-id="14747-120">Если делегат, ссылающийся не был подключен, сделайте это.</span><span class="sxs-lookup"><span data-stu-id="14747-120">If the delgate has not been hooked up, do so.</span></span>

```objective-c
adaptiveView.acrActionDelegate = self
```