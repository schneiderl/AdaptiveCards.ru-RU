---
title: Собственный стиль — пакет SDK для iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f9ed839a19ac778381fa36361ad37e95b7ab5e08
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727470"
---
# <a name="native-styling---ios"></a>Собственный стиль — iOS

Используйте XIB для точной детализации стилей.

Существует следующий XIB

| XIB | Использование |
|---|---|
| Акрбуттон. XIB | кнопки |
| Акрцеллфоркомпактмоде. XIB   | Компактный режим "Choice"|
| Акрдатепиккер. XIB | DatePicker для input. Date |
| Акрдатетекстфиелд. XIB  | TextField для input. Date |
| Акринпуттаблевиев. XIB   | Контейнер для входных данных |
| Акрлабелвиев. XIB  | TextBlock |
| Акрпиккервиев. XIB | Choice |
| Акркуиккактионмултилиневиев. XIB  | Быстрые действия с многострочными |
| Акркуиккактионвиев. XIB | Быстрые действия |
| Акртекстфиелд. XIB | Ввод |

XIB можно редактировать через XCode.
После изменения XIB в спецификацию.
Из терминала
```
ibtool --compile name.nib name.xib 
```

Например, чтобы присвоить стилю кнопку
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

Созданные файлы NIB можно затем заменить на Адаптивекардс. Framework
