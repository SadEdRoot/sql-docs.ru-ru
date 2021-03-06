---
title: sp_articlecolumn (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_articlecolumn
- sp_articlecolumn_TSQL
helpviewer_keywords:
- sp_articlecolumn
ms.assetid: 8abaa8c1-d99e-4788-970f-c4752246c577
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 407c4470ae7dad6a871736df822cb00a22882122
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sparticlecolumn-transact-sql"></a>sp_articlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется для указания столбцов, включенных в статью, для вертикальной фильтрации данных в опубликованной таблице. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_articlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column' ]  
    [ , [ @operation = ] 'operation' ]  
    [ , [ @refresh_synctran_procs = ] refresh_synctran_procs ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @change_active = ] change_actve ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @internal = ] 'internal' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, которая содержит эту статью. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@article=**] **"***статьи***"**  
 Имя статьи. *статья* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@column=**] **"***столбца***"**  
 Имя столбца, который требуется добавить или удалить. *столбец* — **sysname**, значение по умолчанию NULL. Если значение равно NULL, публикуются все столбцы.  
  
 [  **@operation=**] **"***операции***"**  
 Указывает, следует ли добавлять или удалять столбцы из статьи. *Операция* — **nvarchar(5)**, значение по умолчанию add. **Добавить** отметить столбец для репликации. **Удалить** снять отметку столбца.  
  
 [  **@refresh_synctran_procs=**] *refresh_synctran_procs*  
 Указывает, формируются ли повторно хранимые процедуры, поддерживающие немедленно обновляемую подписку, для согласования с числом реплицируемых столбцов. *refresh_synctran_procs* — **бит**, значение по умолчанию **1**. Если **1**, хранимые процедуры формируются повторно.  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 Указывает, выполняется ли данная хранимая процедура без подключения к распространителю. *ignore_distributor* — **бит**, значение по умолчанию **0**. Если **0**, базы данных должна быть включена для публикации, а кэш статей следует обновить для отображения новых столбцов, реплицируемых данной статьей. Если **1**, позволяет столбцов статьи для удаления для статей, которые находятся в неопубликованной базе данных; следует использовать только в ситуациях восстановления.  
  
 [  **@change_active =** ] *change_active*  
 Разрешает изменение столбцов в публикациях, на которые имеются подписки. *change_active* — **int** значение по умолчанию **0**. Если **0**, столбцы не изменяются. Если **1**, столбцы можно добавить или удалить из активных статей, на которые имеются подписки.  
  
 [  **@force_invalidate_snapshot =** ] *подписки потребуют*  
 Подтверждает, что действие, выполненное этой хранимой процедурой, может сделать недействительным существующий моментальный снимок. *подписки потребуют* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменение статьи не приводит к недействительности моментального снимка. Если хранимая процедура определяет, что изменение требует создания нового моментального снимка, возникает ошибка и изменения не выполняются.  
  
 **1** указывает, что изменения статьи может привести к недействительности моментального снимка и если существующие подписки потребуют нового моментального снимка, дается разрешение существующий моментальный снимок помечается как устаревшего и создание нового моментального снимка.  
  
 [ **@force_reinit_subscription =** ] *этот*  
 Подтверждает, что действие, выполняемое данной хранимой процедурой, может сделать необходимой повторную инициализацию текущих подписок. *Этот* — **бит**, значение по умолчанию **0**.  
  
 **0** указывает, что изменения в статье не вызывают повторной инициализации подписки. Если хранимая процедура определяет, что изменение потребует повторной инициализации подписки, то выдается сообщение об ошибке, и изменения не производится. **1** означает, что изменения в статье приводят существующих подписок для повторной инициализации и дает разрешение произвести повторную инициализацию подписки.  
  
 [  **@publisher=** ] **"***издатель***"**  
 Указывает значение, отличное от[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не должны использоваться с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
 [  **@internal=** ] **"***внутренней***"**  
 Только для внутреннего применения.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_articlecolumn** используется в репликации моментальных снимков и репликации транзакций.  
  
 Только статей без подписки можно фильтровать с помощью **sp_articlecolumn**.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlecolumn-transac_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_articlecolumn**.  
  
## <a name="see-also"></a>См. также  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Определение и изменение фильтра столбцов](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [Фильтрация опубликованных данных](../../relational-databases/replication/publish/filter-published-data.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
