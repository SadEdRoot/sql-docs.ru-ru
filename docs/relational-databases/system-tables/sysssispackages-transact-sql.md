---
title: sysssispackages (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
caps.latest.revision: 43
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dfad4f28a2349ad6f3c5212ae26841a77b78e39b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого пакета, который будет сохранен [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта таблица хранится в **msdb** базы данных.  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Уникальный идентификатор пакета.|  
|**идентификатор**|**uniqueidentifier**|Идентификатор GUID пакета.|  
|**Описание**|**nvarchar**|Необязательное описание пакета.|  
|**CREATEDATE**|**datetime**|Дата создания пакета.|  
|**FolderId**|**uniqueidentifier**|Идентификатор GUID логической папки, в которой среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит данный пакет.|  
|**ownersid**|**varbinary**|Уникальный идентификатор защиты пользователя, создавшего пакет.|  
|**packagedata**|**image**|Пакет.|  
|**номера**|**int**|Формат, в котором пакет сохранен:<br /><br /> Значение 2 указывает, что пакет сохранен в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] формат.<br /><br /> Значение 3 указывает, что пакет сохраняется в формате [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]или более поздней версии.|  
|**Тип корпуса**|**int**|Клиент, создавший пакет. Возможны следующие значения:<br /><br /> 0 (значение по умолчанию);<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] репликации)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] конструктора)<br /><br /> 6 (конструктор или мастер планов обслуживания базы данных).<br /><br /> <br /><br /> Обратите внимание, что значения в этом столбце соответствуют <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> перечисления.|  
|**vermajor**|**int**|Последняя основная версия пакета.|  
|**verminor**|**int**|Последняя вспомогательная версия пакета.|  
|**verbuild**|**int**|Последняя сборка пакета.|  
|**vercomments**|**nvarchar**|Примечания о версии пакета.|  
|**verid**|**uniqueidentifier**|Идентификатор GUID версии пакета.|  
|**isencrypted**|**бит**|Логическое значение, показывающее, зашифрован ли пакет.|  
|**readrolesid**|**varbinary**|Роль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая может загрузить пакет.|  
|**writerolesid**|**varbinary**|Роль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая может сохранить пакет.|  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services & #40; Службы SSIS & #41; Пакеты](../../integration-services/integration-services-ssis-packages.md)  
  
  
