---
title: "Смена контекста кластера HADR экземпляра сервера (SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 29d356ca6c432963015a4c9f4a81702b97812c51
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a>Смена контекста кластера HADR экземпляра сервера (SQL Server)
  В этом разделе описывается переключение контекста кластера HADR экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)] в [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] и более поздних версий. *Контекст кластера HADR* определяет кластер отказоустойчивой кластеризации Windows Server (WSFC), который управляет метаданными для реплик доступности, размещенных в экземпляре сервера.  
  
 Переключать контекст кластера HADR следует только во время миграции с кластера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] на экземпляр [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] в новом кластере WSFC. Миграция с кластера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] поддерживает обновление операционной системы до [!INCLUDE[win8](../../../includes/win8-md.md)] или [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] с минимальным временем простоя групп доступности. Дополнительные сведения см. в документе [Миграция между кластерами групп доступности AlwaysOn для обновления ОС](http://msdn.microsoft.com/library/jj873730.aspx).  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Переключение контекста кластера реплики доступности с помощью:**  [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После переключения контекста кластера реплики доступности](#FollowUp)  
  
-   [Связанные задачи](#RelatedTasks)  
  
-   [См. также](#RelatedContent)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
> [!CAUTION]  
>  Переключать контекст кластера HADR следует только во время миграции между кластерами развертываний [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Переключать контекст кластера HADR можно только с локального кластера WSFC на удаленный и обратно с удаленного кластера на локальный. Нельзя переключить контекст кластера HADR с одного удаленного кластера на другой удаленный кластер.  
  
-   Контекст кластера HADR можно переключить на удаленный кластер, только если на экземпляре SQL Server не размещено ни одной реплики доступности.  
  
-   Удаленный контекст кластера HADR можно переключить обратно на локальный кластер в любое время. Однако контекст нельзя переключать повторно, пока на экземпляре сервера содержатся реплики доступности.  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   На экземпляре сервера, на котором необходимо изменить контекст кластера HADR, должна выполняться [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] или более новая версия (выпуск Enterprise Edition или выше).  
  
-   Экземпляр сервера должен быть включен для AlwaysOn. Дополнительные сведения см. в разделе [Включение и отключение групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Чтобы отвечать требованиям к переключению с контекста локального кластера на контекст удаленного кластера, на экземпляре сервера не могут размещаться реплики доступности. Представление каталога [sys.availability_replicas](../../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md) не должно возвращать строк.  
  
     Если на экземпляре сервера существуют реплики доступности, то перед изменением контекста кластера HADR необходимо выполнить одно из следующих действий.  
  
    |Роль реплики|Действие|Ссылка|  
    |------------------|------------|----------|  
    |Первичная|Перевод группы доступности в режим «вне сети».|[Перевод группы доступности в режим "вне сети" (SQL Server)](../../../database-engine/availability-groups/windows/take-an-availability-group-offline-sql-server.md)|  
    |Вторичная|Удалить реплику из ее группы доступности|[Удаление вторичной реплики из группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   Перед тем как станет возможным переключение с удаленного кластера на локальный кластер, все локальные реплики с синхронной фиксацией должны перейти в состояние SYNCHRONIZED.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Рекомендуется указывать полное имя домена. Это необходимо потому, что для поиска целевого IP-адреса короткого имени ALTER SERVER CONFIGURATION использует разрешение DNS. В некоторых ситуациях в зависимости от порядка поиска DNS использование кратких имен может вызвать затруднения. Например, рассмотрим следующую команду, которая выполняется на узле в домене `abc` (`node1.abc.com`). Целевым кластером назначения является кластер `CLUS01` в домене `xyz` (`clus01.xyz.com`). Однако на узлах локального домена также размещен кластер с именем `CLUS01` (`clus01.abc.com`).  
  
     Если было указано короткое имя целевого кластера `CLUS01`, разрешение имени DNS может вернуть IP-адрес неправильного кластера `clus01.abc.com`. Чтобы избежать подобной путаницы, указывайте полное имя целевого кластера, как показано в следующем примере:  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
  
-   **имя входа SQL Server**  
  
     Необходимо разрешение CONTROL SERVER.  
  
-   **учетная запись службы SQL Server**  
  
     Учетная запись службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра сервера должна иметь следующее:  
  
    -   Разрешение на открытие целевого кластера WSFC.  
  
    -   Доступ в режиме чтения или записи к удаленному WSFC.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение контекста кластера WSFC для реплики доступности**  
  
1.  Подключитесь к экземпляру сервера, на котором размещена либо первичная, либо вторичная реплика группы доступности.  
  
2.  Используйте предложение SET HADR CLUSTER CONTEXT инструкции [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md) следующим образом:  
  
     ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'***кластер_windows***'** | LOCAL }  
  
     где  
  
     *кластер_windows*  
     Объект имени WSFC-кластера (CNO). Вы можете указать короткое имя или полное имя домена. Рекомендуется указывать полное имя домена. Дополнительные сведения см. в подразделе [Рекомендации](#Recommendations)ранее в этом разделе.  
  
     LOCAL  
     Локальный кластер WSFC.  
  
### <a name="examples"></a>Примеры  
 В следующем примере выполняется смена контекста кластера HADR на другой кластер. Для определения целевого кластера WSFC `clus01`в примере указывается полное имя объекта кластера `clus01.xyz.com`.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 В следующем примере выполняется смена контекста кластера HADR на локальный кластер WSFC.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После переключения контекста кластера реплики доступности  
 Новый контекст кластера HADR вступает в силу сразу, без перезапуска экземпляра сервера. Настройка контекста кластера HADR является постоянной установкой уровня экземпляра, которая остается неизменной при перезапуске экземпляра сервера.  
  
 Проверить новый контекст кластера HADR можно, выполнив запрос к динамическому административному представлению [sys.dm_hadr_cluster](../../../relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql.md) следующим образом:  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 Этот запрос должен возвращать имя кластера, на который был переключен контекст кластера HADR.  
  
 Если контекст кластера HADR был переключен на новый кластер.  
  
-   Выполняется очистка метаданных для всех реплик доступности, которые в настоящее время размещены в экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Все базы данных, которые ранее принадлежали к реплике доступности, теперь находятся в состоянии RESTORING.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Удаление прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [Перевод группы доступности в режим "вне сети" (SQL Server)](../../../database-engine/availability-groups/windows/take-an-availability-group-offline-sql-server.md)  
  
-   [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Удаление вторичной реплики из группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   [Технические статьи по SQL Server 2012](http://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
## <a name="see-also"></a>См. также:  
 [Группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация Windows Server (WSFC) с SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [ALTER SERVER CONFIGURATION (Transact-SQL)](../../../t-sql/statements/alter-server-configuration-transact-sql.md)  
  
  
