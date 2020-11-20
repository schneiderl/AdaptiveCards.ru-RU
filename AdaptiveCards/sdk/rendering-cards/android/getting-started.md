---
title: Пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 864bb96c5875365845f7b9a7955b8a5380f034d9
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001791"
---
# <a name="getting-started---android"></a>Начало работы — Android

Это средство визуализации, использующее собственные элементы управления Android.

## <a name="install-maven-package"></a>Установка пакета Maven

[![Центральная Maven](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Опубликованные пакеты можно найти [здесь](https://search.maven.org/artifact/io.adaptivecards/adaptivecards-android) .

Чтобы добавить в проект библиотеку, включите следующую строку в gradle.build проекта в разделе зависимостей.

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
Вам нужно изменить номер версии с учетом версии, которую вы хотите добавить в проект.

## <a name="add-import"></a>Добавление импорта

Чтобы добавить объектную модель, выполните следующую операцию импорта:

```
 import io.adaptivecards.objectmodel.*;
```

Чтобы добавить средство визуализации, выполните следующую операцию импорта:

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>Дальнейшие действия

См. подробнее о [визуализации карточек](render-a-card.md).
