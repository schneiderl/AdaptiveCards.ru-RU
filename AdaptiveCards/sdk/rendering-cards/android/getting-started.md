---
title: Пакет SDK для Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: d15e0963427babe045a4db6f93800e09e0d95da9
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145504"
---
# <a name="getting-started---android"></a>Начало работы — Android

Это средство визуализации, использующее собственные элементы управления Android.

## <a name="install-maven-package"></a>Установка пакета Maven

[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Опубликованные пакеты доступны ![здесь,](https://search.maven.org/search?q=g:io.adaptivecards)

Чтобы добавить в проект библиотеку, включите следующую строку в gradle.build проекта в разделе зависимостей.

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
Вам нужно изменить номер версии с учетом версии, которую вы хотите добавить в проект.

## <a name="add-import"></a>Импорт

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
