---
title: "Использование собственного формата для импорта или экспорта данных (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 09/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-bulk-import-export
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4cb08ec44780935a8340d267fd3790af5150659b
ms.contentlocale: ru-ru
ms.lasthandoff: 07/31/2017

---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a>Использование собственного формата для импорта или экспорта данных
Собственный формат данных рекомендуется использовать при массовой передаче данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через файл данных, который не содержит символов в расширенной кодировке или символов в двухбайтовой кодировке (DBCS).  

> [!NOTE]
>  При массовой передаче данных между несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи файла данных, содержащего символы в расширенной кодировке или символы DBCS, необходимо использовать собственный формат в Юникоде. Дополнительные сведения см. в разделе [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).

В собственном формате используются собственные типы данных базы данных. Собственный формат предназначен для высокоскоростной передачи данных между таблицами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если используется файл форматирования, то исходная и целевая таблицы не обязаны быть идентичными. Передача данных происходит в два этапа:  
  
1.  Массовый экспорт данных из исходной таблицы в файл данных.  
  
2.  Массовый импорт данных из файла данных в целевую таблицу.  
  
Использование собственного формата между идентичными таблицами позволяет избежать бесполезного преобразования типов данных из символьного формата и обратно, экономя тем самым время и пространство хранения. Для достижения оптимальной скорости передачи, однако, уменьшается количество проверок форматирования данных. Чтобы избежать проблемы с загруженными данными, изучите следующий список ограничений.  

|В этом разделе.|
|---|
|[Ограничения](#restrictions)|
|[Как bcp обрабатывает данные в собственном формате](#considerations)|
|[Параметры командной строки для собственного формата](#command_options)|
|[Пример условий теста](#etc)<br /><br />&emsp;&#9679;&emsp;[Образец таблицы](#sample_table)<br />&emsp;&#9679;&emsp;[Образец файла форматирования в формате, отличном от XML](#nonxml_format_file)|
|[Примеры](#examples)<br />&emsp;&#9679;&emsp;[Использование bcp и собственного формата для экспорта данных](#bcp_native_export)<br />&emsp;&#9679;&emsp;[Использование bcp и собственного формата для импорта данных без файла форматирования](#bcp_native_import)<br />&emsp;&#9679;&emsp;[Использование bcp и собственного формата для импорта данных с файлом форматирования, не являющимся XML-файлом](#bcp_native_import_fmt)<br />&emsp;&#9679;&emsp;[Использование инструкции BULK INSERT и собственного формата без файла форматирования](#bulk_native)<br />&emsp;&#9679;&emsp;[Использование инструкции BULK INSERT и собственного формата с файлом форматирования, не являющимся XML-файлом](#bulk_native_fmt)<br />&emsp;&#9679;&emsp;[Использование инструкции OPENROWSET и собственного формата с файлом форматирования, не являющимся XML-файлом](#openrowset_native_fmt)|
|[Связанные задачи](#RelatedTasks)<p>                                                                                                                                                                                                                  </p>|

## Ограничения<a name="restrictions"></a>  
Чтобы успешно импортировать данные в собственный формат, убедитесь, что:  
  
-   Файл данных создан в собственном формате.  
  
-   Либо целевая таблица должна быть совместима с файлом данных (иметь верное число столбцов, типы данных, длину, допустимость значений NULL и так далее), либо необходимо использовать файл форматирования для сопоставления каждого поля с соответствующим столбцом.  
  
    > [!NOTE]
    >  Если импортируются данные из файла, не совпадающего по структуре с целевой таблицей, то, хотя операция импорта может завершиться успешно, вставляемые в целевую таблицу данные, скорее всего, будут неправильными. Это происходит из-за того, что данные из файла интерпретируются при помощи формата целевой таблицы. Таким образом, любые различия приведут к вставке неправильных данных. Однако ни при каких обстоятельствах подобные различия не могут привести к логическому или физическому несоответствию в базе данных.  
  
     Дополнительные сведения см. в разделе [Файлы форматирования для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
 Успешный импорт не приводит к повреждению целевой таблицы.  
  
## Как bcp обрабатывает данные в собственном формате<a name="considerations"></a>
 В этом разделе обсуждаются особые аспекты выполнения программой **bcp** операций экспорта и импорта данных в собственном формате.  
  
-   Несимвольные данные.  
  
     [Программа bcp](../../tools/bcp-utility.md) использует для записи несимвольных данных из таблицы в файл данных внутренний двоичный формат данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Данные типа[char](../../t-sql/data-types/char-and-varchar-transact-sql.md) или [varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md) .  
  
     В начале каждого поля [char](../../t-sql/data-types/char-and-varchar-transact-sql.md) или [varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md) программа [bcp](../../tools/bcp-utility.md) добавляет длину префикса.  
  
    > [!IMPORTANT]
    >  По умолчанию при использовании собственного режима программа [bcp](../../tools/bcp-utility.md) перед копированием в файл данных преобразует символы из формата [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в символы OEM. [Программа bcp](../../tools/bcp-utility.md) преобразует символы из файла данных в символы ANSI перед их массовым импортом в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Во время подобных преобразований расширенные символьные данные могут быть потеряны. Для расширенных наборов символов необходимо либо использовать собственный формат в Юникоде, либо задать кодовую страницу.
  
-   [sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md) data  
  
     Если данные типа [sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md) сохраняются как SQLVARIANT в файле данных в собственном формате, то все характеристики данных сохраняются. Метаданные, в которых записан тип данных каждой величины, записываются вместе со значениями данных. Эти метаданные используются для повторного создания значений данных с тем же типом данных, что и в столбце назначения [sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md) .  
  
     Если в столбце назначения тип данных отличается от [sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md), то каждое значение данных преобразуется в тип данных столбца назначений согласно стандартным правилам неявного преобразования данных. При возникновении ошибки во время преобразования данных происходит откат текущего пакета. С любыми значениями [char](../../t-sql/data-types/char-and-varchar-transact-sql.md) и [varchar](../../t-sql/data-types/char-and-varchar-transact-sql.md), которые передаются между столбцами [sql_variant](../../t-sql/data-types/sql-variant-transact-sql.md), могут возникнуть проблемы преобразования кодовых страниц.  
  
     Дополнительные сведения о преобразовании данных см. в статье [Преобразование типов данных (ядро СУБД)](../../t-sql/data-types/data-type-conversion-database-engine.md).  
  
## Параметры командной строки для собственного формата<a name="command_options"></a>  
Импортировать в таблицу данные в собственном формате можно при помощи программы [bcp](../../tools/bcp-utility.md), инструкции [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) или [INSERT ... SELECT * FROM OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md).  Для команды [bcp](../../tools/bcp-utility.md) или инструкции [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) формат данных можно указать в инструкции.  Для инструкции [INSERT ... SELECT * FROM OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md) нужно указать формат данных в файле форматирования.  

Собственный формат поддерживается следующими параметрами командной строки:  

|Command|Параметр|Описание|  
|-------------|------------|-----------------|  
|bcp|**-n**|Приводит к использованию служебной программой bcp собственных типов данных. *|  
|BULK INSERT|DATAFILETYPE **="native"**|Использует собственный тип данных или расширенный собственный тип данных. Учтите, что параметр DATAFILETYPE не нужен, если типы данных указываются в файле форматирования.|  
|OPENROWSET|Недоступно|Требуется использовать файл форматирования.|

  
 \*Чтобы загрузить собственные (**-n**) данные в формате, совместимом с клиентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущих версий, используйте параметр **-V** . Дополнительные сведения см. в разделе [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
> [!NOTE]
>  Также в файле форматирования можно указать форматирование для каждого поля. Дополнительные сведения см. в статье [Файлы форматирования для импорта или экспорта данных (SQL Server)](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).
  

## Пример условий теста<a name="etc"></a>  
Примеры в этой статье основаны на таблице и файле форматирования, которые определены ниже.

### **Образец таблицы**<a name="sample_table"></a>
Приведенный ниже скрипт создает тестовую базу данных, таблицу с именем `myNative` и заполняет таблицу начальными значениями.  Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
CREATE DATABASE TestDatabase;
GO

USE TestDatabase;
CREATE TABLE dbo.myNative ( 
   PersonID smallint NOT NULL,
   FirstName varchar(25) NOT NULL,
   LastName varchar(30) NOT NULL,
   BirthDate date,
   AnnualSalary money
   );

-- Populate table
INSERT TestDatabase.dbo.myNative
VALUES 
(1, 'Anthony', 'Grosse', '1980-02-23', 65000.00),
(2, 'Alica', 'Fatnowna', '1963-11-14', 45000.00),
(3, 'Stella', 'Rossenhain', '1992-03-02', 120000.00);

-- Review Data
SELECT * FROM TestDatabase.dbo.myNative;
```

### **Образец файла форматирования в формате, отличном от XML**<a name="nonxml_format_file"></a>
SQL Server поддерживает два типа файлов форматирования: файлы форматирования в формате, отличном от XML, и XML-файлы форматирования.  Файл форматирования не в формате XML поддерживается более ранними версиями SQL Server.  Дополнительные сведения см. в разделе [Файлы формата, отличные от XML (SQL Server)](../../relational-databases/import-export/non-xml-format-files-sql-server.md) .  Следующая команда будет использовать [служебную программу bcp](../../tools/bcp-utility.md) для создания файла форматирования `myNative.fmt`в формате, отличном от XML, на основе схемы `myNative`.  Чтобы создать файл форматирования с помощью служебной программы [bcp](../../tools/bcp-utility.md) , укажите аргумент **format** , а вместо пути файла данных задайте значение **nul** .  Параметр format также требует наличия параметра **-f** .  Кроме того, в этом примере квалификатор **c** используется для указания символьных данных, а **T** используется для указания доверенного подключения, в рамках которого применяется встроенная система безопасности.  В командной строке введите следующие команды:

```
bcp TestDatabase.dbo.myNative format nul -f D:\BCP\myNative.fmt -T -n 

REM Review file
Notepad D:\BCP\myNative.fmt
```

> [!IMPORTANT]
> Убедитесь, что файл форматирования не в формате XML заканчивается символом перевода строки или возврата каретки.  В противном случае, скорее всего, появится следующее сообщение об ошибке:
> 
> `SQLState = S1000, NativeError = 0`  
> `Error = [Microsoft][ODBC Driver 13 for SQL Server]I/O error while reading BCP format file`

## Примеры<a name="examples"></a>
В приведенных ниже примерах используется база данных и файлы форматирования, созданные ранее.

### **Использование bcp и собственного формата для экспорта данных**<a name="bcp_native_export"></a>
**-n** и команда **OUT** .  Примечание. Файл данных, созданный в этом примере, будет использоваться во всех последующих примерах.  В командной строке введите следующие команды:
```
bcp TestDatabase.dbo.myNative OUT D:\BCP\myNative.bcp -T -n

REM Review results
NOTEPAD D:\BCP\myNative.bcp
```

### **Использование bcp и собственного формата для импорта данных без файла форматирования**<a name="bcp_native_import"></a>
**-n** и команда **IN** .  В командной строке введите следующие команды:
```
REM Truncate table (for testing)
SQLCMD -Q "TRUNCATE TABLE TestDatabase.dbo.myNative;"

REM Import data
bcp TestDatabase.dbo.myNative IN D:\BCP\myNative.bcp -T -n

REM Review results
SQLCMD -Q "SELECT * FROM TestDatabase.dbo.myNative;"
```

### **Использование bcp и собственного формата для импорта данных с файлом форматирования, не являющимся XML**<a name="bcp_native_import_fmt"></a>
**-n** и **-f** и команда **IN** .  В командной строке введите следующие команды:
```
REM Truncate table (for testing)
SQLCMD -Q "TRUNCATE TABLE TestDatabase.dbo.myNative;"

REM Import data
bcp TestDatabase.dbo.myNative IN D:\BCP\myNative.bcp -f D:\BCP\myNative.fmt -T

REM Review results
SQLCMD -Q "SELECT * FROM TestDatabase.dbo.myNative;"
```

### **Использование инструкции BULK INSERT и собственного формата без файла форматирования**<a name="bulk_native"></a>
Аргумент**DATAFILETYPE** .  Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
TRUNCATE TABLE TestDatabase.dbo.myNative; -- for testing
BULK INSERT TestDatabase.dbo.myNative
    FROM 'D:\BCP\myNative.bcp'
    WITH (
        DATAFILETYPE = 'native'
        );

-- review results
SELECT * FROM TestDatabase.dbo.myNative;
```

### **Использование инструкции BULK INSERT и собственного формата с файлом форматирования, не являющимся XML**<a name="bulk_native_fmt"></a>
Аргумент**FORMATFILE** .  Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
TRUNCATE TABLE TestDatabase.dbo.myNative; -- for testing
BULK INSERT TestDatabase.dbo.myNative
   FROM 'D:\BCP\myNative.bcp'
   WITH (
        FORMATFILE = 'D:\BCP\myNative.fmt'
        );

-- review results
SELECT * FROM TestDatabase.dbo.myNative;
```

### **Использование инструкции OPENROWSET и собственного формата с файлом форматирования, не являющимся XML**<a name="openrowset_native_fmt"></a>
Аргумент**FORMATFILE** .  Выполните следующий запрос Transact-SQL в Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS):
```tsql
TRUNCATE TABLE TestDatabase.dbo.myNative;  -- for testing
INSERT INTO TestDatabase.dbo.myNative
    SELECT *
    FROM OPENROWSET (
        BULK 'D:\BCP\myNative.bcp', 
        FORMATFILE = 'D:\BCP\myNative.fmt'  
        ) AS t1;

-- review results
SELECT * FROM TestDatabase.dbo.myNative;
```
  
## Связанные задачи<a name="RelatedTasks"></a>
Использование форматов данных для массового импорта или экспорта 
  
-   [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Использование символьного формата для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование символьного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)   
 [Импорт данных в собственном и символьном формате из предыдущих версий SQL Server](../../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [Использование собственного формата Юникод для импорта и экспорта данных (SQL Server)](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
