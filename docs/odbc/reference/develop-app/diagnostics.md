---
title: Диагностика | Документы Microsoft
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
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d2db5f46fc157015f035775ac185fb9005de8a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostics"></a>Диагностика
В ODBC возвращают диагностические сведения двумя способами. Код возврата указывает общий успех или сбой функции, а диагностические записи предоставляют подробные сведения о функции. По крайней мере одна диагностическая запись — запись заголовка — возвращается, даже если функция выполняется успешно.  
  
 Диагностические сведения используется во время разработки для перехвата ошибок программирования, например недопустимых дескрипторов и синтаксических ошибок в жестко запрограммированных инструкциях SQL. Используется во время выполнения для перехвата ошибок во время выполнения и предупреждения, такие как усечение данных, нарушения прав доступа и синтаксические ошибки в инструкциях SQL, введенных пользователем.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Коды возврата](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [Диагностические записи](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [Использование SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Реализация SQLGetDiagRec и SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [Примеры диагностической обработки](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
