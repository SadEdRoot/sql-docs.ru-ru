---
title: Метод storesUpperCaseIdentifiers | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.storesUpperCaseIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a622b748-d10b-4f02-afe3-fba4a5bca17b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16a32c65682c651c5b8fd6469501666afaf0f2bd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="storesuppercaseidentifiers-method-sqlserverdatabasemetadata"></a>Метод storesUpperCaseIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, учитывает ли база данных регистр символов для идентификаторов SQL в смешанном регистре, не заключенных в кавычки, и сохраняет их в верхнем регистре.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean storesUpperCaseIdentifiers()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если идентификаторы хранятся в верхнем регистре. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод storesUpperCaseIdentifiers указывается с помощью метода storesUpperCaseIdentifiers в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
