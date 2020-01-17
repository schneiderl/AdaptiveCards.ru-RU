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
# <a name="getting-started---android"></a><span data-ttu-id="e3801-102">Начало работы — Android</span><span class="sxs-lookup"><span data-stu-id="e3801-102">Getting started - Android</span></span>

<span data-ttu-id="e3801-103">Это средство визуализации, использующее собственные элементы управления Android.</span><span class="sxs-lookup"><span data-stu-id="e3801-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="e3801-104">Установка пакета Maven</span><span class="sxs-lookup"><span data-stu-id="e3801-104">Install Maven package</span></span>

<span data-ttu-id="e3801-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="e3801-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="e3801-106">Опубликованные пакеты доступны</span><span class="sxs-lookup"><span data-stu-id="e3801-106">You can find the published packages</span></span> ![здесь,](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="e3801-108">Чтобы добавить в проект библиотеку, включите следующую строку в gradle.build проекта в разделе зависимостей.</span><span class="sxs-lookup"><span data-stu-id="e3801-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="e3801-109">Вам нужно изменить номер версии с учетом версии, которую вы хотите добавить в проект.</span><span class="sxs-lookup"><span data-stu-id="e3801-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="e3801-110">Импорт</span><span class="sxs-lookup"><span data-stu-id="e3801-110">Add import</span></span>

<span data-ttu-id="e3801-111">Чтобы добавить объектную модель, выполните следующую операцию импорта:</span><span class="sxs-lookup"><span data-stu-id="e3801-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="e3801-112">Чтобы добавить средство визуализации, выполните следующую операцию импорта:</span><span class="sxs-lookup"><span data-stu-id="e3801-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="e3801-113">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="e3801-113">Next steps</span></span>

<span data-ttu-id="e3801-114">См. подробнее о [визуализации карточек](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="e3801-114">See [Render a card](render-a-card.md) for the next steps!</span></span>
