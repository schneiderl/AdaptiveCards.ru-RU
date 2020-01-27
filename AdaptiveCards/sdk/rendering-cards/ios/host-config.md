---
title: Конфигурация узла — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: fa420c0a6e9e9b7e5713b6cc528de39335f0b56c
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727482"
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

Редерер принимает адаптивную карту и конфигурацию узла. Хостконфиг может быть nil, а если пусто, будет использоваться значение по умолчанию.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```

## <a name="customization"></a>Настройка

Существует три способа настройки адаптивной визуализации карт:

1. Конфигурация узла
2. XIB
3. Отрисовка пользовательского элемента
