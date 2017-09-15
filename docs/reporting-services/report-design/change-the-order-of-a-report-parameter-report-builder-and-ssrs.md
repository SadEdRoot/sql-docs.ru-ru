---
title: "Изменение порядка параметров отчета (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3377e943ddf7d8c7bd06aeab52ee263a754af25c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Изменение порядка параметров отчета (построитель отчетов и службы SSRS)
  Изменять порядок параметров отчета необходимо в случае, если зависимый параметр расположен перед параметром, от которого он зависит. Порядок параметров имеет значение при наличии каскадных параметров или в случае, если необходимо показать пользователям значение по умолчанию одного параметра перед тем, как они выберут значения для других параметров. Зависимый параметр отчета ссылается (в своем запросе значений по умолчанию или в запросе допустимых значений) на параметр запроса, указывающий на параметр отчета, расположенный после него в списке параметров в области **Данные отчета** .  
  
 Порядок, в котором параметры отображаются на панели инструментов средства просмотра отчетов при запуске отчета, определяется порядком параметров в области **Данные отчета** и расположением параметров на панели пользовательских параметров. Дополнительные сведения см. в разделе [Настройка области параметров в отчет &#40; Построитель отчетов &#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-change-the-order-of-report-parameters"></a>Изменение порядка параметров отчета  
  
Изменить порядок параметров отчета можно одним из следующих способов:  
  
-   Щелкните параметр в области **Данные отчета** и переместите его выше или ниже в списке, используя кнопки со стрелками вниз и вверх, как показано на изображении ниже.  При изменении порядка параметров в области **Данные отчета** также меняется расположение параметра на панели.  
  
     ![Изменение порядка параметров в области данных отчета](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "изменить порядок параметров в области данных отчета")  
  
-   На панели параметров перетащите параметр в новый столбец или строку. При изменении расположения параметра на панели также изменяется порядок параметров в области **Данные отчета** . Дополнительные сведения о переносе параметров в области см. в разделе [Настройка области параметров в отчет &#40; Построитель отчетов &#41; ](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета &#40; Построитель отчетов и конструктор отчетов &#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Справка построителя отчетов по диалоговым окнам, панелей и мастеров](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Добавление каскадных параметров отчета &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Учебник: Добавление параметра к отчету &#40; Построитель отчетов &#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Добавление фильтров набора данных, фильтров области данных и фильтры групп &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Ссылки на коллекцию параметров &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md)  
  
  