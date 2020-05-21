---
title: Конфигурация узла — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 614fc4a91941f59e422470c37ee90faa547bcede
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631307"
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

Модуль подготовки отчетов использует адаптивную карту и конфигурацию узла. Хостконфиг может быть nil, а если пусто, будет использоваться значение по умолчанию.

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
