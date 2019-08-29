---
title: Конфигурация узла — пакет SDK для iOS
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
# <a name="host-config---ios"></a>Конфигурация узла — iOS

Узел можно настроить с помощью Хостконфиг, который может быть создан строкой JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

Экземпляр Хостконфиг по умолчанию можно создать

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Подготовка карты с помощью конфигурации узла

Средство визуализации принимает адаптивную карточку и параметр HostConfig. Если HostConfig имеет значение NULL, применяется конфигурация по умолчанию.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```