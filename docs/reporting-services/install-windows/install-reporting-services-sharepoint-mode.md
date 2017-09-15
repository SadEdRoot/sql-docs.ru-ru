---
title: "Установка служб Reporting Services в режиме SharePoint | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 17effa28932798a3cd35427a0a7104d4aa355b56
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="install-reporting-services-sharepoint-mode"></a>Установка режима интеграции с SharePoint для служб Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Отчет SQL Server Reporting Services в SharePoint, позволяет создавать и просматривать в библиотеках документов, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] подписки доставки отчетов по электронной почте [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], предупреждения об изменении данных и функции управления отчета, в развертывание на основе [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint. Дополнительные сведения о функциях в режиме интеграции с SharePoint, см в разделе «Поддержка функций и поведение различия в режимах сервера» [сервера отчетов служб Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md).

> [!NOTE]
> Интеграция служб Reporting Services с SharePoint больше не доступны после SQL Server 2016.

Существует два основных компонента [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которые будут установлены для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  

|Установка|Описание|  
|------------------|-----------------|  
|**Сервер отчетов** . Сервер отчетов служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , установленный в режиме SharePoint|Сервер отчетов обеспечивает обработку и подготовку данных и отчетов, а также обработку подписок и предупреждений об изменении данных. Сервер отчетов в режиме SharePoint предназначен для установки как общая служба SharePoint.<br /><br /> **Как установить** : используйте установочный носитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**Надстройка** . Сервер отчетов служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint ( **rsSharePoint.msi**).|Эта надстройка устанавливает страницы пользовательского интерфейса и компоненты служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на сервер клиентского веб-интерфейса SharePoint. В компоненты пользовательского интерфейса входят [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], страницы в центре администрирования SharePoint, страницы компонентов, используемые в библиотеках документов SharePoint, и страницы предупреждений об изменении данных служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> **Как установить**  : скачайте надстройку из Интернета или используйте установочный носитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
  
## <a name="in-this-section"></a>В этом разделе  
 [Поддерживаемые сочетания SharePoint, компонентов служб Reporting Services и надстроек (SQL Server 2016)](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Где найти надстройку службы Reporting Services для продуктов SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Установка первого сервера отчетов в режиме интеграции с SharePoint](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [Установка и удаление надстройки служб Reporting Services для SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Добавление дополнительного сервера отчетов в ферму (горизонтально масштабируемые службы SSRS)](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Добавление дополнительного клиентского веб-интерфейса служб Reporting Services в ферме](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Настройка электронной почты для приложения служб Reporting Services (SharePoint 2013 и SharePoint 2016)](http://msdn.microsoft.com/en-us/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [Подготовка подписок и предупреждений для приложений служб SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Служба Claims to Windows Token Service (c2WTS) и службы Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  

## <a name="next-steps"></a>Следующие шаги

 [Архитектура предупреждений об изменении данных и рабочий процесс](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [Диспетчер предупреждений данных для оповещения администраторов](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  

Дополнительные вопросы? [Попробуйте задать вопрос на форуме служб Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)