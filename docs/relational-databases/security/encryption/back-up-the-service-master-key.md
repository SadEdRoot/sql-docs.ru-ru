---
title: "Создание резервной копии главного ключа службы | Документация Майкрософт"
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
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 630f9c3ecdf47e6cb7a5d9f2a7970bea99d330a9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="back-up-the-service-master-key"></a>Создание резервной копии главного ключа службы
  В этом разделе описано, как выполнить резервное копирование главного ключа службы [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Главный ключ службы является корневым элементом иерархии шифрования. Поэтому необходимо создать его резервную копию, которая должна храниться в надежном месте. Создание такой резервной копии должно быть одной из первых задач администрирования, выполненных на сервере.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   [Создание резервной копии главного ключа службы](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Главный ключ должен быть открыт и, таким образом, расшифрован, прежде чем производится его резервное копирование. Если он зашифрован с помощью главного ключа службы, то главный ключ не нужно открывать явным образом, но если главный ключ зашифрован только с помощью пароля, он должен быть явным образом открыт.  
  
-   Рекомендуется создать резервную копию главного ключа сразу же после его создания и затем сохранить в надежном месте.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требует разрешения CONTROL для базы данных.  
  
##  <a name="Procedure"></a> Использование Transact-SQL  
  
#### <a name="to-back-up-the-service-master-key"></a>Создание резервной копии главного ключа службы  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]установите соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , содержащим главный ключ службы, для которого необходимо создать резервную копию.  
  
2.  Задайте пароль, который будет использоваться для шифрования главного ключа службы на носителе данных резервных копий. Пароль проходит проверку сложности. Дополнительные сведения см. в разделе [Password Policy](../../../relational-databases/security/password-policy.md).  
  
3.  Получите съемный носитель данных резервной копии для хранения главного ключа.  
  
4.  Укажите каталог NTFS, в котором будет создана резервная копия главного ключа. В этом каталоге будет сохранен файл, созданный в следующем шаге. Он должен быть защищен с помощью списка управления доступом со строгими ограничениями.  
  
5.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6.  На стандартной панели выберите пункт **Создать запрос**.  
  
7.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Путь к файлу ключа и пароль ключа (если он существует) будет отличаться от вышеуказанного. Убедитесь, что оба этих параметра соответствуют вашему серверу и ключу.  
  
8.  Скопируйте файл на носитель данных резервных копий и проверьте правильность копирования.  
  
9. Сохраните резервную копию в надежном месте вне системы.  
  
 Дополнительные сведения см. в разделах [OPEN MASTER KEY (Transact-SQL)](../../../t-sql/statements/open-master-key-transact-sql.md) и [BACKUP MASTER KEY (Transact-SQL)](../../../t-sql/statements/backup-master-key-transact-sql.md).  
  
  