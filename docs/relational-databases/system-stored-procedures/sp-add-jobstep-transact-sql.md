---
title: sp_add_jobstep (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_jobstep_TSQL
- sp_add_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobstep
ms.assetid: 97900032-523d-49d6-9865-2734fba1c755
caps.latest.revision: 80
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fc7970a2d38786a49beed08e63068be1abab4d51
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spaddjobstep-transact-sql"></a>sp_add_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Добавляет этап (операцию) к заданию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_add_jobstep [ @job_id = ] job_id | [ @job_name = ] 'job_name'   
     [ , [ @step_id = ] step_id ]   
     { , [ @step_name = ] 'step_name' }   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @command = ] 'command' ]   
     [ , [ @additional_parameters = ] 'parameters' ]   
          [ , [ @cmdexec_success_code = ] code ]   
     [ , [ @on_success_action = ] success_action ]   
          [ , [ @on_success_step_id = ] success_step_id ]   
          [ , [ @on_fail_action = ] fail_action ]   
          [ , [ @on_fail_step_id = ] fail_step_id ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @database_user_name = ] 'user' ]   
     [ , [ @retry_attempts = ] retry_attempts ]   
     [ , [ @retry_interval = ] retry_interval ]   
     [ , [ @os_run_priority = ] run_priority ]   
     [ , [ @output_file_name = ] 'file_name' ]   
     [ , [ @flags = ] flags ]   
     [ , { [ @proxy_id = ] proxy_id   
         | [ @proxy_name = ] 'proxy_name' } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@job_id =** ] *job_id*  
 Идентификационный номер задания, к которому добавляется этап. *Аргумент job_id* — **uniqueidentifier**, значение по умолчанию NULL.  
  
 [  **@job_name =** ] **"***job_name***"**  
 Имя задания, к которому добавляется этап. *job_name* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  Либо *job_id* или *job_name* должен быть указан, но не оба аргумента одновременно.  
  
 [  **@step_id =** ] *step_id*  
 Порядковый идентификационный номер для шага задания. Идентификационные номера этапа начинаются на **1** и увеличиваются без разрывов. Если этап вставляется в существующую последовательность, порядковые номера меняются автоматически. Значение указывается в том случае, если *step_id* не указан. *step_id*— **int**, значение по умолчанию NULL.  
  
 [  **@step_name =** ] **"***step_name***"**  
 Имя шага этапа. *step_name*— **sysname**, не имеет значения по умолчанию.  
  
 [  **@subsystem =** ] **"***подсистемы***"**  
 Подсистема, используемая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы агента для выполнения *команда*. *Подсистема* — **nvarchar(40)**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|"**ACTIVESCRIPTING**"|Активный скрипт.<br /><br /> **\*\* Важные \*\*** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|"**CMDEXEC**"|Команда операционной системы или исполняемая программа.|  
|"**РАСПРОСТРАНЕНИЯ**"|Задание агента распространения репликации.|  
|"**МОМЕНТАЛЬНОГО СНИМКА**"|Задание агента моментальных снимков репликации.|  
|"**АГЕНТ ЧТЕНИЯ ЖУРНАЛА**"|Задание агента чтения журнала репликации.|  
|"**СЛИЯНИЯ**"|Задание агента слияния репликации.|  
|"**QueueReader**"|Задание агента чтения очереди репликации.|  
|"**ANALYSISQUERY**"|Запрос служб Analysis Services (многомерное выражение, расширения интеллектуального анализа данных).|  
|"**ANALYSISCOMMAND**"|Команда служб Analysis Services (XML для аналитики).|  
|"**Dts**"|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выполнение пакетов служб|  
|"**PowerShell**"|Скрипт PowerShell|  
|"**TSQL**" (по умолчанию)|инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)]|  
  
 [  **@command=** ] **"***команда***"**  
 Для выполнения команды **SQLServerAgent** через *подсистемы*. *команда* — **nvarchar(max)**, значение по умолчанию NULL. Агент SQL Server выполняет замену токенов, что обеспечивает такую же гибкость, что и переменные при написании программ.  
  
> [!IMPORTANT]  
>  Все токены, используемые в шагах заданий, теперь должны сопровождаться экранирующим макросом, в противном случае они вызовут ошибку. Кроме того, теперь имена токенов нужно заключать в круглые скобки и помещать в начале синтаксиса токена знак доллара (`$`). Например:  
>   
>  `$(ESCAPE_`*имя макроса*`(DATE))`  
  
 Дополнительные сведения о токенах и обновлении шагов заданий для использования нового синтаксиса токенов см. в разделе [использование токенов в шагах заданий](http://msdn.microsoft.com/library/105bbb66-0ade-4b46-b8e4-f849e5fc4d43).  
  
> [!IMPORTANT]  
>  Все пользователи Windows с разрешением на запись в журнал событий Windows могут получить доступ к шагам заданий, которые активированы предупреждениями агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или инструментария WMI. Чтобы избежать этого нарушения безопасности, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] токены агента, которые могут использоваться в заданиях, активированных предупреждениями, по умолчанию отключены. К этим токенам относятся: **A-DBN**, **A-SVR**, **A-ERR**, **A-SEV**, **A-MSG** и **WMI(***свойство***)**. Обратите внимание, что в этом выпуске использование токенов распространяется на все оповещения.  
>   
>  Если необходимо использовать эти токены, убедитесь, что только члены доверенных групп безопасности Windows, таких как группа «Администраторы», обладают разрешением на работу с журналом событий компьютера, на котором находится [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Затем, чтобы включить эти токены, щелкните правой кнопкой мыши элемент **Агент SQL Server** в обозревателе объектов, выберите пункт меню **Свойства**и на странице **Система предупреждений** установите флажок **Заменить токены всех ответов заданий на предупреждения** .  
  
 [  **@additional_parameters=** ] **"***параметры***"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *Параметры* — **ntext**, значение по умолчанию NULL.  
  
 [  **@cmdexec_success_code =** ] *кода*  
 Значение, возвращаемое **CmdExec** командой подсистемы, чтобы указать, что *команда* выполнена успешно. *код*— **int**, значение по умолчанию **0**.  
  
 [  **@on_success_action=** ] *success_action*  
 Операция, выполняемая в случае успешного завершения этапа. *success_action*— **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**1** (по умолчанию)|Завершить с успешным выполнением.|  
|**2**|Завершить с ошибкой.|  
|**3**|Перейти к следующему шагу.|  
|**4**|Перейдите к шагу *on_success_step_id*|  
  
 [  **@on_success_step_id =** ] *success_step_id*  
 Идентификатор шага данного задания, для выполнения, если выполнение этапа завершится успешно и *success_action*— **4**. *success_step_id*— **int**, значение по умолчанию **0**.  
  
 [  **@on_fail_action=** ] *fail_action*  
 Действие, которое необходимо выполнить, если шаг завершился с ошибкой. *fail_action*— **tinyint**, и может принимать одно из следующих значений.  
  
|Значение|Описание (действие)|  
|-----------|----------------------------|  
|**1**|Завершить с успешным выполнением.|  
|**2** (по умолчанию)|Завершить с ошибкой.|  
|**3**|Перейти к следующему шагу.|  
|**4**|Перейдите к шагу *on_fail_step_id*|  
  
 [  **@on_fail_step_id=** ] *fail_step_id*  
 Идентификатор шага данного задания, для выполнения, если шаг завершился с ошибкой и *fail_action*— **4**. *fail_step_id*— **int**, значение по умолчанию **0**.  
  
 [ **@server =**] **'***server***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *сервер*— **nvarchar(30)**, значение по умолчанию NULL.  
  
 [  **@database_name=** ] **"***базы данных***"**  
 Имя базы данных, в которой выполняется шаг [!INCLUDE[tsql](../../includes/tsql-md.md)]. *База данных* — **sysname**, значение по умолчанию NULL, в этом случае **master** используется база данных. Символы, заключенные в квадратные скобки ([ ]), являются недопустимыми. Для шага задания ActiveX *базы данных* имя языка скриптов, который используется в этапе.  
  
 [  **@database_user_name=** ] **"***пользователя***"**  
 Имя учетной записи пользователя, которая используется при выполнении шага [!INCLUDE[tsql](../../includes/tsql-md.md)]. *пользователь* — **sysname**, значение по умолчанию NULL. Когда *пользователя* имеет значение NULL, этап выполняется в контексте пользователя владельца задания на *базы данных*.  Агент SQL Server включит этот параметр только в случае, если владелец задания — член роли SQL Server sysadmin. Если это так, то данный шаг Transact-SQL будет выполнен в контексте данного имени пользователя SQL Server. Если владелец задания не является системным администратором SQL Server, то шаг Transact-SQL всегда будет выполняться в контексте имени входа, которому принадлежит это задание и @database_user_name параметр будет игнорироваться.  
  
 [  **@retry_attempts=** ] *retry_attempts*  
 Число повторных попыток, предпринимаемых при завершении данного шага с ошибкой. *retry_attempts*— **int**, значение по умолчанию **0**, который указывает на отсутствие повторных попыток.  
  
 [  **@retry_interval=** ] *интервал_повтора*  
 Время ожидания в минутах между попытками повтора. *интервал_повтора*— **int**, значение по умолчанию **0**, которое указывает **0**-минутный интервал.  
  
 [  **@os_run_priority =** ] *run_priority*  
 Зарезервировано.  
  
 [  **@output_file_name=** ] **"***имя_файла***"**  
 Имя файла, в котором будут сохранены выходные данные этого шага. *имя_файла*— **nvarchar(200)**, значение по умолчанию NULL. *имя_файла*может включать один или несколько токенов, перечисленных в разделе *команда*. Этот параметр действителен только с командами, запущенными [!INCLUDE[tsql](../../includes/tsql-md.md)], **CmdExec**, **PowerShell**, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], или [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] подсистем.  
  
 [  **@flags=** ] *флаги*  
 Параметр, который управляет поведением. *флаги* — **int**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0** (по умолчанию)|Переписать выходной файл.|  
|**2**|Добавить к выходному файлу.|  
|**4**|Записать вывод шага задания [!INCLUDE[tsql](../../includes/tsql-md.md)] в журнал шагов.|  
|**8**|Записать журнал в таблицу (переписать существующий журнал).|  
|**16**|Записать журнал в таблицу (добавить к существующему журналу).|  
|**32**|Записать все выходные данные в журнал заданий.|  
|**64**|Создать событие Windows для использования в качестве сигнала для прерывания шага задания Cmd.|  
  
 [ **@proxy_id** =] *proxy_id*  
 Идентификационный номер учетной записи-посредника, в качестве которой выполняется шаг задания. *proxy_id* — тип **int**, значение по умолчанию NULL. Если не *proxy_id* указано, не *proxy_name* указано и не *имя_пользователя* указан, шаг задания выполняется как учетная запись службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
 [ **@proxy_name** =] **"***proxy_name***"**  
 Имя учетной записи-посредника, от имени которой выполняется шаг задания. *proxy_name* — тип **sysname**, значение по умолчанию NULL. Если не *proxy_id* указано, не *proxy_name* указано и не *имя_пользователя* указан, шаг задания выполняется как учетная запись службы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 **sp_add_jobstep** должна запускаться из **msdb** базы данных.  
  
 Среда SQL Server Management Studio обеспечивает простой и наглядный способ управления заданиями и рекомендуется для создания инфраструктуры заданий и управления ей.  
  
 Шаг задания необходимо указать учетную запись-посредник, если только создатель шага задания является членом **sysadmin** фиксированной роли безопасности.  
  
 Учетной записи-посредника могут идентифицироваться по *proxy_name* или *proxy_id*.  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию эту хранимую процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** . Другим пользователям должна быть предоставлена одна из следующих предопределенных ролей базы данных агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в базе данных **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Дополнительные сведения о разрешениях этих ролей см. в разделе [Предопределенные роли базы данных агента SQL Server](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
 Создатель шага задания должен иметь доступ к учетной записи-посреднику для шага задания. Члены **sysadmin** предопределенной роли сервера имеют доступ все учетные записи-посредники. Другим пользователям доступ к учетной записи-посреднику должен быть предоставлен явно.  
  
## <a name="examples"></a>Примеры  
 Следующий пример создает шаг задания, который изменяет доступ к базе данных на доступ только для чтения для базы данных Sales. Кроме того, этот пример задает число повторных попыток, которое равно 5, и через каждые 5 минут.  
  
> [!NOTE]  
>  В этом примере предполагается, что задание `Weekly Sales Data Backup` уже существует.  
  
```  
USE msdb;  
GO  
EXEC sp_add_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_name = N'Set database to read only',  
    @subsystem = N'TSQL',  
    @command = N'ALTER DATABASE SALES SET READ_ONLY',   
    @retry_attempts = 5,  
    @retry_interval = 5 ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Просмотр или изменение заданий](http://msdn.microsoft.com/library/57f649b8-190c-4304-abd7-7ca5297deab7)   
 [sp_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_delete_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
