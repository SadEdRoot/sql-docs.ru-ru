---
title: "Состояние свойства (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: efd795c5ae1095a11520215994185987e9cf2b32
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="state-property-ado"></a>Свойство State (ADO)
Указывает все соответствующие объекты, является ли открытое или закрытое состояние объекта. Если объект выполняется асинхронный метод, указывает ли текущее состояние объекта соединения, выполняется или получение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **длинные** значение, которое может быть [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) значение. Значение по умолчанию — **adStateClosed**.  
  
## <a name="remarks"></a>Замечания  
 Можно использовать **состояние** свойства, чтобы определить текущее состояние данного объекта в любое время.  
  
 Объект **состояние** свойство может принимать набор значений. Например, если при выполнении инструкции, это свойство будет объединенное значение **adStateOpen** и **adStateExecuting**.  
  
 **Состояние** свойство доступно только для чтения.  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Объект потока (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>См. также:  
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
