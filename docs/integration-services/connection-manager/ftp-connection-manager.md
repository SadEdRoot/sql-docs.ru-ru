---
title: "Диспетчер FTP-соединений | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8397673c7ed9dfe8ae02871f9077ed7286e49863
ms.openlocfilehash: 051dc7db2ef8aa475fa8739b097edd93d8286524
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="ftp-connection-manager"></a>диспетчер FTP-соединений
  Диспетчер FTP-соединений позволяет пакету подключаться к серверу, использующему протокол передачи файлов (FTP). Задача «FTP», включенная в комплект служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , использует этот диспетчер соединений.  
  
 При добавлении к пакету диспетчера подключений FTP [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] создает диспетчер подключений, который может быть разрешен в соединение FTP во время выполнения, устанавливает свойства диспетчера подключений и добавляет его к коллекции **Подключения** пакета.  
  
 Свойству **ConnectionManagerType** диспетчера соединений присваивается значение **FTP**.  
  
 Диспетчер FTP-сеансов может быть настроен следующим образом.  
  
-   Укажите имя и порт сервера.  
  
-   Выберите анонимный доступ или укажите имя пользователя и пароль для обычной проверки подлинности.  
  
    > [!IMPORTANT]  
    >  Диспетчер FTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
-   Задайте время ожидания, число повторных попыток и количество данных, которое будет копироваться за один раз.  
  
-   Укажите, должен ли диспетчер FTP-сеансов использовать пассивный или активный режим.  
  
 В зависимости от настройки сайта FTP, к которому подключается диспетчер FTP-сеансов, может понадобиться изменить следующие значения по умолчанию для диспетчера подключений.  
  
-   Для сервера порта устанавливается значение 21. Необходимо задать порт для прослушивания FTP-сайтом.  
  
-   Имя пользователя установлено в значение «anonymous». Необходимо предоставить учетные данные, которые требует веб-сайт FTP.  
  
## <a name="activepassive-modes"></a>Активный/пассивный режимы  
 Диспетчер FTP-соединений может отправлять и получать данные либо в активном, либо в пассивном режиме. В активном режиме подключение к данным инициируется сервером, а в пассивном режиме — клиентом.  
  
## <a name="configuration-of-the-ftp-connection-manager"></a>Настройка диспетчера FTP-соединений  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задавать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в статье [Редактор диспетчера FTP-сеансов](../../integration-services/connection-manager/ftp-connection-manager-editor.md).  
  
 Дополнительные сведения о программной настройке диспетчера подключений см. в разделах <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> и [Добавление соединений программным образом](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="ftp-connection-manager-editor"></a>редактор диспетчера FTP-сеансов
  Диалоговое окно **Редактор диспетчера FTP-соединений** используется для задания свойств подключения к серверу FTP.  
  
> [!IMPORTANT]  
>  Диспетчер FTP-соединений поддерживает только анонимную проверку подлинности и обычную проверку подлинности. Проверка подлинности Windows не поддерживается.  
  
 Дополнительные сведения о диспетчере FTP-сеансов см. в разделе [FTP Connection Manager](../../integration-services/connection-manager/ftp-connection-manager.md).  
  
### <a name="options"></a>Параметры  
 **Имя сервера**  
 Позволяет задать имя сервера FTP.  
  
 **Порт сервера**  
 Позволяет задать номер порта, используемый для соединения с FTP-сервером. Значение по умолчанию этого свойства равно **21**.  
  
 **Имя пользователя**  
 Позволяет задать имя пользователя для доступа к FTP-серверу. Значение этого свойства по умолчанию равно **anonymous**.  
  
 **Пароль**  
 Позволяет задать пароль для доступа к серверу FTP.  
  
 **Время ожидания (сек)**  
 Позволяет указать число секунд, в течение которых задача будет ожидать подключения. Значение **0** указывает на бесконечное время ожидания. Значение по умолчанию этого свойства равно **60**.  
  
 **Использовать пассивный режим**  
 Позволяет указать сторону, инициирующую соединение, — сервер или клиент. В активном режиме соединение инициируется сервером, а в пассивном режиме — клиентом. По умолчанию, установлен **активный режим**.  
  
 **Число повторов**  
 Позволяет задать число попыток соединения, осуществляемых задачей. Значение **0** указывает на отсутствие ограничений на число попыток.  
  
 **Размер фрагмента данных (КБ)**  
 Позволяет задать размер фрагмента передаваемых данных в килобайтах.  
  
 **Проверка соединения**  
 После настройки диспетчера FTP-соединений следует проверить доступность подключения, нажав кнопку **Проверить соединение**.  
  
## <a name="see-also"></a>См. также:  
 [Задача «FTP»](../../integration-services/control-flow/ftp-task.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Подключения](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  