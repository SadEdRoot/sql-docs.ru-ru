---
title: Метод setFetchDirection (SQLServerStatement) | Документы Microsoft
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
- SQLServerStatement.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 18176517-2fb3-4266-924d-0f01253083d2
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e52228afe441935952815a0070403ad9fe9be12f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setfetchdirection-method-sqlserverstatement"></a>Метод setFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Предоставляет [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] указание относительно направления, в котором результирующая будут обрабатываться набора строк.  
  
> [!NOTE]  
>  Драйвер JDBC в настоящее время пропускает указание, определенное этим методом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setFetchDirection(int nDir)  
```  
  
#### <a name="parameters"></a>Параметры  
 *nDir*  
  
 **Int** , указывающее направление обработки строк, который может быть одним из следующих значений:  
  
 FETCH_FORWARD  
  
 FETCH_REVERSE  
  
 FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setFetchDirection указывается с помощью метода setFetchDirection в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
