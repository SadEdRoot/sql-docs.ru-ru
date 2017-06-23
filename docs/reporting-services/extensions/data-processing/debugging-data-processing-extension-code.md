---
title: "Отладка кода модуля обработки данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: 40
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 7af6b33039d19029d1595ac08f5d5345cdaa1c58
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="debugging-data-processing-extension-code"></a>Отладка кода модуля обработки данных
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Предоставляет несколько средств отладки, которые помогут вам проанализировать код модуля обработки данных и поиск ошибок в коде. Какое средство будет наилучшим, зависит от того, что нужно выполнить. В этом примере используется [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>Отладка кода модуля обработки данных  
  
1.  Запустите среду [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] и откройте проект модуля обработки данных.  
  
2.  Постройте проект и разверните в конструкторе отчетов сборку модуля обработки данных и сопроводительный PDB-файл. Дополнительные сведения о развертывании см. в разделе [как: развертывание модуля обработки данных в конструкторе отчетов](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md).  
  
3.  Откройте новый проект отчета в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], оставив код модуля обработки данных открытым в отдельном окне среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
4.  Перейдите к окну среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], содержащему проект модуля обработки данных, и установите в коде несколько точек останова.  
  
5.  Обработка данных расширение окна проекта все еще активна, нажмите кнопку **присоединиться к процессу** на **отладки** меню.  
  
     **Присоединиться к процессу** откроется диалоговое окно.  
  
6.  В списке процессов выберите процесс devenv.exe, который соответствует проекту отчета и нажмите кнопку **присоединение**.  
  
7.  Определите источник данных отчета на **данные отчета** вкладку в проекте отчета. Чтобы выполнить запрос к пользовательскому источнику данных, скорее всего, будет использоваться обычный конструктор запросов. Будет запущен отладчик и начнется выполнение кода с учетом заданных точек останова.  
  
8.  Перемещайтесь по шагам кода с помощью клавиши F11. Дополнительные сведения об использовании среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для отладки см. в документации по среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  