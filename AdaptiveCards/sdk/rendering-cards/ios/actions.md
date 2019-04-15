---
title: Действия — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ff8d4924f5394b7882110f5fa38c6833fd2c3896
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553586"
---
# <a name="actions---ios"></a><span data-ttu-id="4904e-102">Действия — iOS</span><span class="sxs-lookup"><span data-stu-id="4904e-102">Actions - iOS</span></span>

<span data-ttu-id="4904e-103">Разработчики могут получать действия таких это операция SubmitAction и OpenUrl путем реализации ACRActionDelegate и задайте для него значение экземпляра AdaptiveCard.</span><span class="sxs-lookup"><span data-stu-id="4904e-103">Developers can receive actions such SubmitAction and OpenUrl by implementing ACRActionDelegate, and set it to instance of AdaptiveCard.</span></span>

```objective-c
//// delegate implementation
- (void) didFetchUserResponses:(ACOAdaptiveCard *)card action:(ACOBaseActionElement *)action
{
     if(action.type == ACROpenUrl){
         NSURL *url = [NSURL URLWithString:[action url]];
         SFSafariViewController *svc = [[SFSafariViewController alloc] initWithURL:url];
         [self presentViewController:svc animated:YES completion:nil];
     }
     else if(action.type == ACRSubmit){
         /// inputs can be examined by method inputs
         NSData * userInputsAsJson = [card inputs];
         NSString *str = [[NSString alloc] initWithData:userInputsAsJson encoding:NSUTF8StringEncoding];
         NSLog(@"user response fetched: %@ with %@", str, [action data]);
     }
}

/// register the delegate with ACRView instance
adaptiveView.acrActionDelegate = self;

/// if using ACRViewController, pass delegate as argument
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];
```