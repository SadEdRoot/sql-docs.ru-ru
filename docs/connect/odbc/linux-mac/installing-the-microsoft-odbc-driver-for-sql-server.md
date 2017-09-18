---
title: "Установка Microsoft ODBC Driver for SQL Server для Linux и macOS | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver, installing
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
caps.latest.revision: 69
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8a12dec078ada9d029a70edbe1c35a608c85a538
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="installing-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Установка Microsoft ODBC Driver for SQL Server для Linux и macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этом разделе описывается установка [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux и macOS, а также дополнительные средства командной строки для SQL Server (`bcp` и `sqlcmd`) и разработки заголовков unixODBC.

## <a name="microsoft-odbc-driver-131-for-sql-server"></a>Microsoft ODBC Driver 13.1 for SQL Server 

### <a name="debian-8"></a>Debian 8
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1610"></a>Ubuntu 16.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="os-x-1011-el-capitan-and-macos-1012-sierra"></a>OS X 10.11 (El Capitan) и macOS 10.12 (Сьерра)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install --no-sandbox msodbcsql mssql-tools
```

## <a name="microsoft-odbc-driver-13-for-sql-server"></a>Microsoft ODBC Driver 13 for SQL Server

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su 
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo 
zypper update 
sudo ACCEPT_EULA=Y zypper install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
zypper install unixODBC-utf16-devel
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="offline-installation"></a>Автономная установка
При необходимости или требуют [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 для установки на компьютере без подключения к Интернету, необходимо будет вручную разрешите зависимости пакета. [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 имеет следующие прямой зависимости:
- Ubuntu: libc6 (> = 2.21), libstdc ++ 6 (> = 4.9), libkrb5-3, libcurl3, openssl, debconf (> = 0,5), unixodbc (> = 2.3.1-1)
- Red Hat: glibc, e2fsprogs, krb5 библиотек, openssl, unixODBC
- SuSE: glibc, libuuid1, krb5, openssl, unixODBC

Каждый из этих пакетов в свою очередь имеет собственные зависимости, которые могут или не могут находиться в системе. Общее решение этой проблемы можно найти на распределение пакета диспетчера документации: [Redhat](https://wiki.centos.org/HowTos/CreateLocalRepos), [Ubuntu](http://unix.stackexchange.com/questions/87130/how-to-quickly-create-a-local-apt-repository-for-random-packages-using-a-debian), и [SUSE](https://en.opensuse.org/Portal:Zypper)

Также являются общими для вручную загрузить все зависимые пакеты и поместите их на компьютере, а затем вручную установить каждого пакета, в свою очередь, окончания работы [!INCLUDE[msCoName](../../../includes/msconame_md.md)] пакет драйвера ODBC 13.

#### <a name="redhat-linux-enterprise-server-7"></a>RedHat Linux Enterprise Server 7
  - Скачать последнюю msodbcsql .rpm здесь: http://packages.microsoft.com/rhel/7/prod/
  - Установить зависимости, так и драйвер
  
```
yum install glibc e2fsprogs krb5-libs openssl unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

#### <a name="ubuntu-1604"></a>Ubuntu 16.04
- Скачать последнюю .deb msodbcsql здесь: http://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/ 
- Установить зависимости, так и драйвер 

```
sudo apt-get install libc6 libstdc++6 libkrb5-3 libcurl3 openssl debconf unixodbc unixodbc-dev #install dependencies
sudo dpkg -i msodbcsql_13.1.X.X-X_amd64.deb #install the Driver
```

#### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12
- Скачать последнюю msodbcsql .rpm здесь: http://packages.microsoft.com/sles/12/prod/
- Установка зависимостей и драйвер

```
zypper install glibc, libuuid1, krb5, openssl, unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

После завершения установки пакета, можно убедиться, что [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 можно найти все его зависимости под управлением ldd и просмотреть выходные данные для отсутствующих библиотек:
```
ldd /opt/microsoft/msodbcsql/lib64/libmsodbcsql-*
```
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-linux"></a>Драйвер Microsoft ODBC 11 для SQL Server в Linux

Прежде чем использовать драйвер, установите диспетчер драйверов unixODBC. Подробнее см. в разделе [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) .  

**Действия по установке**  

> [!IMPORTANT]  
> Эти инструкции относятся к `msodbcsql-11.0.2270.0.tar.gz`, который является файл установки для Red Hat Linux. При установке предварительной версии для SUSE Linux файл имеет имя `msodbcsql-11.0.2260.0.tar.gz`.  
  
Порядок установки драйвера

1.  Убедитесь, что у вас есть корневое разрешение.  

2.  Перейдите в каталог, куда загрузки поместил файл с `msodbcsql-11.0.2270.0.tar.gz`. Убедитесь в наличии файла \*.TAR.GZ, который соответствует вашей версии Linux. Чтобы извлечь файлы, выполните следующую команду: **tar xvzf msodbcsql-11.0.2270.0.tar.gz**.  
  
3.  Измените `msodbcsql-11.0.2270.0` каталог должен находиться файл с именем **install.sh**.  
  
4.  Чтобы просмотреть список доступных параметров установки, выполните следующую команду: **./install.sh**.  
  
5.  Создайте резервную копию **odbcinst.ini**. Установка драйвера обновляет **odbcinst.ini**. Файл odbcinst.ini содержит список драйверов, которые зарегистрированы с помощью диспетчера драйверов unixODBC. Чтобы найти расположение файла odbcinst.ini на компьютере, выполните следующую команду: **odbc_config --odbcinstini**.  
  
6.  Перед установкой драйвера выполните следующую команду: **./install.sh verify**. Выходные данные команды **./install.sh verify** показывают, установлено ли на компьютере необходимое программное обеспечение для поддержки драйвера ODBC в Linux.  
  
7.  Когда все готово к установке драйвера ODBC в Linux, выполните команду: **./install.sh install**. Если необходимо указать команду установки (**bin-dir** или **lib-dir**), укажите команду после параметра **install** .  
  
8.  После просмотра лицензионного соглашения введите **YES** для продолжения установки.  
  
Установка помещает драйвер `/opt/microsoft/msodbcsql/11.0.2270.0`. Драйвер и его вспомогательные файлы должны находиться в `/opt/microsoft/msodbcsql/11.0.2270.0`.  
  
Чтобы убедиться, что драйвер Microsoft ODBC в Linux успешно зарегистрирован, выполните команду **odbcinst -q -d -n "ODBC Driver 11 для SQL Server"**.  
  
В статье[Использование существующих примеров MSDN C++ ODBC для драйвера ODBC в Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) показан пример кода, который подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с помощью драйвера ODBC в Linux.  
  
**Удаление**  
  
Драйвер ODBC 11 для Linux можно удалить, выполнив следующие команды:  
  
1.  `rm -f /usr/bin/sqlcmd`
  
2.  `rm -f /usr/bin/bcp`  
  
3.  `rm -rf /opt/microsoft/msodbcsql`  
  
4.  `odbcinst -u -d -n "ODBC Driver 11 for SQL Server"`
  
## <a name="troubleshooting-connection-problems"></a>Устранение неполадок с соединениями  
Если не удается подключиться к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с помощью драйвера ODBC, используйте следующие сведения для выявления проблемы.  
  
Наиболее распространенная проблема подключения связана с наличием двух установленных копий диспетчера драйверов UnixODBC. Поищите libodbc\*.so\*в /usr. Если отображается более одной версии файла, (возможно) установлено несколько диспетчеров драйверов. Приложение может использовать неправильную версию.
  
Включите журнал соединений, изменив вашей `/etc/odbcinst.ini` файл, содержащий следующий раздел со следующими элементами:

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
Если возникает другой сбой подключения и файл журнала отсутствует, (возможно) на компьютере присутствуют две копии диспетчера драйверов. В противном случае выходные данные журнала должны быть аналогичны следующему:  
  
```  
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 13 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
Если кодировка символов ASCII UTF-8, например: 
  
```  
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
Имеется несколько диспетчеров драйверов и приложения используется неправильным, одно или диспетчер драйверов не удалось правильно построить.  
  
Дополнительные сведения об устранении неполадок подключения см. в статьях:  
  
-   [Шаги для устранения неполадок с подключением SQL](http://blogs.msdn.com/b/sql_protocols/archive/2008/04/30/steps-to-troubleshoot-connectivity-issues.aspx)  
  
-   [Устранение проблем с подключением в SQL Server 2005 — часть I](http://blogs.msdn.com/b/sql_protocols/archive/2005/10/22/sql-server-2005-connectivity-issue-troubleshoot-part-i.aspx)  
  
-   [Устранение проблем с подключением в SQL Server 2008 с помощью кольцевого буфера подключения](http://blogs.msdn.com/b/sql_protocols/archive/2008/05/20/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer.aspx)  
  
-   [Средство устранения неполадок проверки подлинности SQL Server](http://blogs.msdn.com/b/sqlsecurity/archive/2010/03/29/sql-server-authentication-troubleshooter.aspx)  
  
-   [Сведения об ошибке (http://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=11001)](http://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=001)  
  
    Номер ошибки, указанный в URL-адресе (11001), следует изменить в соответствии с отображаемой ошибкой.  
  
## <a name="see-also"></a>См. также:

[Установка диспетчера драйверов](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)

[Требования к системе](../../../connect/odbc/linux-mac/system-requirements.md)
