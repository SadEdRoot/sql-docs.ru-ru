---
title: "Диалоговое окно \"Создание профиля и учетной записи Database Mail\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.dbmailprofileacct.f1
ms.assetid: b93ea3d4-9f22-490e-8e26-d766b454aed6
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 240967b3909a2b3796534cb29c42dfa5838be692
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="create-database-mail-profile-and-account-dialog-box"></a>Диалоговое окно «Создание профиля электронной почты и учетной записи базы данных»
  Используйте диалоговое окно **Создание профиля и учетной записи компонентов Database Mail** для создания профиля компонента Database Mail и учетной записи компонента Database Mail для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Этот профиль будет использоваться для уведомления пользователей и групп по электронной почте, когда результаты проверки бизнес-правил будут отрицательными.  
  
## <a name="database-mail-profile-and-account"></a>Профиль и учетная запись компонента Database Mail  
 *Профиль компонента Database Mail* является коллекцией учетных записей компонентов Database Mail. *Учетная запись компонента Database Mail* содержит сведения, используемые [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для отправки электронных сообщений на SMTP-сервер. При создании профиля и учетной записи в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]учетная запись автоматически добавляется в профиль и ее информация используется при рассылке электронной почты.  
  
> [!NOTE]  
>  Нельзя использовать [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] как для обновления существующего профиля или учетной записи компонента Database Mail, так и для настройки больше чем одной учетной записи в профиле. Для выполнения более сложных задач с компонентом Database Mail можно использовать среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или скрипты Transact-SQL. Дополнительные сведения см. в разделе [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md) электронной документации по SQL Server.  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Имя профиля**|Введите имя нового профиля компонента Database Mail. Это имя должно быть уникальным среди всех профилей компонентов Database Mail, настроенных для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> После создания профиля можно выбрать страницу **База данных** в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].|  
|**Имя учетной записи**|Введите имя новой учетной записи компонента Database Mail, связанной с этим профилем. Это имя должно быть уникальным среди всех учетных записей компонентов Database Mail, настроенных для базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Эта учетная запись не соответствует учетной записи [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или учетной записи пользователя Windows.|  
  
## <a name="outgoing-smtp-mail-server"></a>Исходящий (SMTP) почтовый сервер  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Адрес электронной почты**|Введите адрес электронной почты для этой учетной записи. Это адрес электронной почты, с которого отправляются электронные письма, и он должен соответствовать формату *имя_электронной_почты*@*имя_домена*. Пример адреса электронной почты: sales@contoso.com.|  
|**Отображаемое имя**|Необязательный параметр. Введите имя, которое необходимо отображать в электронных сообщениях, отправляемых от имени этой учетной записи. Пример такого отображаемого имени: Contoso Sales Group.|  
|**Адрес электронной почты для ответных сообщений**|Необязательный параметр. Введите адрес электронной почты, который будет использоваться для ответов на электронные сообщения, отправляемые от имени этой учетной записи. Пример адреса электронной почты для ответных сообщений: admin@contoso.com.|  
|**SMTP-сервер**|Введите имя или IP-адрес SMTP-сервера, который учетная запись будет использовать для отправки электронной почты. Пример формата для SMTP-сервера: **smtp.***<название_организации>***.com**. Обратитесь за помощью к администратору электронной почты.|  
|**Номер порта**|Введите номер порта SMTP-сервера для этой учетной записи. По умолчанию для SMTP используется порт 25.|  
|**Для этого сервера требуется безопасное соединение (SSL)**|Шифрование связи осуществляется с использованием протокола SSL.|  
  
## <a name="smtp-authentication"></a>Проверка подлинности SMTP  
 Почту компонента Database Mail можно отправлять с использованием учетных данных [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], других предоставленных учетных данных или анонимно. Рекомендуется создать специальную учетную запись для компонента Database Mail, если сервер электронной почты запрашивает проверку подлинности. У этой учетной записи пользователя должны быть минимальные разрешения, и она не должна использоваться в других целях.  
  
|Имя элемента управления|Description|  
|------------------|-----------------|  
|**Проверка подлинности Windows с использованием учетных данных службы компонента Database Engine**|Укажите компонент Database Mail, который должен использовать учетные данные [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] для проверки подлинности на SMTP-сервере.|  
|**обычная проверка подлинности**|Укажите, что компонент Database Mail будет использовать отдельные имя пользователя и пароль для проверки подлинности на SMTP-сервере. Эта информация будет использоваться только для проверки подлинности на почтовом сервере, при этом учетная запись не обязана соответствовать пользователю [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или пользователю компьютера, на котором выполняется [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|**Имя пользователя**|Введите имя учетной записи пользователя, которое компонент Database Mail будет использовать для входа на SMTP-сервер. Если SMTP-сервер требует обычную проверку подлинности, необходимо имя пользователя.|  
|**Пароль**|Введите пароль, который компонент Database Mail будет использовать для входа на SMTP-сервер. Пароль необходим, если SMTP-сервер требует обычную проверку подлинности.|  
|**Подтверждение пароля**|Еще раз введите пароль для подтверждения.|  
|**Анонимная проверка подлинности**|Укажите, что SMTP-серверу не требуется проверка подлинности. Компонент Database Mail не будет использовать никаких учетных данных для проверки подлинности на SMTP-сервере.|  
  
## <a name="see-also"></a>См. также:  
 [Страница "Конфигурация базы данных" (диспетчер конфигурации служб Master Data Services)](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
[Установка и настройка служб Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)
  
  