---
title: "SQLGetStmtOption (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
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
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 601dd559d7bf13d1a12d032d8431a8c3fe0287d4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Один уровень  
  
 Возвращает текущее значение параметра инструкции.  
  
|*FOption*|Возвращает|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-разрядное целое число, — это закладка для номер текущей записи|  
|SQL_ROW_NUMBER|установите 32-разрядное целое число, указывающее позицию текущей строки в результат|  
|SQL_TRANSLATE_DLL|Ошибка: «драйвер не поддерживает»|  
  
 Драйвер ODBC для Visual FoxPro имеет преобразование библиотеки DLL.  
  
 Дополнительные сведения см. в разделе [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) в *справочнике программиста ODBC*.