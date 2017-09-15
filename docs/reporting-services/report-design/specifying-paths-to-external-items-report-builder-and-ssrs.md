---
title: "Указание путей к внешним элементам (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3ba2c751b7f851fa9be24ca08cb4ab95f4314258
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a>Указание путей к внешним элементам (построитель отчетов и службы SSRS)
  В свойствах элемента отчета укажите пути к нужным элементам, таким как детализированные отчеты, вложенные отчеты и файлы изображений, которые являются внешними для файла определения отчета и размещены на сервере отчетов.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  В построителе отчетов пути к элементам должны указывать на элементы на сервере отчетов. Пути к элементам в файловой системе не поддерживаются. Осуществить предварительный просмотр отчета, который использует эти элементы, можно только в случае, если установлено соединение с сервером отчетов, на котором располагаются эти элементы.  
  
 При указании пути к внешнему элементу в диалоговом окне действий, вложенных отчетов или изображений, можно непосредственно перейти к серверу отчетов и выбрать элемент. Указывать детализированный отчет или вложенный отчет рекомендуется путем перехода к элементу и выбора его напрямую. При этом правильные имена параметров будут доступны в раскрывающемся списке при указании параметров отчета или вложенного отчета. При замене пути к элементу на путь, указывающий на другой элемент, следует вручную обновить правильные имена параметров и переменные, если это необходимо.  
  
 На сервере отчетов, работающем в собственном режиме, укажите имя детализированного отчета без расширения файла RDL.  
  
 На сервере отчетов, работающем в режиме интеграции с SharePoint, необходимо включить расширение файла RDL. Путь может быть одним из следующих:  
  
-   **Относительный путь к элементу из основного отчета.** Например, ../AllSubreports/Subreport1. В этом примере **..** указывает на родительскую папку для папки, в которой расположен основной отчет.  
  
    > [!NOTE]  
    >  Относительные пути не поддерживаются, если отчет запускается в построителе отчетов. Для просмотра отчета, использующего относительные пути к внешним элементам, необходимо сохранить отчет на сервере отчетов и запустить отчет оттуда.  
  
-   **Полный путь к элементу.**  
  
    -   **На сервере отчетов** путь начинается с **/**(корневой папки). например /Reports/AllSubreports/Subreport1.  
  
    -   **На сайте SharePoint** необходимо указать в выражении имя отчета с полным URL-адресом элемента и расширением файла RDL. Например, `="http://server/site/library/folder/Report1.rdl"`.  
  
## <a name="see-also"></a>См. также  
 [Добавление внешнего изображения &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-an-external-image-report-builder-and-ssrs.md)   
 [Добавить вложенный отчет и параметры &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [Добавление действия детализации в отчет &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  