---
title: Объект процедуры (ADOX) | Документы Microsoft
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
- Procedure
helpviewer_keywords:
- Procedure object [ADOX]
ms.assetid: 927bcf3e-32f5-4a80-98d3-600779f0732e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd25aeeac87c3bd3bc8aa7b1405815f987d44266
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="procedure-object-adox"></a>Объект процедуры (ADOX)
Представляет хранимую процедуру. При использовании в сочетании с ADO [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта, **процедура** объект может использоваться для добавления, удаления или изменения хранимой процедуры.  
  
## <a name="remarks"></a>Замечания  
 **Процедура** позволяет создать хранимую процедуру без необходимости знать или используйте синтаксис «CREATE PROCEDURE» поставщика.  
  
 С помощью свойств **процедура** объекта, вы можете:  
  
-   Определения процедуры с [имя](../../../ado/reference/adox-api/name-property-adox.md) свойства.  
  
-   Укажите ADO **команда** объекта, который может использоваться для создания или выполнения процедуры с [команда](../../../ado/reference/adox-api/command-property-adox.md) свойство.  
  
-   Возвращает сведения о дате с [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) и [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) свойства.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Procedure](../../../ado/reference/adox-api/procedure-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Команда и пример свойства CommandText (Visual Basic)](../../../ado/reference/adox-api/command-and-commandtext-properties-example-vb.md)   
 [Коллекция параметров, пример команды свойства (Visual Basic)](../../../ado/reference/adox-api/parameters-collection-command-property-example-vb.md)   
 [Процедуры добавления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Процедуры удаления пример метода (Visual Basic)](../../../ado/reference/adox-api/procedures-delete-method-example-vb.md)   
 [Коллекция Procedures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
