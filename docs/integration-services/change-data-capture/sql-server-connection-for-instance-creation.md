---
title: "Соединение с SQL Server для создания экземпляров | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 65f20b235b6a3c4bd22ce754467f36a9b03fdaab
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-connection-for-instance-creation"></a>Соединение с SQL Server для создания экземпляров
  Одним из первых шагов при создании экземпляра CDC Oracle является создание базы данных CDC на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта база данных CDC должна быть подготовлена к работе CDC SQL Server, для чего требуется имя входа, которое является членом предопределенной роли сервера `sysadmin` .  
  
 Если пользователь, запускающий мастер **создания экземпляра Oracle CDC** , не является членом предопределенной роли сервера `sysadmin` , то открывается диалоговое окно **Соединение с SQL Server** , где необходимо ввести учетные данные члена роли `sysadmin` , чтобы обеспечить подготовку базы данных задачей CDC SQL Server. При создании базы данных CDC имя входа `sysadmin` удаляется, а работа возобновляется с первоначальным именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое использовалось для входа в консоль конструктора Oracle.  
  
## <a name="task-list"></a>Список задач  
 В диалоговом окне **Соединение с SQL Server** введите следующие данные.  
  
 **Имя сервера**  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Проверка подлинности**  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows.**  
  
-   **Проверка подлинности SQL Server**. При выборе этого варианта необходимо ввести **Имя** и **Пароль** для пользователя в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым устанавливается соединение.  
  
 Имя входа должно иметь роль базы данных, которая обеспечивает доступ к базе данных MSXCDCDB. Рекомендуется, чтобы имя входа также имело доступ ко всем другим используемым базам данных. В противном случае пользователь не сможет просматривать данные из этих баз данных.  
  
 **Параметры**  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания соединения**. Введите время (в секундах), в течение которого служба CDC для Oracle ожидает соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**. Введите время (в секундах), в течение которого служба Windows CDC Oracle ожидает выполнения команды. Значение по умолчанию — **30**.  
  
-   **Шифрование соединения**. Выберите параметр **Шифровать соединение** , чтобы обмен данными между службой Oracle CDC Service и целевым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнялся по зашифрованному соединению.  
  
-   **Дополнительно**: нажмите кнопку **Дополнительно** и при необходимости введите любые дополнительные свойства подключения в диалоговом окне "Дополнительные свойства подключения".  
  
     Дополнительные сведения о диалоговом окне «Дополнительные свойства подключения» см. в разделе [Advanced Connection Properties](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Создание базы данных изменения SQL Server](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [Соединение с SQL Server разрешения, необходимые конструктору CDC](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  