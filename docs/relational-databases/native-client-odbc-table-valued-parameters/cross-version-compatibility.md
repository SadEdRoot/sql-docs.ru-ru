---
title: Совместимость версий | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8da04e9ed25808b83c5c63bcb6906770dd1e53cc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cross-version-compatibility"></a>Совместимость версий
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Конфликты между версиями могут происходить, если экземпляры клиента или сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующие [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], участвуют в обработке возвращающих табличное значение параметров.  
  
 В общем случае функциональные возможности возвращающих табличное значение параметров доступны только клиентам [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (с помощью собственного клиента SQL Server версии 10.0) или более поздних версий, соединенных с серверами [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии). Новые столбцы в результирующих наборов функции каталога появятся только при подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) сервера.  
  
 Если клиентское приложение, скомпилированное с помощью собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущей версии, выполняет инструкции, которые ожидают возвращающие табличное значение параметры, то сервер определяет это условие как ошибку преобразования данных, и ODBC возвращает код SQLSTATE 07006 и сообщение «Нарушение атрибута ограниченного типа данных».  
  
 Если клиентское приложение, скомпилированное с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент версии 10.0 или более поздней версии пытается использовать возвращающие табличные значения параметров при подключении к экземпляру сервера более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент обнаружит это и SQLBindCol, SQLBindParameter, SQLSetDescFields и SQLSetDescRec вызовы завершатся ошибкой с кодом SQLSTATE 07006 и сообщением «Ограниченные (версия SQL Server для этого соединения не поддерживает возвращающие табличные значения параметров) нарушение атрибута типа данных».  
  
## <a name="see-also"></a>См. также  
 [Возвращающие табличные значения параметров &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
