---
title: Пакет SDK для Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: b5f1279317e6b34d2e3bccee2625d972ac185e04
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134275"
---
# <a name="getting-started---android"></a><span data-ttu-id="f36d7-102">Начало работы — Android</span><span class="sxs-lookup"><span data-stu-id="f36d7-102">Getting started - Android</span></span>

<span data-ttu-id="f36d7-103">Это средство визуализации, использующее собственные элементы управления Android.</span><span class="sxs-lookup"><span data-stu-id="f36d7-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="f36d7-104">Установка пакета Maven</span><span class="sxs-lookup"><span data-stu-id="f36d7-104">Install Maven package</span></span>

<span data-ttu-id="f36d7-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="f36d7-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="f36d7-106">Опубликованные пакеты доступны</span><span class="sxs-lookup"><span data-stu-id="f36d7-106">You can find the published packages</span></span> ![здесь](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="f36d7-108">Чтобы добавить в проект библиотеку, включите следующую строку в gradle.build проекта в разделе зависимостей.</span><span class="sxs-lookup"><span data-stu-id="f36d7-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="f36d7-109">Вам нужно изменить номер версии с учетом версии, которую вы хотите добавить в проект.</span><span class="sxs-lookup"><span data-stu-id="f36d7-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="f36d7-110">Импорт</span><span class="sxs-lookup"><span data-stu-id="f36d7-110">Add import</span></span>

<span data-ttu-id="f36d7-111">Чтобы добавить объектную модель, выполните следующую операцию импорта:</span><span class="sxs-lookup"><span data-stu-id="f36d7-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="f36d7-112">Чтобы добавить средство визуализации, выполните следующую операцию импорта:</span><span class="sxs-lookup"><span data-stu-id="f36d7-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="f36d7-113">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="f36d7-113">Next steps</span></span>

<span data-ttu-id="f36d7-114">См. подробнее о [визуализации карточек](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="f36d7-114">See [Render a card](render-a-card.md) for the next steps!</span></span>
