---
title: Конфигурации узла - пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: b788ecc5c2371d2575e0165296365238535dd7c5
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553706"
---
# <a name="host-config---ios"></a>Host config - iOS

Узел можно настроить с помощью HostConfig которого могут быть вызваны строки JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

Можно создать экземпляр по умолчанию HostConfig

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Визуализации карт, с помощью конфигурации узла

Rederer принимает инструмент adaptive Cards и конфигурации узла. HostConfig может быть пустым, и если nil, будет использоваться значение по умолчанию.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```