---
title: Свойство CommandType (ADO) | Документы Microsoft
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
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2008231e7daba12fbbabf81ce5e0e6b79b41cd80
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="commandtype-property-ado"></a>Свойство CommandType (ADO)
Указывает тип [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает один или несколько [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) значения.  
  
> [!NOTE]
>  Не используйте **CommandTypeEnum** значения **adCmdFile** или **adCmdTableDirect** с **CommandType**. Эти значения можно использовать только как параметры с [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="remarks"></a>Замечания  
 Используйте **CommandType** свойство оптимизировать вычисление [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) свойство.  
  
 Если **CommandType** значение свойства установлено значение по умолчанию **adCmdUnknown**, могут возникнуть снижение производительности, так как ADO необходимо выполнять вызовы к поставщику для определения  **CommandText** свойство является инструкции SQL, имя таблицы или хранимой процедуры. Если вы знаете, какой тип команды вы используете, задание **CommandType** свойство предписывает ADO, чтобы перейти на соответствующий код. Если **CommandType** свойства не соответствует типу команды в **CommandText** свойства, произошла ошибка при вызове [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление примере свойства (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
