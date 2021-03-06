---
title: Приложение SQL Profiler | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], profiler90 utility
- profiler90 utility
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: e91c30a9-0d29-4f84-bcb8-e8fb62afadda
caps.latest.revision: 42
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3bcd3dab5c08b7d8df8dec05004b7ee67bbb5a30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="profiler-utility"></a>Приложение SQL Profiler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Служебная программа **profiler** запускает средство [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] . Дополнительные аргументы, перечисленные ниже в этом разделе, позволяют управлять способом запуска приложения.  
  
> [!NOTE]  
>  Служебная программа **profiler** не предназначена для написания скриптов трассировки. Дополнительные сведения см. в разделе [Start SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
profiler  
    [ /? ] |  
[  
{  
{ /U login_id [ /P password ] }  
| /E  
}  
{[ /S sql_server_name ] | [ /A analysis_services_server_name ] }  
[ /D database ]  
[ /T "template_name" ]  
[ /B { "trace_table_name" } ]  
{ [/F "filename" ] | [ /O "filename" ] }  
[ /L locale_ID ]  
[ /M "MM-DD-YY hh:mm:ss" ]  
[ /R ]  
[ /Z file_size ]  
]  
```  
  
## <a name="arguments"></a>Аргументы  
 **/?**  
 Показывает сводку по синтаксису аргументов **profiler** .  
  
 **/U** *login_id*  
 Идентификатор входа при проверке подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . При записи идентификаторов входа регистр символов имеет значение.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)].  
  
 **/P** *password*  
 Задает пользовательский пароль для проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **/E**  
 Задает подключение с использованием проверки подлинности Windows с учетными данными текущего пользователя.  
  
 **/S**  *sql_server_name*  
 Указывает экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Profiler автоматически подключится к указанному серверу с использованием данных проверки подлинности, указанных в параметрах **/U** и **/P** или **/E** . Чтобы подключиться к именованному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], укажите **/S** *sql_server_name*\\*instance_name*.  
  
 **/A**  *analysis_services_server_name*  
 Указывает экземпляр служб Analysis Services. Profiler автоматически подключится к указанному серверу с использованием данных проверки подлинности, указанных в параметрах **/U** и **/P** или **/E** . Чтобы подключиться к именованному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , укажите **/A** *analysis_services_server_name\instance_name*.  
  
 **/D** *database*  
 Указывает имя базы данных, которая будет использоваться с соединением. Если база данных не указывается, этот аргумент выберет базу данных по умолчанию для указанного пользователя.  
  
 **/B "** *trace_table_name* **"**  
 Указывает таблицу трассировки для загрузки при запуске профайлера. Необходимо задать базу данных, пользователя или схему, а также таблицу.  
  
 **/T"** *template_name* **"**  
 Указывает шаблон, загружаемый для настройки трассировки. Имя шаблона должно быть заключено в кавычки. Имя шаблона должно находиться либо в системном каталоге шаблонов, либо в пользовательском каталоге шаблонов. В случае существования двух шаблонов с одним именем в обоих каталогах будет загружен шаблон, находящийся в системном каталоге. Если шаблон с указанным именем не существует, то будет загружен стандартный шаблон. Примечание. Расширение файла для шаблона (TDF) в аргументе *template_name*указывать не нужно. Пример:  
  
```  
/T "standard"  
```  
  
 **/F"** *filename* **"**  
 Указывает путь и имя файла трассировки, загружаемого при запуске профайлера. Полный путь и имя файла должны быть заключены в кавычки. Этот параметр нельзя использовать совместно с параметром **/O**.  
  
 **/O "** *filename*  **"**  
 Указывает путь и имя файла, в который должны быть записаны результаты трассировки. Полный путь и имя файла должны быть заключены в кавычки. Этот параметр нельзя использовать совместно с параметром **/F**.  
  
 **/L** *locale_ID*  
 Недоступно.  
  
 **/M "** *MM-DD-YY hh:mm:ss* **"**  
 Задает дату и время остановки трассировки. Время остановки должно быть заключено в кавычки. Задайте время остановки согласно параметрам в следующей таблице.  
  
|Параметр|Определение|  
|---------------|----------------|  
|ММ|Месяц (2 разряда)|  
|ДД|День (2 разряда)|  
|ГГ|Год (2 разряда)|  
|чч|Час (2 разряда), в 24-часовом формате|  
|ММ|Минуты (2 разряда)|  
|сс|Секунды (2 разряда)|  
  
> [!NOTE]  
>  Формат "ММ-ДД-ГГ чч:мм:сс" можно использовать только в том случае, если включен параметр **Использовать региональные настройки при показе значений даты и времени** в приложении [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]. Если этот параметр не включен, следует использовать формат даты и времени «ГГГГ-ММ-ДД чч:мм:сс».  
  
 **/R**  
 Включает операцию переключения на файл продолжения трассировки.  
  
 **/Z**  *file_size*  
 Определяет размер файла трассировки в мегабайтах (МБ). Размер по умолчанию составляет 5 МБ. Если включена операция переключения, все файлы продолжения будут ограничены значением, указанным в этом аргументе.  
  
## <a name="remarks"></a>Remarks  
 Для запуска трассировки с использованием определенного шаблона укажите параметры **/S** и **/T** . Например, чтобы запустить трассировку с использованием шаблона Standard на экземпляре MyServer\MyInstance, введите в командной строке:  
  
```  
profiler /S MyServer\MyInstance /T "Standard"  
```  
  
## <a name="see-also"></a>См. также:  
 [Справочник по программе командной строки (Database Engine)](../tools/command-prompt-utility-reference-database-engine.md)  
  
  
