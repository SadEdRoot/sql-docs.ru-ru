---
title: Записи реестра (драйвер ODBC для Visual FoxPro) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- registry keys [ODBC]
- Visual FoxPro ODBC driver [ODBC], registry entries
- keys [ODBC]
- FoxPro ODBC driver [ODBC], registry entries
ms.assetid: 1a63d92d-ca3a-46ae-911f-6788292c801e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a8a742aeb4f2290ef7f76410d689e15afec5c6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="registry-entries-visual-foxpro-odbc-driver"></a>Записи реестра (драйвер ODBC для Visual FoxPro)
При установке драйвера ODBC для Visual FoxPro, программа установки обновляет в системном реестре в разделе реестра HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCInst.ini, чтобы добавить новый ключ с именем драйвера Microsoft Visual FoxPro. В данном разделе добавляются со значениями, описанными в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|APILevel|REG_SZ|"1"|  
|ConnectFunctions|REG_SZ|«YYN»|  
|Драйвер|REG_SZ|Путь к файлу vfpodbc.dll|  
|DriverODBCVer|REG_SZ|"02.50"|  
|FileExtns|REG_SZ|«*.dbf,\*.cdx,\*.fpt»|  
|FileUsage|REG_SZ|"1"|  
|Программа установки|REG_SZ|Путь к файлу vfpodbc.dll|  
|SQLLevel|REG_SZ|"0"|  
  
 Программа установки также добавляет раздел «Visual FoxPro Files», представляющему драйвер Visual FoxPro по умолчанию для раздела HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini вашей системы. В этом разделе программа установки добавляет со значениями, описанными в следующей таблице.  
  
|Имя значения|Тип значения|Значение|  
|----------------|----------------|-----------|  
|Драйвер|REG_SZ|Путь к файлу vfpodbc.dll|  
  
 Каждый раз при добавлении источника данных Visual FoxPro ODBC в конфигурацию ODBC новый ключ добавляется имя для этого источника данных. Значения для источника данных, которым соответствуют значения, заданные в **установки Visual FoxPro ODBC** диалоговое окно, как показано в следующей таблице.  
  
|Имя параметра (ключевое слово)|Тип значения|Значение|  
|----------------------------|----------------|-----------|  
|Разобрать по копиям|REG_SQ|Любой поддерживаемый упорядоченной последовательности|  
|Описание|REG_SZ|Описание источника данных пользователя|  
|Драйвер||Путь к файлу vfpodbc.dll|  
|Монопольно||"Да" или "Нет".|  
|BackgroundFetch||"Да" или "Нет".|  
|SourceDB|REG_SZ|Путь. Файл DBC|  
|Тип источника|REG_SZ|«DBC» или «DBF»|  
  
 Эти сведения не доступ напрямую. Если добавить, изменить или удалить источник данных любого администрирования реестра будет выполняться администратором ODBC.  
  
 Некоторые из этих ключевых слов и значений можно использовать в качестве параметров [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) функции ODBC API.
