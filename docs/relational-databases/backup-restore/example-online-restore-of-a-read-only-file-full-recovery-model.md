---
title: "Пример. Оперативное восстановление файла только для чтения (модель полного восстановления) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full recovery model [SQL Server], RESTORE example
- online restores [SQL Server], full recovery model
- restore sequences [SQL Server], online
ms.assetid: 7ea2d2af-086f-48dc-9636-38dc194c7090
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ec5b93ecb4214bb9316865d70a99895bf17fffcd
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="example-online-restore-of-a-read-only-file-full-recovery-model"></a>Пример. Оперативное восстановление файла только для чтения (модель полного восстановления)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Сведения в этом разделе относятся только к базам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , использующим полную модель восстановления, которые содержат несколько файлов или файловых групп.  
  
 В этом примере база данных `adb`, которая использует модель полного восстановления, содержит три файловые группы. Файловая группа `A` доступна для записи и для чтения, файловые группы `B` и `C` доступны только для чтения. Изначально все файловые группы находятся в режиме в сети.  
  
 Необходимо восстановить файл `b1`с атрибутом «только для чтения» из файловой группы `B` базы данных `adb` . Резервное копирование выполнялось после того, как файл был переведен в режим «только для чтения», поэтому резервные копии журналов не требуются. Файловая группа `B` переводится в режим «вне сети» на период восстановления, однако оставшаяся часть базы данных остается в режиме «в сети».  
  
## <a name="restore-sequence"></a>Последовательность восстановления  
  
> [!NOTE]  
>  Синтаксис последовательности восстановления в сети тот же самый, что и в случае последовательности восстановления вне сети.  
  
 Чтобы восстановить файл, администратор базы данных использует следующую последовательность восстановления:  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup  
WITH RECOVERY   
```  
  
 Файловая группа B теперь находится в режиме в сети».  
  
## <a name="additional-examples"></a>Дополнительные примеры  
  
-   [Пример. Поэтапное восстановление базы данных (простая модель восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление отдельных файловых групп (простая модель восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Пример. Оперативное восстановление доступного только для чтения файла (простая модель восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление базы данных (модель полного восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Пример. Поэтапное восстановление только некоторых файловых групп (модель полного восстановления)](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Пример. Оперативное восстановление файла, доступного для чтения и записи (модель полного восстановления)](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
## <a name="see-also"></a>См. также:  
 [Восстановление в сети (SQL Server)](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Обзор процессов восстановления (SQL Server)](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Восстановление файлов (модель полного восстановления)](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  