---
title: CollectionAggregate (тип данных geometry) | Документы Майкрософт
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- CollectionAggregate method (geometry)
ms.assetid: b7c85d59-c841-4b7f-9d46-8b4b7f2a3afe
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fbe90ac3439cd4502128a1ac6de3d85db904b85a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="collectionaggregate-geometry-data-type"></a>CollectionAggregate (тип данных geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Создает экземпляр **GeometryCollection** из набора типов **geometry**.
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CollectionAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Аргументы  
 *geometry_operand*  
 Столбец типа **geometry**, представляющий набор объектов **geometry**, которые будут указаны в экземпляре **GeometryCollection**.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 Тип возвращаемых данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
## <a name="exceptions"></a>Исключения  
 Вызывает исключение `FormatException` при наличии недопустимых входных значений. См. раздел [STIsValid (тип данных geometry)](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md).  
  
## <a name="remarks"></a>Remarks  
 Метод возвращает значение **NULL**, если входные данные пусты или содержат различные идентификаторы пространственных ссылок. См. раздел [Идентификаторы пространственных ссылок (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Метод не обрабатывает входные значения **NULL**.  
  
> [!NOTE]  
>  Метод возвращает значение **NULL**, если входными являются значения **NULL**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается экземпляр `GeometryCollection`, содержащий `CurvePolygon` и `Polygon`.  
  
 ```
 -- Setup table variable for CollectionAggregate example  
 DECLARE @Geom TABLE  
 (  
 shape geometry,  
 shapeType nvarchar(50)  
 )  
 INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'),  
 ('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle');  
 -- Perform CollectionAggregate on @Geom.shape column  
 SELECT geometry::CollectionAggregate(shape).ToString()  
 FROM @Geom;
 ```  
  
## <a name="see-also"></a>См. также:  
 [Расширенные статические геометрические методы](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

