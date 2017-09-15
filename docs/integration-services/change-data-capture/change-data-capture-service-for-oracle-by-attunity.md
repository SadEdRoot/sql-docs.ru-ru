---
title: "Служба Service для Oracle от Attunity для отслеживания измененных данных | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4b11270e4535868da764601fcce1a2d3c12e077d
ms.openlocfilehash: 1f1ce0a4f9e616f38f4b99ad220a7c7e8ba6a2fc
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a>Служба системы отслеживания измененных данных для Oracle компании Attunity
  Служба CDC Service для Oracle ― это служба Windows, которая просматривает журналы транзакций Oracle и регистрирует изменения выбранных таблиц Oracle в таблицах изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Таблицы изменений SQL, где хранятся отслеженные изменения из базы данных Oracle, принадлежат к тому же типу, что и таблицы изменений, используемые в собственной системе отслеживания изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поэтому использовать эти изменения так же легко, как и изменения баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="installation"></a>Установка  
 Конструктор и служба системы отслеживания измененных данных Microsoft® для Oracle от Attunity для Microsoft SQL Server® 2016 находятся в составе пакета дополнительных компонентов SQL Server 2016. Скачать компоненты пакета дополнительных компонентов можно со страницы [Microsoft® SQL Server® 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=746297)(Пакет дополнительных компонентов Microsoft® SQL Server® 2016).  
  
 Службу CDC Service для Oracle можно установить на любой поддерживаемый компьютер с ОС Windows с доступом к исходным базам данных Oracle, изменения в которых отслеживаются, и к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где находится целевая база данных CDC. Службе CDC Service не нужны локально установленные базы данных Oracle или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а только их поддерживаемые клиенты. Сведения о месте установки необходимых компонентов базы данных см. в подразделе **Предварительные требования базы данных** в этом разделе.  
  
 Установка службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service для Oracle помещает в выбранном месте графический интерфейс пользователя для настройки службы и служебную программу. Служба CDC Service для Oracle настраивается отдельно с помощью консоли конфигурации службы Oracle CDC. Дополнительные сведения о настройке службы Oracle CDC Service см. в разделе [Change Data Capture Service for Oracle by Attunity F1 Help](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 Службу CDC Service для Oracle можно установить на любой поддерживаемый компьютер с ОС Windows, на котором установлен собственный клиент Native Client [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ; он не обязательно должен быть установлен на том же компьютере, что и целевая база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="supported-windows-environments"></a>Поддерживаемые среды Windows  
 Служба системы отслеживания измененных данных для Oracle от Attunity может работать в следующих средах Windows:  
  
-   Windows 8 и 8.1  
-   Windows 10  
-   Windows Server 2012 и 2012 R2
-   Windows Server 2016
  
## <a name="database-prerequisites"></a>Предварительные требования базы данных  
 Для работы со службой CDC Service для Oracle следует установить программное обеспечения собственного клиента Native Client Oracle [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service. Кроме того, необходимо установить клиент ODBC для SQL Server, используя процесс установки SQL Server.  
  
 Служба CDC для Oracle поддерживает следующие версии:  
  
### <a name="source-oracle-database"></a>Исходная база данных Oracle  
  
-   Версии 10g базы данных Oracle 2
-   База данных Oracle 11g выпуске 1 и версии 2
-   База данных Oracle 12c в классической установке. (Многоклиентская установка не поддерживается.)  
  
### <a name="target-sql-server-database"></a>Целевая база данных SQL Server  
 Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="running-the-installation-program"></a>Запуск программы установки  
 Чтобы установить службу CDC Service для Oracle, откройте мастер установки для используемой платформы Windows (32-/64-разрядной) и следуйте инструкциям на экране.  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a>Удаление службы системы отслеживания измененных данных для Oracle от Attunity  
 Служба CDC Service для Oracle удаляется с помощью пункта панели управления «Программы и компоненты».  
  
 При удалении службы CDC Service созданные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удаляются. Для полного удаления этого средства нужно удалить базу данных MSXDBCDC и конкретные базы данных CDC, созданные в целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым производилась работа.  
  
 Если программное обеспечение службы CDC Service удаляется с одного компьютера и устанавливается на другой, нужно задать только следующие данные:  
  
-   Учетная запись службы  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и учетные данные  
  
-   Главный пароль  
  
 Все прочие определения хранятся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и доступны из предыдущей установки на другом компьютере.  
  
## <a name="in-this-documentation"></a>В этой документации  
  
-   [Архитектура службы системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Служба CDC Oracle](../../integration-services/change-data-capture/the-oracle-cdc-service.md)  
  
-   [Change Data Capture Service for Oracle by Attunity F1 Help](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Руководство по службе системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Работа со службой CDC Oracle](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md)  
  
  
