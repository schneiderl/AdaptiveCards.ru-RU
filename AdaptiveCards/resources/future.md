---
title: Стратегия развития адаптивной карты
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: 6c6e14108caefa8dd1ff854b29d4651fe9b2d15c
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553486"
---
# <a name="future-work"></a>Дальнейшей работы

Хотя мы внесли отличную хода выполнения, определение адаптивной карты, по-прежнему много работы. Мы надеемся является, через сообщества разработчиков active botness и отлично партнеров, как Slack и Kik, можно создать отличные экосистемы кросс платформенных карт.

## <a name="roadmap"></a>Стратегия

Вы увидите наших [текущий план (неконечного) здесь](https://github.com/Microsoft/AdaptiveCards/projects/8). Обратите внимание, что-то в данной статье, может быть изменена что это значение не гарантирует доставку.

## <a name="future-ideas"></a>Будущие идеи

Ниже приведены некоторые будущих идеи, которые у нас есть, которые являются просто стадии мозговой. Если вы заинтересованы в любой из них, сообщите об этом в комментарии.

### <a name="great-looking-cards-from-data"></a>Отличный выглядящие карты на основе данных

Мы знаем, многие авторы карты еще нет четко определенных данных карты. Наш план является исследование модель шаблонов, которая позволила бы карты для создаваемого (на стороне сервера или на стороне клиента) на основе данных и репозиторием четко определенных и настраиваемых шаблонов.

### <a name="make-cards-responsive"></a>Создание быстро реагирующих карточек

Макеты карт следует за событиями доступное пространство. Адаптивная карты — для адаптации к различных устройств, стили ux и и инфраструктур пользовательского интерфейса, но они еще не реактивное. Дополнительные свойства должны быть определены в элементах, позволяющих производители карты для предоставления необходимых указаний в библиотеки визуализации, поэтому они интеллектуально можно изменить макет так, поддерживающий цель карточки.

### <a name="responsive-exploration"></a>Быстрые исследования

* Добавить **важности** свойство, которое добавляет заметки к важность содержимого. Менее важное содержимое может удаляться по размеру доступного пространства
* Добавить **ограничения** и **политики** свойства, описывающие, как реагировать, когда не удается соблюсти ограничения. 
  * Скрыть содержимое или свернуть содержимое до меньшего размера.
  * Добавление пороговое значение, при превышении изменяет `columnSet` для Карусель столбцов.

### <a name="new-element-types"></a>Новых типов элементов

* Сопоставляет? -встроить карту в карточку с взаимодействие или переход к растрового изображения
* *Какие элементы той или*?

### <a name="new-rendering-libraries"></a>Новые библиотеки визуализации

* Реагирование на них?
* Xamarin?
* *Какие платформы требуются?*