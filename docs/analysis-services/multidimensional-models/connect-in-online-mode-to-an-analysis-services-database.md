---
title: "Подключение в режиме в сети для базы данных служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 626d0643a170f96850c6c274d64694e86e4663a3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Подключение в режиме «в сети» к базе данных служб Analysis Services
  Можно напрямую подключиться к существующей базе данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и изменить объекты непосредственно в этой базе данных. При прямом подсоединении к базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] изменения объектов происходят моментально и проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не создается в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a>Прямое соединение с базой данных служб Analysis Services с помощью SQL Server Data Tools  
  
1.  Откройте среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** укажите пункт **Открыть** и выберите пункт **База данных служб Analysis Services**.  
  
3.  Выберите **Соединиться с существующей базой данных**.  
  
4.  Укажите имя сервера и имя базы данных.  
  
     Можно либо ввести имя базы данных, либо запросить отображение существующих на сервере баз данных.  
  
5.  Нажмите кнопку **ОК**.  
  
     Теперь можно редактировать любой объект непосредственно в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Работа с проектами и базами данных служб Analysis Services на этапе разработки](../../analysis-services/multidimensional-models/work-with-analysis-services-projects-and-databases-in-development.md)   
 [Создание многомерных моделей с помощью SQL Server Data Tools &#40; SSDT &#41;](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  