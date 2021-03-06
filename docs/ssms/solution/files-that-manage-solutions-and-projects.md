---
title: Файлы для управления решениями и проектами | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24d05859d16542935a86d58871a9d226d0474ed6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="files-that-manage-solutions-and-projects"></a>Файлы для управления решениями и проектами
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 В этом разделе описываются типы файлов, характерные для среды [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. По умолчанию все решения и их проекты создаются в папке \My Documents\SQL Server Management Studio Projects.  


## <a name="management-studio-solution-files"></a>Файлы решений среды Management Studio  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] использует типы файлов, отличные от тех, что используются в среде [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] или [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio. Это означает, что открыть решение среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] или Visual Studio нельзя. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] файлы решений позволяют обозревателю решений открывать графический интерфейс для управления файлами.  
   
|Расширение|Тип файла|Description|Создан|  
|-------------|-------------|---------------|--------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] Объект решения|Предоставляет среду со ссылками на расположение проектов, элементов проекта и решения [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на диске.|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]|  
  
## <a name="management-studio-project-files"></a>Файлы проектов среды Management Studio  
Точно так же, как решения содержат файлы решений, управляющие объектами в решении, проекты содержат файлы проектов. Тип файла проекта, который среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] создает для проекта, зависит от шаблона, который использовался для создания этого проекта. В следующей таблице приводятся типы файлов, создаваемых для каждого проекта.  
   
|Расширение|Шаблон проекта|  
|-------------|--------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Проект скриптов|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Проект скриптов|  
   
## <a name="location-of-solution-level-files"></a>Расположение файлов уровня решения  
По умолчанию файлы уровня решения создаются в физическом каталоге первого проекта, созданного в этом решении. Каталог для решения можно определить, создав решение или указав каталог при создании нового проекта.  
 
Если структура каталогов схожа с логической структурой, отображаемой в обозревателе решений, облегчается поиск файлов проектов и решений, а также предоставление доступа к ним для других разработчиков в команде.  
   
## <a name="see-also"></a>См. также:  
[Управление файлами с помощью кодировок](../../ssms/solution/manage-files-with-encoding.md)  
[Прочие файлы](../../ssms/solution/miscellaneous-files.md)  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Решения (среда SQL Server Management Studio)](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Проекты (SQL Server Management Studio)](../../ssms/solution/projects-sql-server-management-studio.md)  
[Обозреватель решений системы управления версиями](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  
