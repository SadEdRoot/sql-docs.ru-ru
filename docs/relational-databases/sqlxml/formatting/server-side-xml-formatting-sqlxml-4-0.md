---
title: Форматирование серверные XML (SQLXML 4.0) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dd37f50bb838717d9a245b038f624dee57bbf7d4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Форматирование XML-кода на сервере (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе содержится информация о форматировании на серверной стороне XML-документов из наборов строк, которые создаются при выполнении запросов к базе данных в Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно помещать XML-документы в таблицы базы данных и получать XML-документы из них. Для получения XML-документа в запросе SELECT используется расширение FOR XML.  
  
 Например, предположим, клиентское приложение выполняет команду [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] состоит из следующих [!INCLUDE[tsql](../../../includes/tsql-md.md)] запроса:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 Сервер выполняет запрос в два шага. Во-первых, сервер выполняет следующую инструкцию SELECT:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Затем сервер применяет преобразование FOR XML к сформированному набору строк. Результирующий XML-документ затем отправляется клиенту в виде набора строк, состоящего из одного столбца. В данной документации этот процесс называется форматированием XML на стороне сервера.  
  
 На стороне сервера можно указать следующие режимы при помощи предложения FOR XML:  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 Дополнительные сведения о предложении FOR XML см. в разделе [конструирование XML используя FOR XML](../../../relational-databases/xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура форматирования XML, клиентские и серверные &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Форматирование XML на стороне клиента &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML (SQL Server)](../../../relational-databases/xml/for-xml-sql-server.md)  
  
  
