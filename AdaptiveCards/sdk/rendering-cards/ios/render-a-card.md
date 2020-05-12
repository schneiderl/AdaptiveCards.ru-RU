---
title: Визуализация карточки — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6248c174775db687a5419f8feb6e0b23b0dcd870
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "82136200"
---
# <a name="render-a-card---ios"></a><span data-ttu-id="90a23-102">Визуализация карточки — iOS</span><span class="sxs-lookup"><span data-stu-id="90a23-102">Render a card - iOS</span></span>

<span data-ttu-id="90a23-103">Визуализировать карточку можно с помощью пакета SDK для iOS следующим образом.</span><span class="sxs-lookup"><span data-stu-id="90a23-103">Here's how to render a card using the iOS SDK.</span></span>

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="90a23-104">Создание карточки из строки JSON</span><span class="sxs-lookup"><span data-stu-id="90a23-104">Create a card from a JSON string</span></span>

<span data-ttu-id="90a23-105">Адаптивная карточка создается из строки JSON.</span><span class="sxs-lookup"><span data-stu-id="90a23-105">AdaptiveCard is generated from JSON string</span></span>

```objective-c

NSString *jsonStr = @"{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";
ACOAdaptiveCardParseResult *cardParseResult = [ACOAdaptiveCard fromJson:jsonStr];

/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a><span data-ttu-id="90a23-106">Отрисовка карточек</span><span class="sxs-lookup"><span data-stu-id="90a23-106">Render a Card</span></span>

<span data-ttu-id="90a23-107">Редерер принимает адаптивную карту и конфигурацию узла. Хостконфиг может быть nil, а если пусто, будет использоваться значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="90a23-107">Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.</span></span>
<span data-ttu-id="90a23-108">Полученный параметр UIView использует автоматический макет.</span><span class="sxs-lookup"><span data-stu-id="90a23-108">Returned UIView uses autolayout.</span></span> <span data-ttu-id="90a23-109">Ширина ограничивается значением, задаваемым параметром widthConstraint.</span><span class="sxs-lookup"><span data-stu-id="90a23-109">Width will be constraint to the value set by widthConstraint.</span></span> <span data-ttu-id="90a23-110">Если задано значение 0, ширина не ограничивается.</span><span class="sxs-lookup"><span data-stu-id="90a23-110">If 0 value is used, it won't be bound.</span></span>
<span data-ttu-id="90a23-111">Высота не ограничивается, и ее полученное значение является суммой значений высоты всего визуализируемого содержимого.</span><span class="sxs-lookup"><span data-stu-id="90a23-111">Height is not bound, and when returned it will have the height of sums of all contents rendered.</span></span> <span data-ttu-id="90a23-112">Для ограничения размеров представления следует использовать параметр NSLayoutConstraint.</span><span class="sxs-lookup"><span data-stu-id="90a23-112">To bound the view dimension, please use NSLayoutConstraint.</span></span> <span data-ttu-id="90a23-113">Точный размер предоставляется контекстом viewDidLayoutSubview из контролера представления или соответствующего одноименного метода, если используется ACRViewController.</span><span class="sxs-lookup"><span data-stu-id="90a23-113">The exact dimension is accessible from the context of viewDidLayoutSubview of its superview's viewcontroller or its method with the same name if ACRViewController is used.</span></span>

```objective-c
ACRRenderResult *renderResult;
if(cardParseResult.isValid){
    renderResult = [ACRRenderer render:cardParseResult.card config:nil widthConstraint:335];
}
``` 
### <a name="example"></a><span data-ttu-id="90a23-114">Пример</span><span class="sxs-lookup"><span data-stu-id="90a23-114">Example</span></span>

```objective-c
--------------------------------------------------------------------------------
ViewController.m
--------------------------------------------------------------------------------
#import "ViewController.h"
#import <SafariServices/SafariServices.h>

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];

    NSString *jsonStr = @"{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";
    ACRRenderResult *renderResult;
    ACOAdaptiveCardParseResult *cardParseResult = [ACOAdaptiveCard fromJson:jsonStr];
    if(cardParseResult.isValid){
        renderResult = [ACRRenderer render:cardParseResult.card config:nil widthConstraint:335];
    }

    if(renderResult.succeeded)
    {
        ACRView *ad = renderResult.view;
        ad.acrActionDelegate = self;
        
        UIView *view = self.view;
        view.autoresizingMask |= UIViewAutoresizingFlexibleHeight;
        [self.view addSubview:ad];
        ad.translatesAutoresizingMaskIntoConstraints = NO;
        
        [NSLayoutConstraint constraintWithItem:ad attribute:NSLayoutAttributeCenterX relatedBy:NSLayoutRelationEqual toItem:view attribute:NSLayoutAttributeCenterX multiplier:1.0 constant:0].active = YES;

        [NSLayoutConstraint constraintWithItem:ad attribute:NSLayoutAttributeCenterY relatedBy:NSLayoutRelationEqual toItem:view attribute:NSLayoutAttributeCenterY multiplier:1.0 constant:3].active = YES;
    }
}

- (void)didFetchUserResponses:(ACOAdaptiveCard *)card action:(ACOBaseActionElement *)action
{
    if(action.type == ACROpenUrl){
        NSURL *url = [NSURL URLWithString:[action url]];
        SFSafariViewController *svc = [[SFSafariViewController alloc] initWithURL:url];
        [self presentViewController:svc animated:YES completion:nil];
    }
}

@end

```

```swift
--------------------------------------------------------------------------------
ViewController.swift
--------------------------------------------------------------------------------

import UIKit
import SafariServices

class ViewController: UIViewController, ACRActionDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        let jsonStr = "{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";

        let cardParseResult = ACOAdaptiveCard.fromJson(jsonStr);
        if((cardParseResult?.isValid)!){
            let renderResult = ACRRenderer.render(cardParseResult!.card, config: nil, widthConstraint: 335);

            if(renderResult?.succeeded ?? false)
            {
                let ad = renderResult?.view;
                ad!.acrActionDelegate = (self as ACRActionDelegate);
                self.view.autoresizingMask = [.flexibleHeight];
                self.view.addSubview(ad!);
                ad!.translatesAutoresizingMaskIntoConstraints = false;
    
                NSLayoutConstraint(item: ad!, attribute: .centerX, relatedBy: .equal, toItem: view, attribute: .centerX, multiplier: 1.0, constant: 0).isActive = true;
                NSLayoutConstraint(item: ad!, attribute: .centerY, relatedBy: .equal, toItem: view, attribute: .centerY, multiplier: 1.0, constant: 3).isActive = true;
            }
        }
    }

    func didFetchUserResponses(_ card: ACOAdaptiveCard, action: ACOBaseActionElement)
    {
        if(action.type == ACRActionType.openUrl){
            let url = URL.init(string:action.url());
            let svc = SFSafariViewController.init(url: url!);
            self.present(svc, animated: true, completion: nil);
        }
    }

}
```
