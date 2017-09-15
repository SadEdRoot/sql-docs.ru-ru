---
title: "Просмотр и анализ трассировок с помощью приложения SQL Server Profiler | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
caps.latest.revision: 38
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 026f6f0422de3345be3dc5d44c17bf9dfcdc1137
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a>Просмотр и анализ трассировок с помощью приложения SQL Server Profiler
  Просмотр данных событий, перехваченных при трассировке с помощью программы [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает данные с учетом определенных свойств трассировки. Одним способом анализа данных сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является их копирование в другую программу, например в сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в помощник по настройке ядра СУБД [!INCLUDE[ssDE](../../includes/ssde-md.md)] . [!INCLUDE[ssDE](../../includes/ssde-md.md)] Если столбец данных **Текст** включен в трассировку, помощник по настройке может использовать файл трассировки, который содержит пакет инструкций SQL и события удаленного вызова процедуры (RPC). Для обеспечения того, чтобы при использовании помощника по настройке [!INCLUDE[ssDE](../../includes/ssde-md.md)] Д были захвачены правильные события и столбцы, используйте стандартный шаблон настройки, который поставляется с приложением [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 При открытии трассировки с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]трассировка не должна иметь обязательно расширение файла TRC, если файл был создан либо с помощью приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , либо системными хранимыми процедурами средства трассировки SQL.  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]также может считывать log-файл средства трассировки SQL и общие файлы скриптов SQL. При открытии LOG-файла средства трассировки SQL, который имеет расширение, отличное от LOG, например trace.txt, укажите значение **SQLTrace_Log** в качестве формата файла.  
  
 Можно настроить формат отображения даты и времени в приложении [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , чтобы облегчить анализ трассировки.  
  
## <a name="troubleshooting-data"></a>Данные диагностики  
 Используя приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], можно проводить диагностику данных, группируя трассировки или файлы трассировок по столбцам данных **Duration**, **CPU**, **Reads**и **Writes** . Примерами данных, которые можно использовать при диагностике, являются запросы, которые завершаются неудачно или которые имеют исключительно высокое число логических операций чтения.  
  
 Дополнительные сведения могут быть найдены путем сохранения трассировок в таблицы и использования инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] для выполнения запросов к данным событий. Например, чтобы определить, какие из событий **SQL:BatchCompleted** превысили время ожидания, выполните следующее:  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  Сервер сообщает о длительности события в микросекундах (10^-6 с), а о количестве времени, затраченного ЦП на событие, в миллисекундах (10^-3 с). В [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] графический пользовательский интерфейс по умолчанию отображает столбец **Продолжительность** в миллисекундах, но, когда данные трассировки сохраняются в файле или таблице базы данных, значение столбца **Продолжительность** записывается в микросекундах.  
  
## <a name="displaying-object-names-when-viewing-traces"></a>Отображение имен объектов при просмотре трассировок  
 Если необходимо отобразить имя объекта вместо идентификатора объекта (**Object ID**), нужно захватывать столбцы данных **Server Name** и **Database ID** вместе со столбцом данных **Object Name** .  
  
 При выборе группирования по столбцу данных **Object ID** убедитесь, что группирование выполняется вначале по столбцам данных **Server Name** и **Database ID** , а уже потом по столбцу **Object ID** . Аналогично при группировании по столбцу данных **Index ID** убедитесь, что группирование выполняется вначале по столбцам данных **Server Name**, **Database ID**и **Object ID** , а потом уже по столбцу **Index ID** . Группировать следует в таком порядке, так как идентификаторы объектов и индексов не являются уникальными для нескольких серверов и баз данных (и для объектов, соответствующих идентификаторам индексов).  
  
## <a name="finding-specific-events-within-a-trace"></a>Поиск конкретных событий в трассировке  
 Для нахождения и группировки событий в трассировке выполните следующие шаги.  
  
1.  Создайте трассировку.  
  
    -   При определении трассировки укажите столбцы данных **Event Class**, **ClientProcessID** и **Start Time** в дополнение к любым другим столбцам данных, которые необходимо захватывать. Дополнительные сведения см. в статье [Создание трассировки (SQL Server Profiler)](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md).  
  
    -   Сгруппируйте захваченные данные по столбцу данных **Event Class** и захватите трассировку в файл или таблицу. Чтобы сгруппировать захваченные данные, на вкладке **Выбор событий** диалогового окна "Свойства трассировки" выберите **Расположить столбцы**. Дополнительные сведения см. в статье [Упорядочение столбцов, отображаемых в трассировке (приложение SQL Server Profiler)](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md).  
  
    -   Запустите трассировку и остановите ее по истечении определенного времени или после захвата необходимого количества событий.  
  
2.  Поиск необходимых событий.  
  
    -   Откройте файл или таблицу трассировки и раскройте узел желаемого класса событий, например **Цепочка взаимоблокировки**. Дополнительные сведения см. в статье [Открыть файл трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) или в помощник по настройке ядра СУБД [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
    -   Найдите в данных трассировки искомые события (для ускорения поиска значений в трассировке можно воспользоваться командой **Поиск** в меню **Изменить** приложения [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ). Запомните значения в столбцах данных **ClientProcessID** и **Start Time** для искомых событий трассировки.  
  
3.  Отображение событий в контексте.  
  
    -   Откройте свойства трассировки и сгруппируйте их по столбцу данных **ClientProcessID**, а не по столбцу **Event Class** .  
  
    -   Раскройте узлы для каждого идентификатора клиентского процесса, который необходимо просмотреть. Вручную или с помощью команды **поиска** найдите в трассировке отмеченные ранее значения **Start Time**нужных событий. События отображаются в хронологическом порядке вместе с другими событиями, которые принадлежат к каждому выбранному идентификатору клиентского процесса. Например, события **Deadlock** и **Deadlock Chain**, записанные в трассировке, отображаются сразу после событий **SQL:BatchStarting**в пределах раскрытого идентификатора клиентского процесса.  
  
 Такой же метод может быть применен для поиска сгруппированных событий. Как только будут найдены искомые события, сгруппируйте их по **ClientProcessID**, **имя_приложения**или другому классу событий для просмотра соответствующей деятельности в хронологическом порядке.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр сохраненной трассировки (Transact-SQL)](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md)   
 [sys.fn_trace_getinfo (Transact-SQL)](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Просмотр сведений о фильтре &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Просмотр сведений о фильтре &#40; Transact-SQL &#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md)   
 [Откройте файл трассировки &#40; Приложение SQL Server Profiler &#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Открыть таблицу трассировки (приложение SQL Server Profiler)](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  