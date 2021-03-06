---
title: Устранение неполадок при сборе данных для машинного обучения — SQL Server
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9b0fdd8d198675720188d6ab2417be97a9280c57
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708412"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Устранение неполадок при сборе данных для машинного обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описаны методы сбора данных, который следует использовать для устранения неполадок на локальном или с помощью клиента Microsoft поддержки при попытке. 

**Применяется к:** служб R SQL Server 2016, SQL Server 2017 г машинного обучения службы (R и Python)


## <a name="sql-server-version-and-edition"></a>Версии и выпуска SQL Server

SQL Server 2016 R Services находится в первом выпуске SQL Server для поддержки интеграции R. SQL Server 2016 с пакетом обновления 1 (SP1) включает в себя значительные улучшения, включая возможность запуска внешних скриптов. Если вы являетесь клиентом SQL Server 2016, рассмотрите возможность установки пакета обновления 1 или более поздней версии.

SQL Server 2017 г. добавлены интеграции языка Python. Не удается получить Python функция интеграции в более ранних выпусках.

Помощь начало выпуска и версии, см. в этой статье перечислены номера построения для каждого из [версий SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions).

В зависимости от выпуска SQL Server, вы используете некоторые машинного обучения функциональность может быть недоступность или ограниченная. Следующий список статей функции обучения компьютера в выпусках Enterprise, Developer, Standard и Express.

* [Выпуски и поддерживаемых функций SQL Server](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [Функции R и Python выпусках SQL Server](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>Версии языка и средства R

Как правило версии Microsoft R, которая устанавливается при выборе функции служб R и службах обучения машин определяется номер сборки SQL Server. Если выполняется обновление или исправление для SQL Server, необходимо обновить или исправить его компонентов R.

Список выпусков, а также ссылки на загружаемые файлы компонентов R см. в разделе [установить компоненты обучения компьютер без доступа к Интернету](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access). На компьютерах с доступом в Интернет требуемая версия R идентифицировать и устанавливается автоматически.

Это возможно обновление компонентов R Server отдельно от SQL Server database engine, в процессе, называемом привязки. Таким образом версии R, используемый при выполнении кода R в SQL Server могут отличаться в зависимости от установленной версии SQL Server и на ли были перенесены сервер до последней версии R.

### <a name="determine-the-r-version"></a>Определить версию R

Для определения версии R проще всего получить свойствам среды выполнения, выполнив инструкции из следующего:

```SQL
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"), 
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP] 
> Если R Services не работает, попробуйте выполнить только часть скрипта R из RGui.

В качестве последнего средства можно открывать файлы на сервере, чтобы определить установленную версию. Чтобы сделать это, найдите файл rlauncher.config, чтобы получить расположение среды выполнения R и текущего рабочего каталога. Рекомендуется создать и открыть копию файла, чтобы случайного изменения любого свойства.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

Чтобы получить версии R и RevoScaleR, откройте окно командной строки R или открыть RGui, который связан с экземпляром.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`


В консоли R отображаются сведения о версии во время запуска. Например следующая версия представляет конфигурации по умолчанию для SQL Server 2017 г CTP 2.0:

    *Microsoft R Open 3.3.3*
    
    *The enhanced R distribution from Microsoft*
    
    *Microsoft packages Copyright (C) 2017 Microsoft*
    
    *Loading Microsoft R Server packages, version 9.1.0.*


## <a name="python-versions"></a>Версии Python

Существует несколько способов получить версию Python. Проще всего выполнить эту инструкцию из среды Management Studio или другого средства запросов SQL:

```SQL
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Если службы обучения машина не запущена, можно определить установленную версию Python, просмотрев файл pythonlauncher.config. Рекомендуется создать и открыть копию файла, чтобы случайного изменения любого свойства.

1. Только для SQL Server 2017 г.: `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config `
2. Получить значение для **PYTHONHOME**.
3. Получает значение в текущем рабочем каталоге.


> [!NOTE]
> После установки Python и R в SQL Server 2017 г., рабочий каталог и пул рабочих учетных записей являются общими для языков R и Python.

## <a name="are-multiple-instances-of-r-or-python-installed"></a>Несколько экземпляров R или Python установлен?

Проверьте, установлена ли более одной копии библиотек R на компьютере. Это дублирование может произойти, если:

* Во время установки выбрать службы R (в базе данных) и R Server (изолированный). 
* Установки клиента Microsoft R в дополнение к SQL Server.
* Другой набор библиотек R была установлена с помощью средства R для Visual Studio, R Studio, Microsoft R клиента или другого интерфейса IDE r.
* Компьютер содержит несколько экземпляров SQL Server и более одного экземпляра с применением машинного обучения.

Применяются те же условия Python.

Если установлено несколько библиотек или сред выполнения, убедитесь, что вы получите только ошибки, связанные с сред выполнения Python или R, которые используются экземпляром SQL Server.

## <a name="origin-of-errors"></a>Источник ошибки

Ошибки, которые возникают при попытке запуска кода R могут поступать из любой из следующих источников:

- СУБД SQL Server, включая sp_execute_external_script хранимой процедуры
- Доверенная панель запуска SQL Server 
- Другие компоненты платформы расширения, включая средства запуска R и Python и вспомогательных процессов
- Поставщики, например Microsoft Open Database Connectivity (ODBC)
- Язык R

При работе со службой в первый раз, может быть трудно определить, какие сообщения получаются из службы. Корпорация Майкрософт рекомендует для сохранения не только текстовое сообщение об ошибке, но контекст, в котором показано сообщение. Обратите внимание, клиентское программное обеспечение, которую вы используете для запуска машинного обучения кода:

- Вы используете среду Management Studio? Внешнее приложение?
- Выполняется ли код R, в удаленных клиентов или непосредственно в хранимой процедуре?

## <a name="sql-server-log-files"></a>Файлы журнала SQL Server

Получите самые последние ОШИБОК SQL Server. Полный набор файлов журнала ошибок, состоит из файлов в папке журнала по умолчанию:

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE] 
> Точное имя папки зависит от того, имя экземпляра.


## <a name="errors-returned-by-spexecuteexternalscript"></a>Ошибки, возвращенные sp_execute_external_script

Получите полный текст ошибки, которые возвращаются, если таковая имеется, при выполнении команды sp_execute_external_script. 

Для предотвращения проблем R или Python из рассмотрения, можно выполнять этот скрипт, который запускает среду выполнения R или Python и передает данные и обратно.

**Для R**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Для Python**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>Ошибки, созданные с помощью extensibility framework

SQL Server создает отдельные файлы журналов для среды выполнения языка внешних скриптов. Эти ошибки не формируются языка Python или R. Они будут созданы из компонентов расширяемости в SQL Server, включая средства запуска конкретного языка и их вспомогательных процессов.

Эти журналы можно получить из следующих расположений по умолчанию.

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog `

> [!NOTE] 
> Точное имя папки отличается в зависимости от имени экземпляра. В зависимости от конфигурации папка может быть на другом диске.

Например следующие сообщения журнала, относящиеся к структуре расширяемости.

* *Сбой LogonUser для пользователя MSSQLSERVER01*
  
  Это может указывать учетные записи работника, которые работают внешних скриптов не может обращаться к экземпляру.

* *Не удалось выполнить InitializePhysicalUsersPool* 
  
  Это сообщение может означать, что параметры безопасности препятствуют установки создавать пул рабочих учетных записей, которые необходимы для выполнения внешних скриптов.

* *Не удалось инициализировать диспетчер контекста безопасности* 

* *Не удалось инициализировать диспетчер сеансов вспомогательных*

## <a name="system-events"></a>Системные события

1. Откройте средство просмотра событий Windows и поиск **системное событие** журнала для сообщений, содержащих строки *запуска*. 
2. Откройте файл ExtLaunchErrorlog и наличие строки *ErrorCode*. Ознакомьтесь с сообщением, связанной с ErrorCode.

Например следующие сообщения являются общих системных ошибок, относящихся к структуре расширяемости SQL Server: 

* *Служба панели запуска SQL Server (MSSQLSERVER) не удалось запуститься из-за следующей ошибки:  <text>*

* *Служба не ответила на запрос запуска или управления в течение отведенного времени.* 

* *Время ожидания (в миллисекундах 120000) во время ожидания для службы панели запуска SQL Server (MSSQLSERVER) для подключения.* 

## <a name="dump-files"></a>Файлы дампа

Если знаниями об отладке, файлы дампа можно использовать для анализа сбоев в панель запуска.

1. Найдите папку, содержащую журналы установки начальной загрузки для SQL Server. Например в SQL Server 2016 путь по умолчанию был C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log.
2. Откройте папку начальной загрузки журнала, характерное для расширяемости.
3. Если необходимо отправить запрос на техническую поддержку, добавьте все содержимое этой папки в ZIP-файл. Например C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\Log\LOG\ExtensibilityLog.
  
Точное расположение может отличаться в вашей системе, и может оказаться на диске, отличном от диска C. Убедитесь в том, что получить журналы для экземпляра, где установлен машинного обучения. 


## <a name="configuration-settings"></a>Параметры конфигурации

В этом разделе перечислены дополнительные компоненты или поставщики, которые могут быть источника ошибок при выполнении скриптов R или Python.

### <a name="what-network-protocols-are-available"></a>Доступных сетевых протоколов?

Службы обучения машины требуются следующие сетевые протоколы для внутренней связи между компонентами расширяемости и для связи с внешними клиентами R или Python.

* Именованные каналы
* TCP/IP

Откройте диспетчер конфигурации SQL Server для определения протокола, установлен ли и, если он установлен, чтобы определить, включена ли она.

### <a name="security-configuration-and-permissions"></a>Настройки безопасности и разрешений

Для рабочих учетных записей:

1. В панели управления откройте **пользователей и групп**и найдите группу, используемую для запуска заданий внешнего скрипта. По умолчанию группа — **SQLRUserGroup**.
2. Убедитесь, что группа существует и что он содержит по крайней мере одной рабочей учетной записи.
3. В SQL Server Management Studio, выберите экземпляр, в которой будет выполняться задания R или Python, выберите **безопасности**и определить, существует ли имя входа для SQLRUserGroup.
4. Просмотреть разрешения для группы пользователей.

Для отдельных учетных записей пользователей:

1. Определите, поддерживает ли экземпляр смешанного режима проверки подлинности, только имена входа SQL или только проверку подлинности Windows. Этот параметр влияет на R или Python code требования.
2. Для каждого пользователя, которому необходимо запустить код R определите требуемый уровень разрешений для каждой базы данных, где объекты будут записаны из R, будет получить доступ к данным или будут создаваться объекты.
3. Чтобы включить выполнение скриптов, Создание ролей или добавить пользователей в следующих ролей, при необходимости:

   - Все, кроме *db_owner*: требуется EXECUTE ANY EXTERNAL SCRIPT.
   - *db_datawriter*: для записи результатов из R или Python. 
   - *db_ddladmin*: для создания новых объектов. 
   - *db_datareader*: для чтения данных, используемый в коде R или Python. 
4. Обратите внимание, изменено ли учетные записи запуска по умолчанию при установке SQL Server 2016.
5. Если пользователю нужно установить новый R-пакетов или использовать пакеты R, которые были установлены с другими пользователями, может потребоваться включить управление пакетами в экземпляре, а затем назначьте дополнительные разрешения. Дополнительные сведения см. в разделе [включить или отключить управление пакетами R](r\r-package-how-to-enable-or-disable.md).

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>Какие папки подлежат блокировки антивирусной программой?

Антивирусное программное обеспечение можно заблокировать папок, что запрещает установки машинного обучения, функций и выполнение скрипта успешно. Определите все папки в дереве SQL Server может быть проверка на наличие вирусов.

Тем не менее при нескольких служб или компоненты установлены на экземпляре, может быть трудно перечислить все возможные папки, которые используются в экземпляре. Например при добавлении новых функций, новых папок должно быть определены и исключен.

Кроме того некоторые возможности создавать новые папки динамически во время выполнения. Например таблицы OLTP в памяти, хранимые процедуры и функции создайте новые каталоги во время выполнения. Эти имена папок часто содержат идентификаторы GUID, предсказать нельзя. Панель запуска SQL Server доверенные создает новые рабочие каталоги для R и Python скрипты заданий.

Может оказаться невозможным исключить все папки, которые требуются процесс SQL Server и его компонентах, поэтому рекомендуется исключить все дерево каталогов экземпляра SQL Server.

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>Открыта брандмауэра для SQL Server? Поддерживает ли экземпляр удаленные соединения?

1. Чтобы определить, поддерживает ли SQL Server удаленные соединения, в разделе [Настройка соединения с удаленным сервером](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md).

2. Определяет, создается ли правило брандмауэра для SQL Server. По соображениям безопасности при установке по умолчанию не возможно для удаленных клиентов R или Python для подключения к экземпляру. Дополнительные сведения см. в разделе [Устранение неполадок подключения к SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).


## <a name="see-also"></a>См. также

[Устранение неполадок машинного обучения в SQL Server](machine-learning-troubleshooting-faq.md)
