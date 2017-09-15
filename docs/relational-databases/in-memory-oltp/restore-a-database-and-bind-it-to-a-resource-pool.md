---
title: "Восстановление базы данных и ее привязка к пулу ресурсов | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd9e0ff8de0d4c7099200dfbb329709db437bb53
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a>восстановить базу данных и привязать ее к пулу ресурсов
  Даже если у вас имеется достаточно памяти для восстановления базы данных оптимизированными для памяти таблицами, вы хотите следовать рекомендациям и привязать базу данных к именованному пулу ресурсов. Хотя база данных должна существовать до того, как вы сможете ее привязать к пулу, восстановление вашей базы данных является многоступенчатым процессом. Этот раздел поможет выполнить данный процесс.  
  
## <a name="restoring-a-database-with-memory-optimized-tables"></a>Восстановление базы данных оптимизированными для памяти таблицами  
 Следующие шаги полностью восстанавливают базу данных IMOLTP_DB и привязывают ее к Pool_IMOLTP.  
  
1.  [Восстановление с NORECOVERY](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_NORECOVERY)  
  
2.  [Создание пула ресурсов](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_createPool)  
  
3.  [Привязка базы данных к пулу ресурсов](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_bind)  
  
4.  [Восстановление с RECOVERY](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_RECOVERY)  
  
5.  [Наблюдение за производительностью пула ресурсов](../../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_Monitor)  
  
###  <a name="bkmk_NORECOVERY"></a> Восстановление с NORECOVERY  
 Когда вы восстанавливаете базу данных, NORECOVERY осуществляет создание базы данных и восстановление образа диска без потребления памяти.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
###  <a name="bkmk_createPool"></a> Создание пула ресурсов  
 Следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] создает пул ресурсов с именем Pool_IMOLTP с 50% памяти, доступной для его использования.  После создания пула Регулятор Ресурсов перенастраивается для включения Pool_IMOLTP.  
  
```tsql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
###  <a name="bkmk_bind"></a> Привязка базы данных к пулу ресурсов  
 Используйте системную функцию `sp_xtp_bind_db_resource_pool` , чтобы привязать базу данных к пулу ресурсов. Эта функция принимает два параметра: имя базы данных, за которым следует имя пула ресурсов.  
  
 Следующий код [!INCLUDE[tsql](../../includes/tsql-md.md)] определяет привязку базы данных IMOLTP_DB к пулу ресурсов Pool_IMOLTP. Привязка не начнет функционировать до тех пор, пока не будет выполнен следующий шаг.  
  
```tsql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
###  <a name="bkmk_RECOVERY"></a> Восстановление с RECOVERY  
 При восстановлении базы данных с параметром WITH RECOVERY база данных переводится в режим «в сети» и выполняется восстановление всех данных.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
###  <a name="bkmk_Monitor"></a> Наблюдение за производительностью пула ресурсов  
 После того, как база данных привязана к именованному пулу ресурсов и восстановлена параметром recovery, отследите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Объект Статистики Пула Ресурсов. Дополнительные сведения см. в разделе [SQL Server, объект Resource Pool Stats](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md).  
  
## <a name="see-also"></a>См. также:  
 [привязать базу данных с таблицами, оптимизированными для памяти, к пулу ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)   
 [SQL Server, объект Resource Pool Stats](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)   
 [sys.dm_resource_governor_resource_pools](../../relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql.md)  
  
  