---
title: "DENY, разрешения схемы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], schemas
- schemas [SQL Server], permissions
- permissions [SQL Server], schemas
- DENY statement, schemas
ms.assetid: 300a67c4-d226-4653-9e9f-7ae4d53fcf33
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7d4d3e3709ff4ad38d8b033afe1569d9c234bfa2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-schema-permissions-transact-sql"></a>DENY, запрет разрешений на схему (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения на схему.  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DENY permission  [ ,...n ] } ON SCHEMA :: schema_name  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *разрешение*  
 Указывает разрешение, которое может быть запрещено на схему. Список разрешений см. в подразделе «Примечания» далее в этом разделе.  
  
 ON SCHEMA **::** схемы*_name*  
 Указывает схему, на которую запрещается разрешение. Квалификатор области **::** является обязательным.  
  
 *database_principal*  
 Задает участника, для которого запрещается разрешение, — *database_principal* может принимать одно из следующих действий:  
  
-   Пользователь базы данных  
-   Роль базы данных  
-   Роль приложения  
-   Пользователь базы данных, сопоставленный имени входа Windows  
-   Пользователь базы данных, сопоставленный группе Windows  
-   Пользователь базы данных, сопоставленный сертификату  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
CASCADE  
 Указывает, что запрещаемое разрешение также запрещается для других участников, которым оно было предоставлено данным участником.  
  
*denying_principal*  
 Задает участника, от которого участник, выполняющий данный запрос, получает право на запрет разрешения. *denying_principal* может принимать одно из следующих действий:  
  
-   Пользователь базы данных  
-   Роль базы данных  
-   Роль приложения  
-   Пользователь базы данных, сопоставленный имени входа Windows  
-   Пользователь базы данных, сопоставленный группе Windows  
-   Пользователь базы данных, сопоставленный сертификату  
-   Пользователь базы данных, сопоставленный асимметричному ключу  
-   Пользователь базы данных, не сопоставленный серверу-участнику  
  
## <a name="remarks"></a>Замечания  
 Схема — это защищаемая сущность уровня базы данных, содержащаяся в базе данных, которая является для нее родительской в иерархии разрешений. Наиболее специфичные и ограниченные разрешения на работу со схемой, которые можно запрещать, приведены в следующей таблице вместе с общими разрешениями, неявно их включающими.  
  
|Разрешение схемы|Содержится в разрешении схемы|Содержится в разрешении базы данных|  
|-----------------------|----------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY SCHEMA|  
|CONTROL|CONTROL|CONTROL|  
|CREATE SEQUENCE|ALTER|ALTER ANY SCHEMA|  
|DELETE|CONTROL|DELETE|  
|Выполните|CONTROL|Выполните|  
|INSERT|CONTROL|INSERT|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|CONTROL|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL для схемы. Если указан параметр AS, указанный участник должен быть владельцем схемы.  
  
## <a name="see-also"></a>См. также:  
 [Создание СХЕМЫ &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [DENY (Transact-SQL)](../../t-sql/statements/deny-transact-sql.md)   
 [Разрешения (компонент Database Engine)](../../relational-databases/security/permissions-database-engine.md)   
 [Участники (компонент Database Engine)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.fn_builtin_permissions (Transact-SQL)](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME (Transact-SQL)](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  
