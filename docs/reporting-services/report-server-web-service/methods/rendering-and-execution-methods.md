---
title: Методы отрисовки и выполнения | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1d4da662ed770c6b104e53e9397321a56d4b065b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="rendering-and-execution-methods"></a>Методы подготовки к просмотру и выполнения
  Эти методы можно использовать для управления выполнением и кэшированием элементов и подготовкой отчетов к просмотру.  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|Делает недействительным кэш для элемента.|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|Возвращает конфигурацию кэширования для элемента и параметры, которые описывают, когда истекает срок действия кэшированной копии элемента.|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|Возвращает параметр выполнения и соответствующие настройки для отдельного элемента.|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|Возвращает список поддерживаемых настроек выполнения.|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|Обрабатывает указанный отчет и готовит его к просмотру в заданном формате.|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|Настраивает элемент для кэширования и предоставляет настройки, указывающие, когда истекает срок действия кэшированной копии элемента.|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|Устанавливает параметры выполнения и соответствующие свойства выполнения для указанного элемента.|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|Создает моментальный снимок состояния выполнения элемента для указанного элемента.|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Методы веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
