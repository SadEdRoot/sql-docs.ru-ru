---
title: "Секции (табличные службы SSAS) | Документы Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 708b9bdf-8c0b-4476-809a-8f616be23a58
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 729c24cf80e99f6f0e2596c51bfbc8bdf2490d0d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="partitions"></a>Секции
  Секции разделяют таблицу на логические части. Каждая секция затем может обрабатываться (обновляться) независимо от других секций. Секции, созданные с помощью диалогового окна «секции», в SSDT во время создания модели применяются к базе данных рабочей области модели. При развертывании модели секции, определенные для базы данных рабочей области модели, дублируются в развернутом шаблоне базы данных. После этого можно создать и управлять секции для развернутой модели базы данных с помощью диалогового окна «секции», в среде SSMS.  В этом разделе описываются секций, создаваемых во время создания модели с помощью диалогового окна диспетчера секций в SSDT. Сведения о создании и управлении секциями в развернутой модели см. в разделе [Создание и управление секций табличной модели](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_benefits"></a> Преимущества  
 Секции в табличной модели делят таблицу на объекты логических секций. Затем каждая секция может обрабатываться независимо от других секций. Например, таблица может включать определенные наборы строк, содержащих данные, которые редко изменяются, однако другие наборы строк могут содержать, напротив, часто изменяющиеся данные. В этом случае нет необходимости обрабатывать все данные, если на самом деле нужно обработать только их часть. Секции позволяют разделить данные, обрабатываемые часто, и данные, которые обрабатываются реже.  
  
 При эффективной разработке моделей секции используются для устранения ненужной обработки и последующей нагрузки на процессор на серверах служб Analysis Services. При этом одновременно гарантируется обработка этих данных и частота обновления, достаточная для отражения последних данных из источников данных. Реализация и использование секций во время создания модели может сильно отличаться от реализации и использования секций для развернутых моделей. Может оказаться, что на этапе создания модели придется работать только с подмножеством тех данных, которые в конечном итоге попадут в развернутую модель, и об этом следует помнить.  
  
### <a name="processing-partitions"></a>Обработка секций  
 Для развернутых моделей обработка происходит с помощью SSMS или путем выполнения сценария, который включает команду обработки и задает параметры обработки. При создании моделей с помощью SSDT, операции процесса можно запускать с помощью команды «обработать» из панели инструментов или меню модель. Операция обработки может быть задана для секции, таблицы или для всех элементов.  
  
 При запуске операции обработки устанавливается соединение с источником данных при помощи подключения к данным. Новые данные импортируются в таблицы модели, связи и иерархии строятся или перестраиваются для каждой таблицы, а вычисления в вычисляемых столбцах и мерах выполняются заново.  
  
 В результате дальнейшего деления таблицы на логические секции можно выборочно определить, какие данные, когда и как обрабатываются в каждой секции. При развертывании модели Обработка секций может быть выполнена вручную с помощью диалогового окна «секции», в среде SSMS или с помощью скрипта, исполняющего команду обработки.  
  
### <a name="partitions-in-the-model-workspace-database"></a>Секции в базе данных рабочей области модели  
 Можно создавать новые секции, изменять, merge или удаление разделов с помощью диспетчера секций в SSDT. В зависимости от уровня совместимости при разработке модели, диспетчере секций предоставлены две модели выбора таблиц, строк и столбцов для секции: для табличных моделей 1400 секции определяются с помощью запросов M или в режиме конструктора можно использовать для открытия Редактор запросов. Для табличных 1100 1103, моделей 1200, используйте режим предварительного просмотра таблицы и режим SQL-запросов. 
  
### <a name="partitions-in-a-deployed-model-database"></a>Секции в развернутом шаблоне базы данных  
 При развертывании модели секции для развернутой модели базы данных будет отображаться как объекты базы данных в среде SSMS. Можно создать, изменить, слияния и удалять секции для развернутой модели с помощью диалогового окна «секции», в среде SSMS. Управление секциями в развернутой модели в среде SSMS выходит за рамки этой статьи. Дополнительные сведения об управлении разделов в SSMS см. в разделе [Создание и управление секций табличной модели](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Связанные задачи  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Создание и управление секциями в базе данных рабочей области](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)|Описывает создание и управление секциями в базе данных рабочей области модели с помощью диспетчера секций в SSDT.|  
|[Обработка секций в базе данных рабочей области](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)|Описывает, как обрабатывать (обновлять) секции в базе данных рабочей области модели.|  
  
## <a name="see-also"></a>См. также:  
 [Режим DirectQuery](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [Обработка данных](../../analysis-services/tabular-models/process-data-ssas-tabular.md)  
  
  