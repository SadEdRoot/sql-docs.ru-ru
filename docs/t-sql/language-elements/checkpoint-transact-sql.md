---
title: CHECKPOINT (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHECKPOINT_TSQL
- CHECKPOINT
dev_langs:
- TSQL
helpviewer_keywords:
- events [SQL Server], checkpoints
- automatic checkpoints
- writing dirty pages to disk
- pages [SQL Server], dirty
- checkpoints [SQL Server]
- CHECKPOINT statement
- log truncate mode [SQL Server]
- dirty pages
- logs [SQL Server], checkpoints
- manual checkpoints [SQL Server]
- pages [SQL Server], checkpoints
ms.assetid: ccdfc689-ad4e-44c0-83f7-0f2cfcfb6406
caps.latest.revision: 59
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2c7232d1494ad48987d91ffe4dfc05e5ef47e4b5
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="checkpoint-transact-sql"></a>CHECKPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает ручную контрольную точку в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которой в данный момент установлено соединение.  
  
> [!NOTE]  
>  Сведения о различных типах контрольных точек баз данных и работе контрольных точек в целом см. в статье [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CHECKPOINT [ checkpoint_duration ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *checkpoint_duration*  
 Задается запрашиваемое количество времени в секундах для завершения ручной контрольной точки. Если задан аргумент *checkpoint_duration*, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] пытается выполнить контрольную точку в течение запрашиваемого периода времени. Аргумент *checkpoint_duration* должен быть выражением типа **int** и должен быть больше нуля. Если этот аргумент опущен, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] настраивает длительность выполнения контрольной точки таким образом, чтобы минимизировать влияние на производительность приложений базы данных. Параметр *checkpoint_duration* является дополнительным параметром.  
  
## <a name="factors-affecting-the-duration-of-checkpoint-operations"></a>Факторы, влияющие на длительность операций выполнения контрольных точек  
 Количество времени, необходимое для операции выполнения контрольной точки, увеличивается с возрастанием количества «грязных» страниц, которые необходимо записать операции. По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регулирует частоту операций записи, которые выполняет контрольная точка, для минимизации влияния на производительность. Уменьшение частоты записи увеличивает время, необходимое для завершения операции выполнения контрольной точки. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяет эту стратегию при работе с ручными контрольными точками, если только в команде CHECKPOINT не задано значение *checkpoint_duration*.  
  
 Влияние на производительность использования аргумента *checkpoint_duration* зависит от количества "грязных" страниц, уровня активности в системе и фактической задаваемой длительности. Например, если обычно для завершения операции выполнения контрольной точки необходимо 120 секунд, задание для аргумента *checkpoint_duration* величины 45 секунд ведет к тому, что серверу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет необходимо выделить контрольной точке больше ресурсов, чем количество, задаваемое по умолчанию. И наоборот, в результате задания для аргумента *checkpoint_duration* значения в 180 секунд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет выделять меньшее количество ресурсов, чем количество по умолчанию. В целом меньшее значение аргумента *checkpoint_duration* увеличивает объем ресурсов, выделяемых контрольной точке, а большее значение аргумента *checkpoint_duration* уменьшает объем выделяемых ресурсов. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда, если это возможно, завершает обработку контрольной точки, а инструкция CHECKPOINT возвращает управление сразу же по завершении обработки контрольной точки. Следовательно, в некоторых случаях выполнение контрольной точки может завершиться быстрее, чем заданный период времени, или выполняться дольше этого периода.  
  
##  <a name="Security"></a> безопасность  
  
### <a name="permissions"></a>Разрешения  
 Разрешения CHECKPOINT по умолчанию предоставляются членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_backupoperator**, и эти разрешения передаваться не могут.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Настройка интервала восстановления в конфигурации сервера](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)   
 [SHUTDOWN (Transact-SQL)](../../t-sql/language-elements/shutdown-transact-sql.md)  
  
  
