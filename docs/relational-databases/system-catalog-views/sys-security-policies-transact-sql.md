---
title: sys.security_policies (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dae89c39aa55f8139ce76942f0bdda660b645241
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "33221135"
---
# <a name="syssecuritypolicies-transact-sql"></a>sys.security_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждой политики безопасности в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Уникальное имя политики безопасности в базе данных.|  
|object_id|**int**|Идентификатор политики безопасности.|  
|principal_id|**int**|Идентификатор владельца политики безопасности, зарегистрированный в базе данных. Значение NULL, если владелец определяется посредством схемы.|  
|schema_id|**int**|Идентификатор схемы, в которой находится объект.|  
|parent_object_id|**int**|Идентификатор объекта, которому принадлежит данная политика. Должно быть равно 0.|  
|Тип|**vachar(2)**|Должно быть **SP**.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|Дата создания политики безопасности в формате UTC.|  
|modify_date|**datetime**|Дата последнего изменения политики безопасности в формате UTC.|  
|is_ms_shipped|**bit**|Всегда значение false.|  
|is_enabled|**bit**|Состояние спецификации политики безопасности.<br /><br /> 0 = отключен<br /><br /> 1 = включен|  
|is_not_for_replication|**bit**|Политика была создана с параметром NOT FOR REPLICATION.|  
|uses_database_collation|**bit**|Использует те же параметры сортировки, что и база данных.|  
|is_schemabinding_enabled|**bit**|Состояние предложения SCHEMABINDING для политики безопасности:<br /><br /> 0 или NULL = включено<br /><br /> 1 = отключено|  
  
## <a name="permissions"></a>Разрешения  
 Участники **ALTER ANY SECURITY POLICY** разрешение имеют доступ ко всем объектам в этом представлении каталога, а также все, кто имеет **VIEW DEFINITION** в объекте.  
  
## <a name="see-also"></a>См. также  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [sys.security_predicates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
