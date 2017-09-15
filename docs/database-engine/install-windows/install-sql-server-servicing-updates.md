---
title: "Установка обновлений для обслуживания SQL Server | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/05/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 46b16dcf147dbd863eec0330e87511b4ced6c4ce
ms.openlocfilehash: 874dc2c5d78484b3aab341b8d515d4e652fe4c30
ms.contentlocale: ru-ru
ms.lasthandoff: 09/05/2017

---
# <a name="install-sql-server-servicing-updates"></a>Установка обновлений для обслуживания SQL Server
В этом разделе описывается установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]. В разделе рассматриваются следующие вопросы.  
  
- Установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] при установке нового экземпляра  
  
- Установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] после установки экземпляра.  
  
Установите последние обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы обеспечить наличие последних обновлений безопасности для систем.  
  
## <a name="installing-updates-for-includenoversionincludesssnoversion-mdmd-during-a-new-installation"></a>Установка обновлений для [!INCLUDE[noVersion](../../includes/ssNoVersion-md.md)] при установке нового экземпляра  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет последние обновления продукта с установкой основного продукта, чтобы он и применимые обновления устанавливались одновременно. Функция обновления продукта может искать подходящие обновления в следующих источниках.  
  
- [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
- Службы Windows Server Update Services (WSUS)  
  
- Локальная папка  
  
- Сетевая папка  
  
Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое.  
  
## <a name="installing-updates-for-includessnoversionincludesssnoversion-mdmd-after-it-has-already-been-installed"></a>Установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] после установки экземпляра  
В установленном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]рекомендуется установить последние обновления безопасности и критические обновления, в том числе выпуски для общего распространения (GDR), пакеты обновления (SP) и накопительные пакеты обновления (CU). Дополнительные сведения см. в [объявлении о добавочной модели обслуживания SQL Server за март 2016 года](http://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-updates-to-the-sql-server-incremental-servicing-model-ism/). 
  
Обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны через центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MU), службу обновления Windows (WSUS) и Центр загрузки Майкрософт. Обновления безопасности и критические обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны в центре обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Чтобы увидеть эти обновления, необходимо дать согласие на использование MU в приложении центра обновления Windows на панели управления.  
  
После получения обновления через центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] все компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляются до последней версии в автоматическом режиме. Если необходима дополнительная гибкость в процессе установки или отсутствует доступ к Интернету или службам WSUS, то нужно получить обновления из центра загрузки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также:  
[Установка SQL Server с помощью мастера установки &#40;программы установки&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)   
[Добавление компонентов в экземпляр SQL Server (программа установки)](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)   
[Исправление неудавшейся установки SQL Server](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  

