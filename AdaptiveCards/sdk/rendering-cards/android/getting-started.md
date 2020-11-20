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
# <a name="getting-started---android"></a><span data-ttu-id="d1f1c-102">Начало работы — Android</span><span class="sxs-lookup"><span data-stu-id="d1f1c-102">Getting started - Android</span></span>

<span data-ttu-id="d1f1c-103">Это средство визуализации, использующее собственные элементы управления Android.</span><span class="sxs-lookup"><span data-stu-id="d1f1c-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="d1f1c-104">Установка пакета Maven</span><span class="sxs-lookup"><span data-stu-id="d1f1c-104">Install Maven package</span></span>

<span data-ttu-id="d1f1c-105">[![Центральная Maven](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="d1f1c-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="d1f1c-106">Опубликованные пакеты можно найти [здесь](https://search.maven.org/artifact/io.adaptivecards/adaptivecards-android) .</span><span class="sxs-lookup"><span data-stu-id="d1f1c-106">You can find the published packages [here](https://search.maven.org/artifact/io.adaptivecards/adaptivecards-android)</span></span>

<span data-ttu-id="d1f1c-107">Чтобы добавить в проект библиотеку, включите следующую строку в gradle.build проекта в разделе зависимостей.</span><span class="sxs-lookup"><span data-stu-id="d1f1c-107">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="d1f1c-108">Вам нужно изменить номер версии с учетом версии, которую вы хотите добавить в проект.</span><span class="sxs-lookup"><span data-stu-id="d1f1c-108">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="d1f1c-109">Добавление импорта</span><span class="sxs-lookup"><span data-stu-id="d1f1c-109">Add import</span></span>

<span data-ttu-id="d1f1c-110">Чтобы добавить объектную модель, выполните следующую операцию импорта:</span><span class="sxs-lookup"><span data-stu-id="d1f1c-110">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="d1f1c-111">Чтобы добавить средство визуализации, выполните следующую операцию импорта:</span><span class="sxs-lookup"><span data-stu-id="d1f1c-111">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="d1f1c-112">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="d1f1c-112">Next steps</span></span>

<span data-ttu-id="d1f1c-113">См. подробнее о [визуализации карточек](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="d1f1c-113">See [Render a card](render-a-card.md) for the next steps!</span></span>
