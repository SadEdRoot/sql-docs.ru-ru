---
title: Отслеживание | Документы Microsoft
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
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ea7116433a06e12a8df40a0b09d214ce0e8a2c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="dynamic-tracing"></a>Отслеживание
Трассировку можно включить или отключить в любой момент запуска приложения. Это позволяет приложению для любого количества вызовов функции трассировки.  
  
 Переменная **ODBCSharedTraceFlag** устанавливается для включения трассировки динамически. Эта переменная используется совместно все работающие копии диспетчера драйверов. Любое приложение присваивает этой переменной, включена ли трассировка для всех приложений ODBC, которые в настоящее время запущен. Чтобы включить трассировку off при включении динамической трассировки, приложение вызывает **SQLSetConnectAttr** SQL_ATTR_TRACE присваивается SQL_TRACE_OFF. Этот вызов станет выключение трассировки только для этого приложения. Приложения, которые связаны с библиотекой Odbc32.lib можно изменять использование этой переменной. Данные трассировки могут отображаться в окне, в режиме реального времени, вместо файла трассировки, который должен быть открыт после сеанса ODBC. Элементы управления можно добавить на экран приложения, чтобы включить или отключить трассировку на будут.  
  
 Трассировки, библиотеки DLL, поставляемых с ODBC 3 *.x* не является потокобезопасным. Не гарантируется, что файл журнала записывается правильно при включенной трассировке глобальные (переменная **ODBCSharedTraceFlag** задано) и более чем одним приложением записывает в файл трассировки в то же время. Это условие не возвращает ошибку.
