---
title: dbo.systargetservergroupmembers (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.systargetservergroupmembers_TSQL
- dbo.systargetservergroupmembers
- systargetservergroupmembers
- systargetservergroupmembers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservergroupmembers system table
ms.assetid: ee1b2ebd-03cb-4b91-a5d2-98d4d38f82ec
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2585f8b21fad9d831acd2bc8b58f1d58a3592218
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="dbosystargetservergroupmembers-transact-sql"></a>dbo.systargetservergroupmembers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Записывает, какие целевые серверы связаны в настоящее время с данной многосерверной группой.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**servergroup_id**|**int**|Идентификатор серверной группы|  
|**server_id**|**int**|Идентификатор сервера|  
  
  
