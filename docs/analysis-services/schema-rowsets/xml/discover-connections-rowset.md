---
title: Набор строк DISCOVER_CONNECTIONS | Документы Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4bb236b6d69199bd4c488c365ba108fc3913f02c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="discoverconnections-rowset"></a>Набор строк DISCOVER_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Предоставляет сведения об использовании ресурсов и действиях, касающиеся соединений, открытых в настоящее время на сервере.  
  
 **Область применения:** табличные модели, многомерные модели  
  
## <a name="rowset-columns"></a>Столбцы наборов строк  
 Набор строк **DISCOVER_CONNECTIONS** содержит следующие столбцы.  
  
|Имя столбца|Индикатор типа|Ограничения|Описание|  
|-----------------|--------------------|------------------|-----------------|  
|**CONNECTION_ID**|**DBTYPE_I4**|Да|Уникальное число, определяющее соединение.|  
|**CONNECTION_USER_NAME**|**DBTYPE_WSTR**|Да|Имя пользователя соединения.|  
|**CONNECTION_IMPERSONATED_USER_NAME**|**DBTYPE_WSTR**|Да|Зарезервировано для последующего использования. Службы Analysis Services всегда возвращают значение NULL для CONNECTION_IMPERSONATED_USER_NAME.|  
|**CONNECTION_HOST_NAME**|**DBTYPE_WSTR**|Да|Имя компьютера, на котором было инициировано соединение.|  
|**CONNECTION_HOST_APPLICATION**|**DBTYPE_WSTR**||Имя приложения, в котором было инициировано соединение.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент открытия соединения.|  
|**CONNECTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Да|Общее затраченное время (в миллисекундах) со времени начала работы соединения.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время запуска на выполнение последней команды на сервере в формате UTC.|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Дата и время сервера в формате UTC на момент завершения выполнения последней команды.|  
|**CONNECTION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**|Да|Общее затраченное время (в миллисекундах) со времени выполнения последней команды.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**|Да|Время простоя (в миллисекундах) с момента открытия соединения.|  
|**CONNECTION_BYTES_SENT**|**DBTYPE_I8**||Накопленное число байтов, отправленных в соединении со времени начала работы соединения.|  
|**CONNECTION_DATA_BYTES_SENT**|**DBTYPE_I8**||Накопленное число байтов данных, отправленных в соединении со времени начала работы соединения.<br /><br /> Данные перемещаются в соединении в упакованном виде; это значение представляет количество отправленных данных в распакованном виде.|  
|**CONNECTION_BYTES_RECEIVED**|**DBTYPE_I8**||Накопленное число байтов, полученных в соединении со времени начала работы соединения.|  
|**CONNECTION_DATA_BYTES_RECEIVED**|**DBTYPE_I8**||Накопленное число байтов данных, полученных в соединении со времени начала работы соединения.<br /><br /> Данные перемещаются в соединении в упакованном виде; это значение представляет количество полученных данных в распакованном виде.|  
  
 Этот набор строк схемы не отсортирован.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Использование ADOMD.NET для возврата набора строк  
 Если для получения метаданных используется ADOMD.NET и набор строк схемы, то для ссылки на объект набора строк схемы в методе GetSchemaDataSet вы можете использовать идентификатор GUID или строку. Дополнительные сведения см. в статье [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 В следующей таблице указываются значения строки и идентификатора GUID, определяющие этот набор строк.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|GUID|a07ccd25-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Соединения|  
  
## <a name="see-also"></a>См. также  
 [XML для аналитики наборы строк схемы](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
