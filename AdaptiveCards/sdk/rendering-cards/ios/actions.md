---
title: Действия — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 3c0a0886ca5b4403292f8d92cccc329325909738
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454777"
---
# <a name="actions---ios"></a><span data-ttu-id="7dc64-102">Действия — iOS</span><span class="sxs-lookup"><span data-stu-id="7dc64-102">Actions - iOS</span></span>

<span data-ttu-id="7dc64-103">Разработчики могут получить такие действия, как Субмитактион и OpenUrl, реализуя Акрактионделегате, и установить их в качестве экземпляра Адаптивекард.</span><span class="sxs-lookup"><span data-stu-id="7dc64-103">Developers can receive actions such SubmitAction and OpenUrl by implementing ACRActionDelegate, and set it to instance of AdaptiveCard.</span></span>

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