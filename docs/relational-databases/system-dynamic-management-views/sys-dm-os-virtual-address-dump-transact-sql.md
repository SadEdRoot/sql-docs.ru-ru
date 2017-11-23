---
title: "sys.dm_os_virtual_address_dump (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_virtual_address_dump
- sys.dm_os_virtual_address_dump_TSQL
- sys.dm_os_virtual_address_dump
- dm_os_virtual_address_dump_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_virtual_address_dump dynamic management view
ms.assetid: 7b24ea55-3873-42fd-a86c-441c92eb6175
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7088f19776027b7e71d2a0519797c655d7632110
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosvirtualaddressdump-transact-sql"></a>sys.dm_os_virtual_address_dump (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о диапазоне страниц в виртуальном адресном пространстве вызывающего процесса.  
  
> [!NOTE]  
>  Эти сведения можно получить через **VirtualQuery** Windows API.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_os_virtual_address_dump**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**region_base_address**|**varbinary(8)**|Указатель на базовый адрес области страниц. Не допускает значение NULL.|  
|**region_allocation_base_address**|**varbinary(8)**|Указатель на базовый адрес диапазона страниц, выделенных с помощью функции Windows API VirtualAlloc. Страница, на которую указывает элемент BaseAddress, содержится внутри этого выделенного диапазона. Не допускает значение NULL.|  
|**region_allocation_protection**|**varbinary(8)**|Атрибуты защиты при первом выделении области. Значение может быть одним из следующих:<br /><br /> -PAGE_READONLY<br />-PAGE_READWRITE<br />-PAGE_NOACCESS<br />-PAGE_WRITECOPY<br />-PAGE_EXECUTE<br />-PAGE_EXECUTE_READ<br />-PAGE_EXECUTE_READWRITE<br />-PAGE_EXECUTE_WRITECOPY<br />-PAGE_GUARD<br />-PAGE_NOCACHE<br /><br /> Не допускает значение NULL.|  
|**region_size_in_bytes**|**bigint**|Размер области в байтах, начиная с базового адреса, в которой все страницы имеют одинаковые атрибуты. Не допускает значение NULL.|  
|**region_state**|**varbinary(8)**|Текущее состояние области. Возможны следующие варианты.<br /><br /> -MEM_COMMIT<br />-MEM_RESERVE<br />-MEM_FREE<br /><br /> Не допускает значение NULL.|  
|**region_current_protection**|**varbinary(8)**|Атрибуты защиты. Значение может быть одним из следующих:<br /><br /> -PAGE_READONLY<br />-PAGE_READWRITE<br />-PAGE_NOACCESS<br />-PAGE_WRITECOPY<br />-PAGE_EXECUTE<br />-PAGE_EXECUTE_READ<br />-PAGE_EXECUTE_READWRITE<br />-PAGE_EXECUTE_WRITECOPY<br />-PAGE_GUARD<br />-PAGE_NOCACHE<br /><br /> Не допускает значение NULL.|  
|**region_type**|**varbinary(8)**|Определяет типы страниц в области. Значение может быть одним из следующих:<br /><br /> -MEM_PRIVATE<br />-MEM_MAPPED<br />-MEM_IMAGE<br /><br /> Не допускает значение NULL.|  
|**pdw_node_id**|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
## <a name="permissions"></a>Permissions  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Относящиеся к операционной системе SQL Server динамические административные представления &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  

