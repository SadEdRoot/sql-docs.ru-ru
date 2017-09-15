---
title: "Устранение проблем с нехваткой памяти | Документация Майкрософт"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f855e931-7502-44bd-8a8b-b8543645c7f4
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d6eef790f729a3270c0ba046d6a60114ae2da8dc
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="resolve-out-of-memory-issues"></a>Устранение проблем нехватки памяти
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[hek_1](../../includes/hek-1-md.md)] использует больше памяти, чем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и делает это по-другому. Возможно, что объем памяти, установленный и выделенный для [!INCLUDE[hek_2](../../includes/hek-2-md.md)] , станет недостаточным для растущих потребностей. В таком случае может возникнуть нехватка памяти. В этом разделе описывается восстановление из ситуации с нехваткой памяти. В статье [Наблюдение и устранение неисправностей при использовании памяти](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md) вы найдете рекомендации, которые помогут вам избежать многих ситуаций нехватки памяти.  
  
## <a name="covered-in-this-topic"></a>Темы данного раздела  
  
|Раздел|Обзор|  
|-----------|--------------|  
|[устранить ошибки восстановления базы данных, возникающие из-за нехватки памяти](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_resolveRecoveryFailures)|Что делать, если вы получите сообщение об ошибке "Выполнение операции восстановления для базы данных '*\<databaseName>*' завершилась неудачей из-за нехватки памяти в пуле ресурсов '*\<resourcePoolName>*'".|  
|[устранить влияния нехватки свободной памяти на рабочую нагрузку](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_recoverFromOOM)|Что следует предпринять, если обнаружится, что недостаток памяти отрицательно влияет на производительность.|  
|[Устранение ошибок выделения страниц, возникших из-за нехватки памяти при наличии достаточных ресурсов памяти](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_PageAllocFailure)|Что делать, если вы получите сообщение об ошибке "Производится отключение выделения страниц для базы данных '*\<databaseName>*' из-за нехватки памяти в пуле ресурсов '*\<resourcePoolName>*'. …" , если объема доступной памяти достаточно для выполнения операции.|  
  
##  <a name="bkmk_resolveRecoveryFailures"></a> устранить ошибки восстановления базы данных, возникающие из-за нехватки памяти  
 При попытке восстановить базу данных может возникнуть сообщение об ошибке "Выполнение операции восстановления для базы данных '*\<databaseName>*' завершилось неудачей из-за нехватки памяти в пуле ресурсов '*\<resourcePoolName>*'". Это означает, что у сервера недостаточно памяти для восстановления базы данных.
   
Сервер, на который восстанавливается база данных, должен иметь достаточно памяти для оптимизированных для памяти таблиц в резервной копии базы данных, в противном случае база данных не подключится к сети.  
  
Если сервер имеет достаточный объем физической памяти, но по-прежнему возникает данная ошибка, возможно, что другие процессы используют слишком много памяти или операция восстановления не получает достаточный объем памяти из-за проблем с конфигурацией. При подобных проблемах воспользуйтесь следующими мерами, чтобы предоставить операции восстановления дополнительную память. 
  
-   Временно закройте выполняющиеся приложения.   
    Закрыв одно или несколько выполняющихся приложений или остановив ненужные на данный момент службы, можно освободить используемую ими память для операции восстановления. Эти приложения можно будет перезапустить после успешного завершения восстановления.  
  
-   Увеличьте значение MAX_MEMORY_PERCENT.   
    Если база данных, как и рекомендуется, [привязана к пулу ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md), то память, доступная для операции восстановления, регулируется параметром MAX_MEMORY_PERCENT. Если значение слишком мало, восстановление завершится со сбоем. В этом фрагменте кода значение параметра MAX_MEMORY_PERCENT для пула ресурсов PoolHk увеличивается до 70 % от установленной памяти.  
  
    > [!IMPORTANT]  
    >  Если сервер выполняется на ВМ и не выделен, установите такое же значение MIN_MEMORY_PERCENT, как и MAX_MEMORY_PERCENT.   
    > Дополнительные сведения см. в статье [Использование In-Memory OLTP в среде ВМ](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) .  
  
    ```tsql  
  
    -- disable resource governor  
    ALTER RESOURCE GOVERNOR DISABLE  
  
    -- change the value of MAX_MEMORY_PERCENT  
    ALTER RESOURCE POOL PoolHk  
    WITH  
         ( MAX_MEMORY_PERCENT = 70 )  
    GO  
  
    -- reconfigure the Resource Governor  
    --    RECONFIGURE enables resource governor  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
  
    ```  
  
     Дополнительные сведения о максимальных значениях параметра MAX_MEMORY_PERCENT см в разделе [Процент памяти, доступной для оптимизированных для памяти таблиц и индексов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable).  
  
-   Увеличьте значение **max server memory**.  
    Дополнительные сведения о настройке **максимальной памяти сервера** см. в разделе [Оптимизация производительности сервера с помощью параметров конфигурации памяти](http://technet.microsoft.com/library/ms177455\(v=SQL.105\).aspx).  
  
##  <a name="bkmk_recoverFromOOM"></a> устранить влияния нехватки свободной памяти на рабочую нагрузку  
 Очевидно, проще всего вообще избегать ситуаций, связанных с нехваткой памяти. Помочь в этом может хорошее планирование и отслеживание. Однако даже самое хорошее планирование не гарантирует стабильной работы, и возникновение нехватки памяти всегда возможно. Для устранения этой ситуации необходимо выполнить два действия.  
  
1.  [Откройте выделенное административное соединение](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_openDAC)  
  
2.  [Примените действие по исправлению](../../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md#bkmk_takeCorrectiveAction)  
  
###  <a name="bkmk_openDAC"></a> Откройте выделенное административное соединение  
 В Microsoft SQL Server есть выделенное административное соединение. С помощью выделенного административного соединения администратор может обращаться к запущенному экземпляру ядра СУБД SQL Server для устранения неполадок на сервере, даже если сервер не отвечает на другие клиентские соединения. Выделенные административные соединения доступны в программе `sqlcmd` и в среде SQL Server Management Studio (SSMS).  
  
 Рекомендации по использованию `sqlcmd` и выделенных административных соединений см. в разделе [Использование выделенного административного соединения](http://msdn.microsoft.com/library/ms189595\(v=sql.100\).aspx/css). Использование выделенного административного соединения в среде SSMS описано в статье [Как применять выделенное административное соединение с помощью среды SQL Server Management Studio](http://msdn.microsoft.com/library/ms178068.aspx).  
  
###  <a name="bkmk_takeCorrectiveAction"></a> Примените действие по исправлению  
 Для устранения проблемы с нехваткой памяти необходимо либо освободить имеющуюся память путем сокращения объема ее использования, либо выделить дополнительный объем памяти таблицам в памяти.  
  
#### <a name="free-up-existing-memory"></a>Освобождение имеющейся памяти  
  
##### <a name="delete-non-essential-memory-optimized-table-rows-and-wait-for-garbage-collection"></a>Удаление неважных строк оптимизированных для памяти таблиц и ожидание выполнения сборки мусора  
 Можно удалить неважные строки из оптимизированной для памяти таблицы. Сборщик мусора делает объем памяти, используемый этими строками, доступным. , и делает это по-другому. Компонент In-memory OLTP выполняет сбор ненужных строк агрессивно. Однако долго выполняющаяся транзакция может помешать сбору мусора. Например, если имеется транзакция, которая выполняется в течение 5 минут, все версии строк, созданные из-за операции обновления или удаления во время выполнения транзакции, не подпадают под сборку мусора.  
  
##### <a name="move-one-or-more-rows-to-a-disk-based-table"></a>Переместить одну или несколько строк в таблице на диске  
 В следующих статьях TechNet представлены рекомендации по перемещению строк из таблиц, оптимизированных для памяти, в таблицы на диске.  
  
-   [Секционирование уровня приложения](http://technet.microsoft.com/library/dn296452\(v=sql.120\).aspx)  
  
-   [Модель приложения для секционирования таблиц, оптимизированных для памяти](http://technet.microsoft.com/library/dn133171\(v=sql.120\).aspx)  
  
#### <a name="increase-available-memory"></a>Увеличение объема доступной памяти  
  
##### <a name="increase-value-of-maxmemorypercent-on-the-resource-pool"></a>Увеличение значения MAX_MEMORY_PERCENT для пула ресурсов  
 Если именованный пул ресурсов для таблиц в памяти еще не создан, то его необходимо создать и привязать к нему базы данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)] . Инструкции по созданию пула ресурсов и привязки к нему баз данных [см. в разделе](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов [!INCLUDE[hek_2](../../includes/hek-2-md.md)] .  
  
 Если база данных [!INCLUDE[hek_2](../../includes/hek-2-md.md)] привязана к пулу ресурсов, то пользователь может увеличить процент памяти, доступной для пула. Инструкции по изменению значения MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для пула ресурсов см. в подразделе [Изменение параметров MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для существующего пула](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation) .  
  
 Увеличьте значение MAX_MEMORY_PERCENT.   
В этом фрагменте кода значение параметра MAX_MEMORY_PERCENT для пула ресурсов PoolHk увеличивается до 70 % от установленной памяти.  
  
> [!IMPORTANT]  
>  Если сервер выполняется на ВМ и не выделен, установите такое же значение MIN_MEMORY_PERCENT, как и MAX_MEMORY_PERCENT.   
> Дополнительные сведения см. в статье [Использование In-Memory OLTP в среде ВМ](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) .  
  
```tsql  
  
-- disable resource governor  
ALTER RESOURCE GOVERNOR DISABLE  
  
-- change the value of MAX_MEMORY_PERCENT  
ALTER RESOURCE POOL PoolHk  
WITH  
     ( MAX_MEMORY_PERCENT = 70 )  
GO  
  
-- reconfigure the Resource Governor  
--    RECONFIGURE enables resource governor  
ALTER RESOURCE GOVERNOR RECONFIGURE  
GO  
  
```  
  
 Дополнительные сведения о максимальных значениях параметра MAX_MEMORY_PERCENT см в разделе [Процент памяти, доступной для оптимизированных для памяти таблиц и индексов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_PercentAvailable).  
  
##### <a name="install-additional-memory"></a>Установка дополнительной памяти  
 В конечном счете наилучшим решением является установка дополнительной памяти. Если выбран этот вариант, то необходимо учитывать, что, скорее всего, также можно будет увеличить значение MAX_MEMORY_PERCENT (см. подраздел [Изменение параметров MIN_MEMORY_PERCENT и MAX_MEMORY_PERCENT для существующего пула](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md#bkmk_ChangeAllocation)), так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вряд ли будет нужно больше памяти, а это позволит выделить большую часть или даже всю установленную новую память пулу ресурсов.  
  
> [!IMPORTANT]  
>  Если сервер выполняется на ВМ и не выделен, установите такое же значение MIN_MEMORY_PERCENT, как и MAX_MEMORY_PERCENT.   
> Дополнительные сведения см. в статье [Использование In-Memory OLTP в среде ВМ](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9) .  
  
##  <a name="bkmk_PageAllocFailure"></a> Устранение ошибок выделения страниц, возникших из-за нехватки памяти при наличии достаточных ресурсов памяти  
 Если в журнале ошибок появится сообщение "Производится отключение выделения страниц для базы данных '*\<databaseName>*' из-за нехватки памяти в пуле ресурсов '*\<resourcePoolName>*'", см. статью по адресу http://go.microsoft.com/fwlink/?LinkId=330673", а доступной физической памяти достаточно для выделения страницы, это может быть связано с отключенным регулятором ресурсов. Если регулятор ресурсов отключен, то MEMORYBROKER_FOR_RESERVE вызывает искусственную нагрузку на ресурсы памяти.  
  
 Для устранения этой ошибки необходимо включить регулятор ресурсов.  
  
 См. в разделе [Включение регулятора ресурсов](http://technet.microsoft.com/library/bb895149.aspx) дополнительные сведения об ограничениях, а также рекомендации по включению регулятора ресурсов через обозреватель объектов, свойства регулятора ресурсов или Transact-SQL.  
  
## <a name="see-also"></a>См. также:  
 [Управление памятью для компонента In-Memory OLTP](http://msdn.microsoft.com/library/d82f21fa-6be1-4723-a72e-f2526fafd1b6)   
 [Наблюдение и устранение неисправностей при использовании памяти](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)   
 [см. в разделе](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Использование In-Memory OLTP в среде ВМ](http://msdn.microsoft.com/library/27ec7eb3-3a24-41db-aa65-2f206514c6f9)  
  
  
