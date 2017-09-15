---
title: "Отчеты с дополнительной информацией (SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 55d22d2fd64faef6e913bf226c831546d71665ca
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="clickthrough-reports-ssrs"></a>Отчеты с дополнительной информацией (SSRS)
  Отчетом с дополнительной информацией называется отчет, в котором есть подробные сведения о данных, содержащихся в основном отчете. Отчет с дополнительной информацией выводится, когда пользователь щелкает интерактивные данные в основном отчете. Такие отчеты автоматически создаются сервером отчетов. Конструктор моделей определяет, что должно отображаться в отчетах с дополнительной информацией, устанавливая свойства **DefaultDetailAttribute** и **DefaultAggregateAttribute** сущности в модели отчета.  
  
> [!NOTE]  
>  Отчеты с дополнительной информацией доступны не в каждом выпуске [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md). Если используемый выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неизвестен, обратитесь к администратору базы данных.  
  
## <a name="using-default-templates"></a>Использование шаблонов по умолчанию  
 По умолчанию сервер отчетов создает два типа шаблонов для каждой сущности: шаблон одного экземпляра и шаблон нескольких экземпляров. Тип шаблона определяется выбранным элементом. Если щелчок мышью выполняется на скалярном атрибуте, то используется шаблон одного экземпляра. Если щелчок мышью выполняется на статистическом атрибуте, то используется шаблон нескольких экземпляров.  
  
#### <a name="single-instance-templates"></a>Шаблоны одного экземпляра  
 Шаблон одного экземпляра отображает все атрибуты целевой сущности и все статистические атрибуты по умолчанию, заданные для связанных сущностей, которые имеют связь «один ко многим» с целевой сущностью. Шаблон одного экземпляра имеет вид, показанный на следующем изображении.  
  
 ![Многие 1 отчет с дополнительной информацией. ] (../../reporting-services/reports/media/manytooneclickthrough.gif "Многие 1 отчет с дополнительной информацией.")  
  
#### <a name="multiple-instance-templates"></a>Шаблоны нескольких экземпляров  
 Шаблон нескольких экземпляров отображает только атрибуты детализации целевой сущности по умолчанию и все статистические атрибуты по умолчанию, заданные для связанных сущностей, которые имеют связь «один ко многим» с целевой сущностью. Шаблон нескольких экземпляров имеет вид, показанный на следующем изображении.  
  
 ![Многие 1 отчет с дополнительной информацией. ] (../../reporting-services/reports/media/onetomanyclickthrough.gif "Многие 1 отчет с дополнительной информацией.")  
  
## <a name="customizing-clickthrough-reports"></a>настройка отчетов с дополнительной информацией  
 Вместо того чтобы использовать шаблоны по умолчанию, созданные сервером отчетов, в построителе отчетов можно создать отдельный отчет, который будет использоваться в качестве пользовательского отчета с дополнительной информацией. Затем можно связать отчет с моделью в качестве детализированного отчета в диспетчере отчетов.  
  
 Чтобы превратить отчет построителя отчетов в отчет с дополнительной информацией, нужно установить флажок **Включить детализацию для этого отчета** в диалоговом окне **Свойства** построителя отчетов. При установке данного флажка к этому отчету добавляется параметр детализации, после чего запустить его непосредственно в построителе отчетов не удастся. Параметр детализации автоматически вычисляется сервером отчетов, когда читатель отчета щелкает тот или иной элемент в отчете построителя отчетов.  
  
> [!IMPORTANT]  
>  Первичная (или базовая) сущность, использующаяся в отчете, должна быть той же самой, с которой связывается отчет.  
  
## <a name="see-also"></a>См. также  
 [Связывание отчета с моделью в качестве отчета с дополнительной информацией](http://msdn.microsoft.com/library/3af42de3-67ef-41c2-bc8a-7045baec6f63)  
  
  
