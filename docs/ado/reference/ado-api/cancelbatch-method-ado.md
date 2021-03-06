---
title: Метод CancelBatch (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 241bf36ab3ee4babf8d4e306b9d27a350985cb20
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cancelbatch-method-ado"></a>Метод CancelBatch (ADO)
Отменяет ожидающие пакетного обновления.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Параметры  
 *AffectRecords*  
 Необязательно. [AffectEnum](../../../ado/reference/ado-api/affectenum.md) значение, указывающее, сколько записей **CancelBatch** повлияет на метод.  
  
## <a name="remarks"></a>Замечания  
 Используйте **CancelBatch** метод, чтобы отменить все имеющиеся обновления в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) в пакетном режиме обновления. Если **записей** находится в режиме немедленного обновления, вызов **CancelBatch** без **adAffectCurrent** приводит к ошибке.  
  
 Если изменения применяются к текущей записи или добавляются новые записи, при вызове **CancelBatch**, сначала вызывает ADO [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) метод, чтобы отменить изменения в кэше. После этого все ожидающие изменения в **записей** отменяются.  
  
 Текущая запись может быть неопределенной после **CancelBatch** вызвать, особенно в том случае, если были в процессе добавления новой записи. По этой причине рекомендуется задать положение текущей записи в известном расположении в **записей** после **CancelBatch** вызова. Например, вызов [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) метод.  
  
 Если попытка отменить ожидающие обновления завершается неудачей из-за конфликта с базовыми данными (например, если запись была удалена другим пользователем), поставщик возвращает предупреждения, чтобы [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекции, но не останавливается выполнение программы. Ошибка во время выполнения возникает только в том случае, если запрошенными записями конфликтуют. Используйте [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство (**adFilterAffectedRecords**) и [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) свойство для поиска записей с конфликтами.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [UpdateBatch и пример CancelBatch методы (Visual Basic)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch и CancelBatch примере методы (VC ++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Метод Cancel (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Метод Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Метод CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Метод CancelUpdate (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Метод Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [Свойство LockType (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
