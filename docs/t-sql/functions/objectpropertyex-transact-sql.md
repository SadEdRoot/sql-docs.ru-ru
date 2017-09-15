---
title: "OBJECTPROPERTYEX (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECTPROPERTYEX
- OBJECTPROPERTYEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying schema-scoped object information
- viewing schema-scoped object information
- OBJECTPROPERTYEX function
- schema-scoped objects [SQL Server]
- objects [SQL Server], schema-scoped
ms.assetid: be36b3e3-3309-4332-bfb5-c7e9cf8dc8bd
caps.latest.revision: 76
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 73e4cbb26ea46753a79b9089acaaab7fe5d50e65
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="objectpropertyex-transact-sql"></a>OBJECTPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает данные об объектах области схемы в текущей базе данных. Список этих объектов см. в разделе [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md). Функция OBJECTPROPERTYEX не может применяться к объектам, недоступным в области, например: триггерам DDL и уведомлениям о событиях.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
OBJECTPROPERTYEX ( id , property )  
```  
  
## <a name="arguments"></a>Аргументы  
 *идентификатор*  
 Выражение, которое представляет идентификатор объекта в текущей базе данных. *Идентификатор* — **int** и предполагается, что объект схемы в текущем контексте базы данных.  
  
 *Свойство*  
 Выражение, содержащее сведения, которые необходимо вернуть для объекта, указываемого идентификатором. Возвращаемый тип — **sql_variant**. В следующей таблице перечислены базовые типы данных для каждого из свойств.  
  
> [!NOTE]  
>  Если не указано иное, значение NULL возвращается, когда *свойство* не является допустимым именем свойства, *идентификатор* не является допустимым Идентификатором объекта, *идентификатор* является неподдерживаемым типом объекта для указанного *свойство*, или вызывающий объект не имеет разрешения на просмотр метаданных объекта.  
  
|Имя свойства|Тип объекта|Описание и возвращаемые значения|  
|-------------------|-----------------|-------------------------------------|  
|BaseType|Любой объект области схемы|Идентифицирует базовый тип объекта. Если указанный объект — SYNONYM, возвращается базовый тип соответствующего объекта.<br /><br /> Не NULL = тип объекта<br /><br /> Базовый тип данных: **char(2)**|  
|CnstIsClustKey|Ограничение|Ограничение PRIMARY KEY с кластеризованным индексом.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsColumn|Ограничение|Ограничение CHECK, DEFAULT или FOREIGN KEY на одиночный столбец.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsDeleteCascade|Ограничение|Ограничение FOREIGN KEY с параметром ON DELETE CASCADE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsDisabled|Ограничение|Отключенное ограничение.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsNonclustKey|Ограничение|Ограничение PRIMARY KEY с некластеризованным индексом:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsNotRepl|Ограничение|Ограничение определено с помощью ключевых слов NOT FOR REPLICATION.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsNotTrusted|Ограничение|Ограничение было включено без проверки существующих строк, то есть ограничение может выполняться не для всех строк.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|CnstIsUpdateCascade|Ограничение|Ограничение FOREIGN KEY с параметром ON UPDATE CASCADE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsAfterTrigger|Триггер|Триггер AFTER.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsAnsiNullsOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Значение параметра ANSI_NULLS на момент создания:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsDeleteTrigger|Триггер|Триггер DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsFirstDeleteTrigger|Триггер|Первый триггер, срабатывающий при выполнении инструкции DELETE для таблицы:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsFirstInsertTrigger|Триггер|Первый триггер, срабатывающий при выполнении инструкции INSERT для таблицы:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsFirstUpdateTrigger|Триггер|Первый триггер, срабатывающий при выполнении инструкции UPDATE для таблицы:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsInsertTrigger|Триггер|Триггер INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsInsteadOfTrigger|Триггер|Триггер INSTEAD OF.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsLastDeleteTrigger|Триггер|Последний триггер, сработавший при выполнении инструкции DELETE для таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsLastInsertTrigger|Триггер|Последний триггер, сработавший при выполнении инструкции INSERT для таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsLastUpdateTrigger|Триггер|Последний триггер, сработавший при выполнении инструкции UPDATE для таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsQuotedIdentOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Значение параметра QUOTED_IDENTIFIER на момент создания.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsStartup|Процедура|Процедура запуска.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsTriggerDisabled|Триггер|Триггер отключен.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsTriggerNotForRepl|Триггер|Триггер определен как NOT FOR REPLICATION.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsUpdateTrigger|Триггер|Триггер UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|ExecIsWithNativeCompilation|Процедура [!INCLUDE[tsql](../../includes/tsql-md.md)]|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Процедура компилируется в собственном коде.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|HasAfterTrigger|Таблица, представление|Таблица или представление с триггером AFTER.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|HasDeleteTrigger|Таблица, представление|Таблица или представление с триггером DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|HasInsertTrigger|Таблица, представление|Таблица или представление с триггером INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|HasInsteadOfTrigger|Таблица, представление|Таблица или представление с триггером INSTEAD OF.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|HasUpdateTrigger|Таблица, представление|Таблица или представление с триггером UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsAnsiNullsOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], таблица, триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Указывает, что значение параметра ANSI NULLS для таблицы равно ON, что означает, что все сравнения со значением NULL имеют результат UNKNOWN. Эта настройка относится ко всем выражениям в определении таблицы, включая вычисляемые столбцы и ограничения, в течение всего времени существования таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsCheckCnst|Любой объект области схемы|Ограничение CHECK.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsConstraint|Любой объект области схемы|Ограничение:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsDefault|Любой объект области схемы|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Привязанное значение по умолчанию:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsDefaultCnst|Любой объект области схемы|Ограничение DEFAULT:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsDeterministic|Скалярная функция или функция с табличным значением, представление|Свойство детерминизма функции или представления.<br /><br /> 1 = детерминированная<br /><br /> 0 = недетерминированная<br /><br /> Базовый тип данных: **int**|  
|IsEncrypted|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], таблица, триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Указывает, что исходный текст инструкции модуля был преобразован в запутанный формат. Результат запутывания не виден непосредственно ни в одном представлении каталога [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Пользователи, не имеющие доступа к системным таблицам или файлам баз данных, не могут получить текст, подвергнутый запутыванию. Однако этот текст будет доступен пользователям, которые либо смогут обращаться к системным таблицам через [порт выделенного административного Соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md) или непосредственный доступ к файлам базы данных. Кроме того, пользователь, имеющий возможность подключить отладчик к серверному процессу, сможет получить исходный текст процедуры из памяти во время выполнения.<br /><br /> 1 = зашифрована<br /><br /> 0 = не зашифрована<br /><br /> Базовый тип данных: **int**|  
|IsExecuted|Любой объект области схемы|Указывает, может ли объект быть выполнен (представление, процедура, функция или триггер):<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsExtendedProc|Любой объект области схемы|Расширенная процедура.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsForeignKey|Любой объект области схемы|Ограничение FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsIndexed|Таблица, представление|Таблица или представление с индексом:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsIndexable|Таблица, представление|Таблица или представление, для которого может быть создан индекс:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsInlineFunction|Функция|Встроенная функция.<br /><br /> 1 = встроенная функция<br /><br /> 0 = невстроенная функция<br /><br /> Базовый тип данных: **int**|  
|IsMSShipped|Любой объект области схемы|Объект создан во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsPrecise|Вычисляемый столбец, функция, определяемый пользователем тип, представление|Указывает, содержит ли объект вычисления с потерей точности (например: операции с плавающей запятой):<br /><br /> 1 = точные вычисления;<br /><br /> 0 = вычисления с потерей точности.<br /><br /> Базовый тип данных: **int**|  
|IsPrimaryKey|Любой объект области схемы|Ограничение PRIMARY KEY.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsProcedure|Любой объект области схемы|Процедура.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsQuotedIdentOn|Ограничение CHECK, определение DEFAULT, функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], таблица, триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Указывает, что параметр «идентификатор в кавычках» для объекта имеет значение ON; это означает, что во всех выражениях, присутствующих в определении объекта, идентификаторы заключаются в кавычки.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsQueue|Любой объект области схемы|Очередь компонента Service Broker<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsReplProc|Любой объект области схемы|Процедура репликации.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsRule|Любой объект области схемы|Привязанное правило.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsScalarFunction|Функция|Скалярная функция.<br /><br /> 1 = скалярная функция<br /><br /> 0 = нескалярная функция<br /><br /> Базовый тип данных: **int**|  
|IsSchemaBound|Процедура, функция, представление|Привязанная к схеме функция или представление, созданные с помощью SCHEMABINDING.<br /><br /> 1 = привязана к схеме<br /><br /> 0 = Не привязан к схеме.<br /><br /> Базовый тип данных: **int**|  
|IsSystemTable|Таблица|Системная таблица.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsSystemVerified|Вычисляемый столбец, функция, определяемый пользователем тип, представление|Свойства точности и детерминизма объекта могут быть проверены [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsTable|Таблица|Таблица.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsTableFunction|Функция|Функция с табличным значением.<br /><br /> 1 = функция с табличным значением<br /><br /> 0 = функция не с табличным значением<br /><br /> Базовый тип данных: **int**|  
|IsTrigger|Любой объект области схемы|Триггер.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsUniqueCnst|Любой объект области схемы|Ограничение UNIQUE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsUserTable|Таблица|Пользовательская таблица.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|IsView|Просмотр|Представление.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|OwnerId|Любой объект области схемы|Владелец объекта.<br /><br /> **Примечание:** владелец схемы не обязательно является владельцем объекта. Например, дочерние объекты (такие, у которых *parent_object_id* является не нулевым) всегда будет возвращать тот же идентификатор владельца, что и родительский объект.<br /><br /> Не NULL = идентификатор пользователя базы данных — владельца объекта.<br /><br /> NULL = недопустимый идентификатор объекта или тип объекта не поддерживается.<br /><br /> Базовый тип данных: **int**|  
|SchemaId|Любой объект области схемы|Идентификатор схемы, связанной с объектом.<br /><br /> Не NULL = идентификатор схемы объекта.<br /><br /> Базовый тип данных: **int**|  
|SystemDataAccess|Функция, представление|Объект производит доступ к системным данным, системным каталогам или виртуальным системным таблицам в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = нет<br /><br /> 1 = чтение<br /><br /> Базовый тип данных: **int**|  
|TableDeleteTrigger|Таблица|У таблицы есть триггер DELETE.<br /><br /> > 1 = идентификатор первого триггера указанного типа.<br /><br /> Базовый тип данных: **int**|  
|TableDeleteTriggerCount|Таблица|В таблице существует указанное число триггеров типа DELETE.<br /><br /> Не NULL = Число триггеров DELETE.<br /><br /> Базовый тип данных: **int**|  
|TableFullTextMergeStatus|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Определяет, участвует ли в настоящий момент полнотекстовый индекс для таблицы в процессе слияния.<br /><br /> 0 = для таблицы отсутствует полнотекстовый индекс, либо индекс не находится в процессе слияния.<br /><br /> 1 = полнотекстовый индекс находится в процессе слияния.|  
|TableFullTextBackgroundUpdateIndexOn|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Таблица содержит включенный полнотекстовый индекс (с автоматическим отслеживанием изменений) с фоновым обновлением:<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Базовый тип данных: **int**|  
|TableFulltextCatalogId|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор полнотекстового каталога, в котором находятся данные полнотекстового индекса для таблицы.<br /><br /> Не 0 = идентификатор полнотекстового каталога, связанный с уникальным индексом, идентифицирующим строки в полнотекстовой индексированной таблице.<br /><br /> 0 = таблица не имеет полнотекстового индекса.<br /><br /> Базовый тип данных: **int**|  
|TableFullTextChangeTrackingOn|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Для таблицы включено полнотекстовое отслеживание изменений.<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Базовый тип данных: **int**|  
|TableFulltextDocsProcessed|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество строк, обработанных с начала полнотекстового индексирования. В таблице, которая индексируется для полнотекстового поиска, все столбцы одной строки рассматриваются как часть единого индексируемого документа.<br /><br /> 0 = отсутствие активного сканирования или полнотекстовое индексирование закончено.<br /><br /> > 0 = один из следующих (A или B): A) число документов, обработанных операциями вставки или операций обновления с момента начала полного, добавочного или ручного заполнения; отслеживания изменений (Б) число строк, обрабатываемых insert или операции обновления с момента включения отслеживания изменений при фоновом заполнении индекса, изменения схемы полнотекстового индекса, полнотекстовый каталог перестроен или экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапуск и т. д.<br /><br /> NULL = Таблица не содержит полнотекстового индекса.<br /><br /> Базовый тип данных: **int**<br /><br /> **Примечание** это свойство не отслеживает и не подсчитывает удаленные строки.|  
|TableFulltextFailCount|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Число строк, не проиндексированных для полнотекстового поиска.<br /><br /> 0 = Заполнение завершено.<br /><br /> > 0 = один из следующих (A или B): A) число документов, не индексированных с начала заполнения; отслеживания изменений полного, постепенного или ручного обновления (Б) для отслеживания изменений при фоновом режиме обновления индекса, количество строк, не индексированных с начала заполнения или перезапуска заполнения. Это может быть вызвано изменением схемы, перестройкой каталога, перезапуском сервера и т. д.<br /><br /> NULL = таблица не содержит полнотекстового индекса.<br /><br /> Базовый тип данных: **int**|  
|TableFulltextItemCount|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> NonNULL = число строк, которые были полнотекстово проиндексированы.<br /><br /> NULL = Таблица не содержит полнотекстового индекса.<br /><br /> Базовый тип данных: **int**|  
|TableFulltextKeyColumn|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор столбца, связанного с одностолбцовым уникальным индексом, который является частью определения полнотекстового индекса и семантического индекса.<br /><br /> 0 = таблица не имеет полнотекстового индекса.<br /><br /> Базовый тип данных: **int**|  
|TableFulltextPendingChanges|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество ожидающих отслеженных изменений к обработке.<br /><br /> 0 = Отслеживание изменений не включено.<br /><br /> NULL = Таблица не содержит полнотекстового индекса.<br /><br /> Базовый тип данных: **int**|  
|TableFulltextPopulateStatus|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = Бездействует.<br /><br /> 1 = Производится полное заполнение.<br /><br /> 2 = Производится добавочное заполнение.<br /><br /> 3 = Выполняется распространение отслеженных изменений.<br /><br /> 4 = выполняется индексирование фонового обновления (например автоматическое отслеживание изменений).<br /><br /> 5 = Полнотекстовое индексирование приостановлено, или не хватает ресурсов на его выполнение.<br /><br /> 6 = произошла ошибка. Дополнительные сведения в журнале сканирования. Дополнительные сведения см. в разделе **Устранение ошибок в заполнении средства полнотекстового поиска (сканирование)** раздел [заполнения полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).<br /><br /> Базовый тип данных: **int**|  
|TableFullTextSemanticExtraction|Таблица|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Таблица поддерживает семантическое индексирование.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasActiveFulltextIndex|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Таблица имеет активный полнотекстовый индекс.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasCheckCnst|Таблица|Таблица имеет ограничение CHECK.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasClustIndex|Таблица|Таблица имеет кластеризованный индекс.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasDefaultCnst|Таблица|Таблица имеет ограничение DEFAULT.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasDeleteTrigger|Таблица|У таблицы есть триггер DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasForeignKey|Таблица|Таблица имеет ограничение FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasForeignRef|Таблица|На таблицу есть ссылки по ограничению FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasIdentity|Таблица|Таблица содержит столбец идентификаторов.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasIndex|Таблица|Таблица имеет индекс какого-либо типа.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasInsertTrigger|Таблица|Объект имеет триггер INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasNonclustIndex|Таблица|Таблица содержит некластеризованный индекс:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasPrimaryKey|Таблица|Таблица содержит первичный ключ.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasRowGuidCol|Таблица|Таблица содержит свойство ROWGUIDCOL для **uniqueidentifier** столбца.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasTextImage|Таблица|Таблица имеет **текст**, **ntext**, или **изображения** столбца.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasTimestamp|Таблица|Таблица имеет **timestamp** столбца.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasUniqueCnst|Таблица|Таблица имеет ограничение UNIQUE.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasUpdateTrigger|Таблица|Объект содержит триггер UPDATE:<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableHasVarDecimalStorageFormat|Таблица|Таблица включается для **vardecimal** формат хранения.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableInsertTrigger|Таблица|Таблица содержит триггер INSERT.<br /><br /> > 1 = идентификатор первого триггера указанного типа.<br /><br /> Базовый тип данных: **int**|  
|TableInsertTriggerCount|Таблица|В таблице существует указанное число триггеров типа INSERT.<br /><br /> >0 = количество триггеров INSERT.<br /><br /> Базовый тип данных: **int**|  
|TableIsFake|Таблица|Таблица реально не существует. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] материализует ее внутренним образом по запросу.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableIsLockedOnBulkLoad|Таблица|Таблица заблокирована, так как **bcp** или заданием BULK INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|TableIsMemoryOptimized|Таблица|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Таблица, оптимизированная для памяти<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**<br /><br /> Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).|  
|TableIsPinned|Таблица|Таблица закреплена для хранения в кэше данных.<br /><br /> 0 = False.<br /><br /> Эта функция не поддерживается в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях.|  
|TableTextInRowLimit|Таблица|Для таблицы установлен параметр TEXT IN ROW.<br /><br /> > 0 = Максимальная длина текста в строке (в байтах).<br /><br /> 0 = Параметр текста в строке не установлен.<br /><br /> Базовый тип данных: **int**|  
|TableUpdateTrigger|Таблица|Таблица содержит триггер UPDATE.<br /><br /> > 1 = идентификатор первого триггера указанного типа.<br /><br /> Базовый тип данных: **int**|  
|TableUpdateTriggerCount|Таблица|В таблице существует указанное число триггеров типа UPDATE.<br /><br /> >0 = количество триггеров UPDATE.<br /><br /> Базовый тип данных: **int**|  
|UserDataAccess|Функция, представление|Указывает, что объект производит доступ к пользовательским данным, пользовательским таблицам в локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = чтение<br /><br /> 0 = нет<br /><br /> Базовый тип данных: **int**|  
|TableHasColumnSet|Таблица|Таблица содержит набор столбцов.<br /><br /> 0 = False.<br /><br /> 1 = True<br /><br /> Дополнительные сведения см. в статье [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).|  
|Количество элементов|Таблица (системная или определяемая пользователем), представление или индекс|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество строк в указанном объекте.|  
|TableTemporalType|Таблица|**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает тип таблицы.<br /><br /> 0 = нетемпоральные таблицы<br /><br /> 1 = Таблица журнала для таблицы с системным управлением версиями<br /><br /> 2 = временная таблица с системным управлением версиями|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **sql_variant**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это значит, что встроенные функции, создающие метаданные (например, OBJECTPROPERTYEX), могут возвращать значение NULL, если у пользователя нет разрешения на доступ к объекту. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Предполагается, что *object_id* находится в контексте текущей базы данных. Запрос, который ссылается на *object_id* в другой базе данных будут возвращать значение NULL или неправильные результаты. Например в следующем запросе текущий контекст базы данных является база данных master. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Попытается вернуть значение свойства для указанного *object_id* в этой базе данных вместо базы данных, указанный в запросе. Запрос возвращает неверные результаты, так как представление `vEmployee` не находится в базе данных master.  
  
```  
USE master;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID(N'AdventureWorks2012.HumanResources.vEmployee'), 'IsView');  
GO  
```  
  
 OBJECTPROPERTYEX (*view_i*d, 'IsIndexable') может потреблять значительные ресурсы компьютера, так как для вычисления свойства IsIndexable необходимы синтаксический анализ определения представления, нормализация и частичная оптимизация. Даже если свойство IsIndexable определяет, что таблицы или представления могут быть проиндексированы, фактическое создание индекса может завершиться ошибкой, если не выполняются требования к ключу индекса. Дополнительные сведения см. в разделе [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md).  
  
 OBJECTPROPERTYEX (*table_id*, 'TableHasActiveFulltextIndex') вернет значение 1 (true), если хотя бы один столбец таблицы был добавлен для индексирования. Заполнение полнотекстового индекса становится активным, как только для индексирования добавлен хотя бы один столбец.  
  
 К результирующему набору применяются ограничения на видимость метаданных. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-finding-the-base-type-of-an-object"></a>A. Определение базового типа объекта  
 В следующем примере производится создание синонима `MyEmployeeTable` для таблицы `Employee` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], а затем для него определяется базовый тип.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE SYNONYM MyEmployeeTable FOR HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX ( object_id(N'MyEmployeeTable'), N'BaseType')AS [Base Type];  
GO  
```  
  
 Результирующий набор показывает, что базовым типом соответствующего объекта, таблицы `Employee`, является пользовательская таблица.  
  
 `Base Type`  
  
 `--------`  
  
 `U`  
  
### <a name="b-returning-a-property-value"></a>Б. Получение значения свойства  
 Следующий пример показывает, как получить число триггеров UPDATE для указанной таблицы.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID(N'HumanResources.Employee'), N'TABLEUPDATETRIGGERCOUNT');  
GO  
  
```  
  
### <a name="c-finding-tables-that-have-a-foreign-key-constraint"></a>В. Поиск таблиц с ограничением FOREIGN KEY  
 В следующих примерах для возврата всех таблиц с ограничением внешнего ключа используется свойство `TableHasForeignKey`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name, object_id, schema_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTYEX(object_id, N'TableHasForeignKey') = 1  
ORDER BY name;  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-finding-the-base-type-of-an-object"></a>D: определение базового типа объекта  
 В следующем примере возвращается базовый тип `dbo.DimReseller` объекта.  
  
```  
-- Uses AdventureWorks  
  
SELECT OBJECTPROPERTYEX ( object_id(N'dbo.DimReseller'), N'BaseType')AS BaseType;  
```  
  
 Результирующий набор показывает, что базовым типом соответствующего объекта, таблицы `dbo.DimReseller`, является пользовательская таблица.  
  
```  
BaseType   
--------   
U   
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ СИНОНИМ &#40; Transact-SQL &#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION (Transact-SQL)](../../t-sql/functions/object-definition-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [Object_name &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)  
  
  

