---
title: 'Шаг 2: Инициализируйте приложение | Документы Microsoft'
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
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85dff871a4b81551c699acc934aedb14c4f1725f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="step-2-initialize-the-application"></a>Шаг 2: Инициализации приложения
Второй шаг — для инициализации приложения, как показано на следующем рисунке. Именно здесь выполняемые операции зависит от приложения.  
  
 ![Показывает, инициализация ODBC приложения](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 На этом этапе обычно используется **SQLGetInfo** для обнаружения возможностей драйвера. Дополнительные сведения см. в разделе [рассмотрении функции базы данных для использования](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Все приложения должны выделить дескриптор инструкции с **SQLAllocHandle**, и задайте атрибуты инструкции, такие как тип курсора, во многих приложениях **SQLSetStmtAttr**. Дополнительные сведения см. в разделе [выделения дескриптор инструкции](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) и [атрибуты инструкции](../../../odbc/reference/develop-app/statement-attributes.md).
