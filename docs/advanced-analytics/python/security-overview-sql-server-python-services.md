---
title: Общие сведения о безопасности для Python в машинном обучении SQL Server | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d0e2e12dd40dd8a7f7a90beda5a06b751d70aed2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="security-overview-for-python-in-sql-server-machine-learning"></a>Общие сведения о безопасности для Python в машинном обучении SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом разделе описывается архитектура безопасности, используемый для подключения [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ядра и Python компоненты базы данных. Приведенные примеры процесса безопасности для двух стандартных сценариев: выполнение Python в SQL Server с помощью хранимой процедуры, а также с SQL Server в контексте удаленного Python.

## <a name="security-overview"></a>Общие сведения о безопасности

Объект [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] для запуска сценария Python в SQL Server требуется имя входа или учетная запись пользователя Windows. Эти *субъекты безопасности* осуществляется на уровне экземпляра и базы данных и определить пользователей, имеющих разрешение на подключение к базе данных, чтение и запись данных или создания объектов базы данных, например таблицы или хранимых процедур. Кроме того пользователи, запускающие сценарий Python необходимо иметь разрешение на выполнение внешних скриптов на уровне базы данных.

Даже пользователи, которые используются в внешнего средства Python должен быть сопоставлен имени входа или учетной записи в базе данных, если пользователь должен выполнять Python код в базе данных, или объекты базы данных access и данных. Те же разрешения требуются ли сценарий Python отправляется из клиента обработки и анализа удаленных данных или работы с помощью T-SQL для хранимой процедуры.

Например, предположим, что созданный сценарий Python, который выполняется на вашем ноутбуке и вы хотите запустить этот код [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Для этого должны быть выполнены приведенные ниже условия.

+ База данных должна разрешать удаленные подключения.
+ Имя входа SQL или учетной записью Windows, используемой для доступа к базе данных будет добавлен [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] на уровне экземпляра.
+ Имени входа SQL или пользователю Windows должны быть предоставлены разрешения на выполнение внешних скриптов. Обычно это разрешение может добавить только администратор базы данных.
+ Имя входа SQL или окно пользователя необходимо добавить как пользователь, с соответствующими разрешениями, в каждой базе данных, где выполняет сценарий Python любой из следующих операций:
    + извлечение данных;
    + запись или обновление данных;
    + создание новых объектов, например таблиц или хранимых процедур.

После имени входа или учетной записи пользователя Windows были подготовлены и предоставлены необходимые разрешения, можно выполнять код Python [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] с помощью объектов источника данных, предоставляемых **revoscalepy** библиотеки, или путем обращения к хранимому процедура, которая содержит скрипт Python.

Каждый раз, когда запускается скрипт на Python [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], безопасность ядра базы данных возвращает контекст безопасности пользователя, запустившего задание и управляет сопоставлениями пользователя или имени входа к защищаемым объектам.

Таким образом все скрипты Python, инициированные с удаленного клиента необходимо указать сведения о имени входа или пользователя в строке подключения.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Взаимодействие [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] и безопасности на панели запуска

При выполнении сценария Python в контексте [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] компьютера, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] служба возвращает доступный рабочий учетную запись (учетная запись локального пользователя) из пула рабочих учетных записей, установленным для внешних процессов и использует учетную запись для этих рабочих Выполните задачи.

Например предположим, что запуск сценария Python вашими учетными данными домена Windows. Возвращает учетные данные SQL Server и сопоставляет задачу доступных запуска рабочей учетной записи, такие как *SQLRUser01*.

> [!NOTE]
> Имя группы рабочих учетных записей одинаково независимо от того, используется ли R или Python. Тем не менее отдельную группу создается для каждого экземпляра, где включен любой внешний язык.

После сопоставления с рабочей учетной записью [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] создаст токен пользователя, который будет использоваться для запуска процессов. 

Когда все операции [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] будут завершены, рабочая учетная запись пользователя будет помечена как свободная и вернется в пул.

Дополнительные сведения о [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], в разделе [компоненты SQL Server для поддержки интеграции Python](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md).

### <a name="implied-authentication"></a>Неявная проверка подлинности

**Неявной проверки подлинности** является термин, используемый для процесса, в которой SQL Server возвращает пользователя, учетные данные, а затем выполняет все задачи внешний скрипт от имени пользователей, при условии, что пользователь имеет необходимые разрешения в базе данных. Неявной проверки подлинности является особенно важно, если сценарий Python должен произвести вызов ODBC вне базы данных SQL Server. Например код может получить более короткому списку факторов из электронной таблицы или другого источника.

Такие вызовы замыкания на себя для успешного выполнения группу, содержащую рабочих учетных записей, SQLRUserGroup, необходимо иметь разрешения «Локальный вход в систему». По умолчанию это право предоставляется для всех новых локальных пользователей, но в некоторых организациях могут применяться более строгие политики группы.

![Неявной проверки подлинности для R](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>Безопасность рабочих учетных записей

Сопоставление внешнего пользователя Windows или рабочей учетной записи входа SQL является допустимым только для времени существования SQL хранимой процедуры, которая выполняет сценарий Python.

Параллельные запросы, выполняемые с тем же именем входа, сопоставляются с той же рабочей учетной записью пользователя.

Каталоги, используемые для процессов, управляемых [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], и каталогов, доступ ограничен. Для Python PythonLauncher выполняет эту задачу. Каждая учетная запись отдельного работника ограничен в собственную папку и нет доступа к файлам в папках выше свой собственный уровень. Однако рабочая учетная запись может чтение, запись или удаление дочерних объектов в рабочую папку сеанса, который был создан.

Дополнительные сведения о том, как изменить количество рабочих учетных записей, имена учетных записей или паролей учетных записей см. в разделе [изменение пула учетных записей пользователей для SQL Server машинного обучения](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Изоляция безопасности для нескольких внешних скриптов

Механизм изоляции основана на физических учетных записей. Так как вспомогательные процессы запускаются для определенной языковой среды выполнения, каждая вспомогательная задача использует рабочую учетную запись, которую указала [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Если для выполнения задачи требуется несколько вспомогательных процессов, как в случае параллельных запросов, то для всех связанных задач будет использоваться одна рабочая учетная запись.

При этом доступ к файлам, используемым другими рабочими учетными записями, отсутствует.

Если вы являетесь администратором компьютера, вы можете просмотреть каталоги, созданные для каждого процесса. Каждый каталог определяется собственным идентификатором GUID сеанса.

## <a name="see-also"></a>См. также

[Обзор архитектуры](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
