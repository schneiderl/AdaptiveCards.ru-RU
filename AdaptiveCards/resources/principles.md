---
title: Мотивы и принципы
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 243ad63fc585c5afc3fa396b86ff6261e8a7ee93
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454817"
---
# <a name="motivations-and-principles"></a>Мотивы и принципы

Ниже приведены мотивы и принципы, определяющие развитие формата адаптивных карточек.

## <a name="motivations-behind-the-format"></a>Мотивы, определяющие формат

В начале 2016 года несколько команд в корпорации Майкрософт (включая команды по разработке Outlook, Windows и Bot Framework) приступили к реализации необходимых им решений ("карточек"). Они были очень похожи, и все команды разрабатывали свои решения независимо друг от друга.

- В Windows были собственные живые плитки и формат уведомлений.
-  В Bot Framework использовался набор стандартных шаблонов карточек, которые разработчики могли выбирать при отправке сообщений Bot.
- В Outlook использовался собственный формат MessageCard для сообщений с действиями.

В то же время другие платформы, такие как LINE, FaceBook Messenger, Slack и прочие, определяли собственный формат карточки. Так что несколько сотрудников корпорации Майкрософт собрались и начали работать над определением единого открытого формата карточки и набора пакетов SDK, которые:

- упростили бы обмен карточками между ведущими приложениями;
- позволили бы каждому ведущему приложению управлять стилем карточек, чтобы обеспечить согласованность оформления;
- упростили для ведущего приложения отображение карточек благодаря готовым к использованию пакетам SDK;
- имели бы ценность для сторонних производителей и, в конечном итоге, стали бы широко применяться в отрасли.

## <a name="principles-governing-adaptive-cards"></a>Принципы, управляющие адаптивными карточками

1.  **Адаптивная карточка — это _простой_ и _декларативный_ формат карточки.**

    1.  Он не предназначен ни заменить HTML или XAML, ни стать их альтернативой.
    2.  Для применения адаптивных карточек **не нужен код программной части**.
        1. Разработчики карточек не могут внедрять пользовательский или произвольный код в свои полезные данные, поэтому ведущему приложению с адаптивными карточками никогда не требуется запускать сторонний код.
        2. Динамичность и взаимодействие обеспечиваются исключительно с помощью декларативной разметки.
    3.  Это гарантирует, что усилия, необходимые для создания пакета SDK адаптивных карточек для новой платформы, останутся приемлемыми.

2.  **Формат адаптивной карточки не может предписывать использование какой бы то ни было конкретной базовой технологии.**

    1.  Формат адаптивной карточки не зависит от JavaScript, C#, Python или любого другого языка.
    2.  Аналогично, он не основывается на HTML или XAML, а также на любой другой платформе графического или пользовательского интерфейса.
    3.  Таким образом, адаптивные карточки можно отображать на любой платформе, если для нее существует отрисовщик.

3.  **Формат адаптивной карточки является _общим свойством_.**

    1.  Как и соответствующие пакеты SDK, этот формат должен предоставляться как открытый код, а его развитие должно осуществляться усилиями сообщества.
    2.  Таким образом, данный формат не принадлежит ни одной команде.

4.  **Формат адаптивной карточки не предназначен только для решений корпорации Майкрософт.**

    1.  Вместо этого он разработан в соответствии с требованиями широкого спектра приложений и вариантов использования.

5.  **Развитием формата управляет _рабочая группа по разработке адаптивных карточек_.**

    1.  Эта рабочая группа состоит из нескольких сотрудников корпорации Майкрософт, которые искренно заинтересованы в успехе формата.
    2.  Рабочая группа проводит еженедельные собрания (в настоящее время по понедельникам), во время которых рассматриваются предложения по функциям, обсуждаются и приоритизируются текущие проблемы, а также отслеживается общий ход выполнения рабочих элементов vNext.
    3.  Рабочая группа активно использует отзывы сообщества, включая внутренние группы Майкрософт, для принятия решений о развитии формата.
        1. Кто угодно может присоединиться к рабочей группе, отправив сообщение о проблеме на портале GitHub (см. ниже).
        2. Проблемы и запросы возможностей, которые основаны на фактическом использовании платформы адаптивных карточек (как разработчиками ведущих приложений, так и разработчиками карточек), заметнее всего влияют на будущее формата.
    4.  Для утверждения рабочей группой предлагаемые новые возможности:
        1. должны быть обоснованы вариантами использования из реальной жизни;
        2. должны иметь спецификацию функций.
    5.  Утвержденная новая возможность добавляется в очередь невыполненной работы и рассматривается для добавления в vNext.
        1. Критерии, используемые для определения приоритетов новых возможностей, включают в себя количество возможных сценариев, реализацию которых обеспечивает эта возможность, ее сложность, удобство обслуживания и многое другое.
        2. Если есть сомнения, лучше повременить. Гораздо проще представить хорошо спроектированную функцию позже, чем вечно использовать неправильную функцию.
    6.  Все новые функции реализуются во всех поддерживаемых пакетах SDK.
    7.  Все новые функции документируются и связываются с тестовой карточкой, публикуемой в папке Samples.
    8.  Новые версии формата и пакетов SDK проходят этап бета-тестирования.
    9.  Расписание выпуска схемы адаптивной карточки и версий пакета SDK зависит от качества, а не даты.

6.  **Взаимодействие**
    1.  Карточки, созданные в соответствии с задокументированным форматом (например, не использующие специальные расширения для ведущего приложения), будут правильно отображаться в любом ведущем приложении с поддержкой адаптивных карточек.
    2.  Единственное исключение из этого правила приведено ниже.
        1.  Некоторые ведущие приложения не обеспечивают интерактивные возможности и поэтому не могут отображать ни управляющие элементы ввода, ни действия.
        2.  Выполнение действий Action.Submit оставлено на усмотрение ведущего приложения, но не все ведущие приложения будут правильно обрабатывать все полезные данные Action.Submit. Более того, некоторые ведущие приложения могут вообще не поддерживать Action.Submit.

7.  **Формат должен быть расширяемым.**

    1.  Ведущие приложения должны иметь возможность добавления поддержки настраиваемых элементов или действий, которые выходят за рамки формата.
    2.  Это особенно важно для действий, так как разные ведущие приложения не обязательно поддерживают один и тот же набор действий.
    3.  Эти дополнения предоставляются на усмотрение ведущего приложения.
        1. Они не являются *де факто* дополнением к спецификации адаптивной карточки.
        2. Таким образом, они делают полезные данные, которые используют эти дополнения, несовместимыми с основным форматом адаптивной карточки.
        3. Однако эти дополнения можно представить рабочей группе и предложить их в качестве новых возможностей для будущей версии формата, как описано в пункте № 5.

8.  **Разработчики карточек отвечают за содержимое, а ведущее приложение — за пользовательский интерфейс.**

    1.  Ведущие приложения имеют свой стиль, поэтому карточки выглядят так, как-будто являются собственными расширениями пользовательского интерфейса приложения.
    2.  Разработчики карточек по-прежнему могут задавать стиль, но только посредством семантических выражений цветов, размеров и т. д.

9.  **Пакеты SDK будут предоставлены для наиболее популярных платформ разработки.**

    1.  Пакеты SDK позволяют легко отображать полезные данные адаптивных карточек в любом ведущем приложении.
    2.  Это гарантирует, что препятствий для начала работы как для сторонних разработчиков, так и для групп корпорации Майкрософт, будет как можно меньше.
