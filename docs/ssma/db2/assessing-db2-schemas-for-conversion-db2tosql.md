---
title: "Оценка схемы DB2 для преобразования (DB2ToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8892f5a4-72ba-4406-8649-7a9d67f4c1d9
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a3aee9d8a612357fc8023f03d4dca20d309b899c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="assessing-db2-schemas-for-conversion-db2tosql"></a>Оценка схемы DB2 для преобразования (DB2ToSQL)
Прежде чем загружать объекты и переносить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], следует определить быть сложность миграции и о том, сколько времени займет миграции. SSMA можно создать отчет об оценки, который показывает процент объекты, которые будут преобразованы. SSMA также позволяет просматривать конкретные проблемы, вызывающие ошибки преобразования.  
  
## <a name="creating-assessment-reports"></a>Создание отчетов для оценки  
При создании этого отчета оценки, SSMA преобразует выбранные объекты базы данных DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] синтаксис, а затем отображает результаты.  
  
**Создание отчета оценки**  
  
1.  В обозревателе метаданных DB2 выберите схемы для оценки.  
  
2.  Чтобы исключить отдельные объекты, снимите флажки рядом с теми.  
  
3.  Щелкните правой кнопкой мыши **схемы**, а затем выберите **создать отчет**.  
  
    Можно также анализировать отдельных объектов, щелкните правой кнопкой мыши объект, а затем выбрав **создать отчет**.  
  
    SSMA будет отображаться ход выполнения в строке состояния в нижней части окна. Если отображается область вывода, также отображаются сообщения в области вывода.  
  
    После завершения оценки [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] помощник по миграции для DB2: появится окно отчета оценки.  
  
## <a name="using-assessment-reports"></a>С помощью оценки отчетов  
Окно отчета оценки содержит три панели:  
  
-   Левая панель содержит иерархию объектов, включенных в отчет оценки. Можно просматривать иерархию и выбрать объекты и категории объектов, чтобы просмотреть статистику преобразования и кода.  
  
-   Содержимое в правой области зависит от элемента, выбранного на панели слева.  
  
    Если выбрана группа объектов, схемы или если выбрать таблицу, правая панель содержит панель статистики преобразования и объектов в области категории. Панель статистики преобразования показывает статистику преобразования для выбранных объектов. Объекты по области категории показывает статистику преобразования для объекта или категории объектов.  
  
    Если выбрана функция, пакетов, процедуры, последовательности или представления, правая панель содержит статистику, исходный код и целевого кода.  
  
    -   В верхней области отображаются общую статистику для объекта. Может потребоваться развернуть **статистики** для просмотра этих сведений.  
  
    -   Исходная область показывает исходный код объекта, выбранного на панели слева. Выделенные области отображения проблемных исходного кода.  
  
    -   Целевая область отображается преобразованный код. Красный текст показывает проблемный кода и сообщения об ошибках.  
  
-   На нижней панели отображаются сообщения преобразования, сгруппированные по номеру сообщения. Можно щелкнуть **ошибки**, **предупреждения**, или **сведения** для категорий сообщений, а затем разверните группу сообщений. Щелкните отдельное сообщение выберите объект в области слева и отображения сведений в правой области.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Анализ проблем преобразования с помощью отчета оценки  
Панель статистики преобразования показывает статистику преобразования. Если для какой-либо категории процент меньше 100 процентов, следует определить, почему преобразование не выполнено.  
  
**Для просмотра проблем преобразования**  
  
1.  Создание отчета оценки с помощью инструкций в предыдущей процедуре.  
  
2.  В левой области разверните схемы или папки, которые имеют красный значок ошибки. По-прежнему развертывая элементы, пока не появится отдельный элемент, не удалось выполнить преобразование.  
  
3.  В верхней части области источник, нажмите кнопку **Далее проблема**.  
  
    Неисправного кода выделяется, как связанные код в области навигации целевой.  
  
4.  Просмотрите сообщения об ошибках и определите, что необходимо сделать с объектом, вызвавшую ошибку преобразования:  
  
    -   Обновите синтаксис DB2 в SSMA. Синтаксис для процедур, функций, триггеров, упакованные функции и процедуры упакованных можно обновить. Чтобы обновить синтаксис, выберите объект на панели обозревателя метаданных DB2, нажмите кнопку **SQL** вкладку, а затем изменить код SQL. Если покинуть элемент будет предложено сохранить изменения синтаксиса. Можно просмотреть ошибки для объекта на **отчетов** вкладки.  
  
    -   В DB2 можно изменить объект DB2 для удаления или изменения неисправного кода. Чтобы загрузить обновленный код в SSMA, необходимо обновить метаданные. Дополнительные сведения см. в разделе [подключение к базе данных DB2 &#40; DB2ToSQL &#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
    -   Объект можно исключить из процесса миграции. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] обозревателя метаданных и обозревателя метаданных DB2, снимите флажок рядом с элементом, прежде чем загрузить объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и перенос данных из DB2.  
  
## <a name="next-step"></a>Следующий шаг  
[Преобразование схемы DB2 &#40; DB2ToSQL &#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных DB2 в SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
