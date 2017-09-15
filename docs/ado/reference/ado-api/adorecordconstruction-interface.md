---
title: "Интерфейс ADORecordConstruction | Документы Microsoft"
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
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3966038215e1d26828d60b739ac6060859eabd67
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="adorecordconstruction-interface"></a>Интерфейс ADORecordConstruction
**ADORecordConstruction**интерфейса используется для создания объекта ADO **запись** объектов из поставщика OLE DB **строки** объекта в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Доступный только на запись.<br />Задает контейнер OLE DB **строки** объект на этом ADO **записи** объекта.|  
|[Строки](../../../ado/reference/ado-api/row-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **строки** объекта из/в этом ADO **записи** объекта.|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Замечания  
 Получает OLE DB **строки** объекта (`pRow`), построении ADO **записи** объекта (`adoR`), сумм следующие три основные операции:  
  
1.  Создание объекта ADO **записи** объекта:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Запрос **IADORecordConstruction** интерфейс **записи** объекта:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Вызовите **IADORecordConstruction::put_Row** метод свойство, чтобы задать OLE DB **строки** объекта ADO **записи** объекта:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 Итоговые **adoR** теперь представляет объект ADO **запись** объекта, построенным на основе OLE DB **строки** объекта.  
  
 ADO **запись** объект также может быть создан из контейнера OLE DB **строки** объекта.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 и более поздних версий  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4