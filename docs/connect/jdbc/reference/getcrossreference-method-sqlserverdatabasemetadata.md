---
title: Метод getCrossReference (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.getCrossReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 099dd0bf-b017-479d-9696-f5b06f4c6bf9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8876c49e809cf1bd941937c294d6122bb3c7d3f3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getcrossreference-method-sqlserverdatabasemetadata"></a>Метод getCrossReference (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов внешнего ключа в заданной таблице внешнего ключа, который ссылается на столбцы первичного ключа заданной таблицы первичного ключа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getCrossReference(java.lang.String cat1,  
                                            java.lang.String schem1,  
                                            java.lang.String tab1,  
                                            java.lang.String cat2,  
                                            java.lang.String schem2,  
                                            java.lang.String tab2)  
```  
  
#### <a name="parameters"></a>Параметры  
 *cat1*  
  
 Объект **строка** , содержащее имя каталога таблицы, которая содержит первичный ключ.  
  
 *schem1*  
  
 Объект **строка** , содержащее имя схемы таблицы, которая содержит первичный ключ.  
  
 *tab1*  
  
 Объект **строка** , содержащее имя таблицы, которая содержит первичный ключ таблицы.  
  
 *Cat2*  
  
 Объект **строка** , содержащее имя каталога таблицы, содержащей внешний ключ.  
  
 *schem2*  
  
 Объект **строка** , содержащее имя схемы таблицы, содержащей внешний ключ.  
  
 *tab2*  
  
 Объект **строка** , содержащее имя таблицы, содержащей внешний ключ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getCrossReference указывается с помощью метода getCrossReference в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getCrossReference возвращает результирующий набор будет содержать следующие сведения:  
  
|Название|Тип|Описание|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|Имя каталога, содержащего таблицу первичного ключа.|  
|PKTABLE_SCHEM|**String**|Имя схемы таблицы первичного ключа.|  
|PKTABLE_NAME|**String**|Имя таблицы первичного ключа.|  
|PKCOLUMN_NAME|**String**|Имя столбца первичного ключа.|  
|FKTABLE_CAT|**String**|Имя каталога, содержащего таблицу внешнего ключа.|  
|FKTABLE_SCHEM|**String**|Имя схемы таблицы внешнего ключа.|  
|FKTABLE_NAME|**String**|Имя таблицы внешнего ключа.|  
|FKCOLUMN_NAME|**String**|Имя столбца внешнего ключа.|  
|KEY_SEQ|**короткий**|Порядковый номер столбца в первичном ключе из нескольких столбцов.|  
|UPDATE_RULE|**короткий**|Действие, применяемое к внешнему ключу, если операцией SQL является операция обновления. Может иметь одно из следующих значений.<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**короткий**|Действие, применяемое к внешнему ключу, если операцией SQL является операция удаления. Может иметь одно из следующих значений.<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|Имя внешнего ключа.|  
|PK_NAME|**String**|Имя первичного ключа.|  
|DEFERRABILITY|**короткий**|Указывает, можно ли отложить вычисление ограничения внешнего ключа до фиксации. Может иметь одно из следующих значений.<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getCrossReference см. в разделе «sp_fkeys (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getCrossReference для возврата сведений о связи первичного и внешнего ключа между таблицами Person.Contact и HumanResources.Employee в [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
```  
public static void executeGetCrossReference(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCrossReference("AdventureWorks", "Person", "Contact", null, "HumanResources", "Employee");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
