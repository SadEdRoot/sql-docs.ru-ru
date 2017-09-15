---
title: "Элемент таблицы для схемы (DTA) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8786081dfd306de3fdfcf3d407854e49061548a2
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="table-element-for-schema-dta"></a>Элемент Table описания схемы (DTA)
  Указывает таблицу для настройки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>Атрибуты элемента  
  
|Attribute|Описание|  
|---------------|-----------------|  
|**NumberOfRows**|Необязательно. Целое число, позволяющее имитировать таблицы различных размеров.|  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|**string**, от 1 до 255 символов|  
|**Значение по умолчанию**|Нет.|  
|**Применяемость**|Необязательно. Перечисляет необходимое число таблиц для рабочей нагрузки.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент schema описания базы данных &#40; DTA &#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**Дочерние элементы**|[Элемент Name описания таблицы &#40; DTA &#41;](../../tools/dta/name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Замечания  
 Если элемент **Table** не указан, помощник по настройке ядра СУБД считает все таблицы в указанной базе данных доступными для настройки.  
  
## <a name="example"></a>Пример  
 Пример использования см. в разделе [Элемент Server (DTA)](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  