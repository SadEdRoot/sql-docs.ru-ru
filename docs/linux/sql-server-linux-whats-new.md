---
title: Новые возможности для SQL Server 2017 г. для Linux | Документы Microsoft
description: В данной статье описываются новые возможности для 2017 г. SQL Server в Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: f0e20a06faed4b2d6cda1b80f5be9d41aa2c14f1
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Новые возможности для 2017 г. SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описываются основные функции и службы, доступные для ОС Linux 2017 г. SQL Server.

> [!NOTE]
> Помимо этих возможностей в этой статье накопительные обновления выпускаются с регулярными интервалами после выпуска общедоступной версии. Эти накопительные обновления содержат много усовершенствований и исправлений. Сведения о последнем выпуске CU см. в разделе [ http://aka.ms/sql2017cu ](http://aka.ms/sql2017cu). Загрузка пакетов и известных проблемах см. в разделе [заметки о выпуске](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>Компонент SQL Server Database Engine

- Включить основных возможностей SQL Server Database Engine.
- Поддержка собственного пути Linux.
- Поддержка протокола IPv6.
- Поддержку файлов баз данных в NFS.
- Включить [прозрачный слой безопасности](sql-server-linux-encrypted-connections.md) шифрования (TLS).
- Включить [проверки подлинности Active Directory](sql-server-linux-active-directory-authentication.md).
- [Функции групп доступности](sql-server-linux-availability-group-overview.md) для обеспечения высокой доступности.
- [Компонент Full-text Search](sql-server-linux-setup-full-text-search.md) поддержки.

## <a name="sql-server-agent"></a>SQL Server, агент

- Включить [агента SQL Server](sql-server-linux-setup-sql-agent.md) поддержки для выполнения следующих задач:
  - [Задания Transact-SQL](sql-server-linux-run-sql-server-agent-job.md)
  - [DB mail](sql-server-linux-db-mail-sql-agent.md)
  - [Доставка журналов](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>Службы SQL Server Integration Services

- Возможность запускать пакеты служб SSIS в Linux. Дополнительные сведения см. в разделе [настройки SQL Server Integration Services в Linux с помощью служб ssis conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Другие усовершенствования

- Средство командной строки настройки [mssql conf](sql-server-linux-configure-mssql-conf.md).
- Поддержка автоматической установки с помощью [переменных среды](sql-server-linux-configure-environment-variables.md).
- Кросс платформенных [расширения Visual Studio Code mssql сервера](sql-server-linux-develop-use-vscode.md).
- Генератор скриптов между различными платформами, [mssql-scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Монитор кросс платформенных динамическое административное представление (DMV), [DBFS средство](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Следующие шаги

Для установки SQL Server в Linux, используйте один из следующих учебников:

- [Установите на Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Установите на SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Установите на Ubuntu](quickstart-install-connect-ubuntu.md)
- [Запустите на Docker](quickstart-install-connect-docker.md)
- [Подготовка виртуальной машины SQL в Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

Другие улучшения, появившиеся в SQL Server 2017 г. см. в разделе [новые возможности SQL Server 2017 г](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Ответы на часто задаваемые вопросы см. в разделе [SQL Server в Linux часто задаваемые вопросы о](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
