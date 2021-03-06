---
title: SQLSetConnectOption (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
- SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf6a0f1a2bd6e0275f58ca816a18739b3210d383
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: частичная  
  
 Соответствия ODBC API: 1 уровень  
  
 Задает параметры, которые управляют аспектами подключений. Эта функция поддерживается частично: драйвер поддерживает все значения для *fOption* аргумент, но не поддерживает некоторые *vParam* значения для *fOption* аргумент SQL_TXN_ISOLATION.  
  
 В следующей таблице описаны только те аргументы, поведение, характерное для драйвера ODBC для Visual FoxPro реализация **SQLSetConnectOption**.  
  
|*fOption*|Замечания|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|При выборе SQL_AUTOCOMMIT_OFF ваше приложение должно явно фиксации или отката транзакции с [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); драйвер ODBC для Visual FoxPro не фиксирует автоматически выполнении инструкции после завершения. Драйвер начать транзакцию, при выполнении инструкции.|  
|SQL_CURRENT_QUALIFIER|Может быть полным [базы данных](../../odbc/microsoft/visual-foxpro-terminology.md) имя или полный путь к файлу каталог, содержащий ноль или более [свободных таблиц](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SQL_LOGINTIMEOUT|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_CURSORS|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_PACKET_SIZE|Возвращает ошибку «Драйвер не поддерживает».|  
|SQL_TXN_ISOLATION|Драйвер допускает использование только SQL_TXN_READ_COMMITTED.<br /><br /> Следующие *vParam*s не поддерживаются:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Дополнительные сведения см. в разделе [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) в *справочнике программиста ODBC*.
