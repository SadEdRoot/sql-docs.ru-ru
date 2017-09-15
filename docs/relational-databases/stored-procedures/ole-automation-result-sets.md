---
title: "Результирующие наборы OLE-автоматизации | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-ole
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [SQL Server], OLE Automation
- two-dimensional arrays
- one-dimensional arrays
- result sets [SQL Server], OLE Automation
- OLE Automation [SQL Server], result sets
- arrays [SQL Server]
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8b3cf49bb4116a3cbf8bf58c327cdb6af5c11468
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="ole-automation-result-sets"></a>Результирующие наборы OLE-автоматизации
  Если свойство или метод OLE-автоматизации возвращает данные в одномерный или двухмерный массив, то массив возвращается клиенту как результирующий набор следующего вида.  
  
-   Одномерный массив возвращается клиенту как результирующий набор, состоящий из одной строки, в которой число столбцов соответствует количеству элементов массива. Например, массив array(10) возвращается как одна строка с 10 столбцами.  
  
-   Двумерный массив возвращается клиенту в виде результирующего набора с числом столбцов, равным числу элементов первого измерения массива, и числом строк, равным числу элементов второго измерения массива. Например, массив array(2,3) возвращается как 2 столбца в 3 строках.  
  
 Если значение возвращаемого свойства или метода является массивом, процедура sp_OAGetProperty или sp_OAMethod возвращает результирующий набор клиенту. (Выходные параметры метода не могут быть массивами.) Эти процедуры просматривают все значения в массиве для определения подходящих типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и их длин для каждого столбца результирующего набора. Для каждого отдельного столбца эти процедуры используют тип и длину данных, необходимые для представления всех значений данных этого столбца.  
  
 Если все значения данных в столбце имеют один и тот же тип данных, этот тип используется для всего столбца. Когда значения данных в столбце принадлежат к различным типам данных, тип данных всего столбца определяется, как указано в следующей таблице. В следующей таблице определите положение одного типа данных на оси строк слева и другого типа данных на оси столбцов сверху. В пересечении строки и столбца описывается тип данных столбца результирующего набора.  
  
||||||||  
|-|-|-|-|-|-|-|  
||**int**|**float**|**money**|**datetime**|**varchar**|**nvarchar**|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="related-content"></a>См. также  
 [Хранимые процедуры OLE-автоматизации (Transact-SQL)](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
 [Параметр конфигурации сервера «Ole Automation Procedures»](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  