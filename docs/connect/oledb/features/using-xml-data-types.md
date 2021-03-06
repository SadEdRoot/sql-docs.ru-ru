---
title: Использование типов данных XML | Документы Microsoft
description: Использование типов данных XML с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- IRowsetUpdate interface
- data access [OLE DB Driver for SQL Server], xml data type
- OLE DB Driver for SQL Server schema rowsets
- PROVIDER_TYPES rowset
- IColumnsInfo interface
- IRowsetFind interface
- IColumnsRowset interface
- PROCEDURE_PARAMETERS rowset
- MSOLEDBSQL, XML
- xml data type [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, XML
- IRowset interface
- ISequentialStream interface
- ISSCommandWithParameters interface
- SS_XMLSCHEMA rowset
- OLE DB Driver for SQL Server OLE DB interfaces
- XML [SQL Server], OLE DB Driver for SQL Server
- COLUMNS rowset
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f36165da3be9c540166486059cdc0ee150532657
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-xml-data-types"></a>Использование типов данных XML
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]представленные **xml** тип данных, который позволяет хранить XML-документы и фрагменты в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных. **Xml** тип данных является встроенным типом данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]и в чем-то напоминающий другие встроенные типы, такие как **int** и **varchar**. Как и другие встроенные типы можно использовать **xml** как тип столбца при создании таблицы, как тип переменной, тип параметра или типа возвращаемого функцией значения; или в функциях CAST и CONVERT типа данных.  
  
## <a name="programming-considerations"></a>Замечания по программированию  
 Язык XML может описывать сам себя в том смысле, что он может по желанию включать заголовок XML, описывающий кодировку документа, например:  
  
 `<?xml version="1.0" encoding="windows-1252"?><doc/>`  
  
 Стандарт языка XML описывает, как обработчик XML определяет кодировку, использованную в документе, по первым нескольким байтам документа. Существует возможность, что кодировка, заданная приложением, не совпадет с кодировкой, заданной в документе. Для документов, переданных как связанные параметры, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обрабатывает XML как двоичные данные, поэтому никаких преобразований не производится, и синтаксический анализатор XML может без проблем использовать кодировку, указанную в документе. Однако для XML-данных, привязанных как WSTR, приложение должно проверить, что документ имеет кодировку Юникод. Это возможно, придется загрузить документ в виде модели DOM, Изменение кодировки Юникод и сериализовать документ. Если этого не сделать, может произойти порча данных, полученный в XML недопустим или поврежден.  
  
 Возможен также конфликт, если XML задается в виде литерала. Например, приведенные ниже инструкции являются недопустимыми.  
  
 `INSERT INTO xmltable(xmlcol) VALUES('<?xml version="1.0" encoding="UTF-16"?><doc/>')`  
  
 `INSERT INTO xmltable(xmlcol) VALUES(N'<?xml version="1.0" encoding="UTF-8"?><doc/>')`  
  
## <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server 
 DBTYPE_XML — это новый тип данных, определенных в XML в драйвер OLE DB для SQL Server. Кроме того, к XML-данным можно получить доступ через существующие типы OLE DB: DBTYPE_BYTES, DBTYPE_WSTR, DBTYPE_BSTR, DBTYPE_XML, DBTYPE_STR, DBTYPE_VARIANT и DBTYPE_IUNKNOWN. Данные, хранящиеся в столбцах типа XML можно получить из столбца в драйвер OLE DB для SQL Server набора строк в следующих форматах:  
  
-   Текстовая строка.  
  
-   **ISequentialStream**  
  
> [!NOTE]  
>  Драйвер OLE DB для SQL Server не поддерживает чтения SAX, но **ISequentialStream** можно легко передать объектам SAX и DOM в MSXML.  
  
 **ISequentialStream** следует использовать для извлечения больших XML-документов. При работе с типами больших значений в XML используются те же технологии, что и для работы с другими типами больших значений. Дополнительные сведения см. в разделе [с помощью типов больших значений](../../oledb/features/using-large-value-types.md).  
  
 Данные, хранящиеся в столбцах типа XML в наборе строк, можно также получить, вставлены или обновлены приложением через обычные интерфейсы, такие как **IRow::GetColumns**, **IRowChange::SetColumns**, и **ICommand::Execute**. Аналогично случаю извлечения прикладной программы можно передать строку текста или **ISequentialStream** драйвера OLE DB для SQL Server.  
  
> [!NOTE]  
>  Для отправки XML-данных в строковом формате через **ISequentialStream** интерфейса, необходимо получить **ISequentialStream** , задав DBTYPE_IUNKNOWN и задать его *pObject* аргумент значение null в привязке.  
  
 Если полученные XML-данные усечены из-за недостаточного размера буфера потребителя, возвращаемое значение длины может быть равно 0xffffffff — это означает, что длина данных неизвестна. Такое поведение согласуется с его реализацией как тип данных, которое загружается на клиент не отправляет сведения о длине до фактических данных. В некоторых случаях может возвращаться фактическую длину при помещено в буфер поставщика всего значения, такие как **IRowset::GetData** и где выполняется преобразование данных.  
  
 XML-данные, переданные в SQL Server, сервер обрабатывает как двоичные данные. Это предотвращает преобразование данных и позволяет средству синтаксического анализа XML автоматически обнаружить кодировку XML. Это позволяет принимать в качестве входных данных для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более широкий диапазон XML-документов (например, документы в кодировке UTF-8).  
  
 Если входные данные XML привязаны как тип DBTYPE_WSTR, приложение должно убедиться, что данные уже находятся в кодировке Юникод, чтобы предотвратить всякую возможность повреждения данных ненужными преобразованиями.  
  
### <a name="data-bindings-and-coercions"></a>Привязки данных и приведение типов  
 В следующей таблице описаны привязка и приведение, которая возникает, когда с помощью указанных данных типов с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **xml** тип данных.  
  
|Тип данных|На сервер<br /><br /> **XML**|На сервер<br /><br /> **Отличном от XML**|С сервера<br /><br /> **XML**|С сервера<br /><br /> **Отличном от XML**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_XML|Пропуск<sup>6,7</sup>|Ошибка<sup>1</sup>|ОК<sup>11, 6</sup>|Ошибка<sup>8</sup>|  
|DBTYPE_BYTES|Пропуск<sup>6,7</sup>|N/A<sup>2</sup>|ОК <sup>11, 6</sup>|N/A <sup>2</sup>|  
|DBTYPE_WSTR|Пропуск<sup>6,10</sup>|N/A <sup>2</sup>|ОК<sup>4, 6, 12</sup>|N/A <sup>2</sup>|  
|DBTYPE_BSTR|Пропуск<sup>6,10</sup>|N/A <sup>2</sup>|OK <sup>3</sup>|N/A <sup>2</sup>|  
|DBTYPE_STR|ОК<sup>6, 9, 10</sup>|N/A <sup>2</sup>|ОК<sup>5, 6, 12</sup>|N/A <sup>2</sup>|  
|DBTYPE_IUNKNOWN|Байтовый поток через **ISequentialStream**<sup>7</sup>|N/A <sup>2</sup>|Байтовый поток через **ISequentialStream**<sup>11</sup>|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Пропуск<sup>6,7</sup>|N/A <sup>2</sup>|Недоступно|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Пропуск<sup>6,10</sup>|N/A <sup>2</sup>|OK<sup>3</sup>|N/A <sup>2</sup>|  
  
 <sup>1</sup>Если сервера тип, отличный от DBTYPE_XML, указанном с помощью **ICommandWithParameters::SetParameterInfo** и типом метода доступа задан DBTYPE_XML, при выполнении инструкции возникает ошибка (DB_E_ERRORSOCCURRED, состояние параметра будет DBSTATUS_E_BADACCESSOR); в противном случае данные отправляются на сервер, но сервер возвращает ошибку, указывающую, что имеется не неявное преобразование из XML в тип данных параметра.  
  
 <sup>2</sup>выходит за рамки данной статьи.  
  
 <sup>3</sup>формат — UTF-16, не порядка следования байтов (BOM) отсутствует кодировка не указана, не завершаются нулем.  
  
 <sup>4</sup>имеет формат UTF-16, метка BOM, не кодировка не указана, нулем.  
  
 <sup>5</sup>формат — многобайтовых символов в кодовую страницу клиента с помощью завершающий символ null. Преобразование из сервера предоставленного Юникод может вызвать повреждение данных, поэтому не рекомендуется использовать этой привязки.  
  
 <sup>6</sup>может использоваться by_ref.  
  
 <sup>7</sup>данные UTF-16 должны начинаться с метки порядка БАЙТОВ. Если метка отсутствует, то кодировка может быть неправильно распознана сервером.  
  
 <sup>8</sup>проверка может происходить во время создания метода доступа или во время получения. Значение ошибки — DB_E_ERRORSOCCURRED, для привязки устанавливается состояние DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>9</sup>данные преобразуются в Юникод с использованием кодовой страницы клиента перед его отправкой на сервер. Если кодировка документа не соответствует клиентской кодовой страницы, может произойти повреждение данных, поэтому такую привязку крайне нежелательно.  
  
 <sup>10</sup>Спецификации всегда добавляется к данным, отправляемых на сервер. Если данные уже запущен со Спецификацией, в начале буфера будет две спецификации. Сервер использует первую метку для распознавания кодировки как UTF-16, а затем отбрасывает ее. Вторая метка порядка следования байтов рассматривается как символ неразрывного пробела нулевой ширины.  
  
 <sup>11</sup>формат UTF-16 без кодирования спецификация Спецификации является добавляется в данные, полученные от сервера. Если сервер вернул пустую строку, метка порядка байтов все равно будет возвращена приложению. Если длина буфера составляет нечетное число байтов, данные усекаются правильно. Если все значение возвращается по фрагментам данных, их можно объединить для восстановления правильного значения.  
  
 <sup>12</sup>Если длина буфера меньше двух символов — иными словами, не хватает места для нулем — ошибка переполнения.  
  
> [!NOTE]  
>  Для XML-данных со значением NULL не возвращаются никакие данные.  
  
 Согласно стандарту XML, XML-документы в кодировке UTF-16 должны начинаться с метки порядка следования байтов (BOM); в UTF-16 это код символа 0xFEFF. При работе с привязками типов WSTR и BSTR, драйвер OLE DB для SQL Server не требует или добавить Спецификацию как кодировка задана привязкой. При работе с привязками типов BYTES, XML и IUNKNOWN целью является предоставить возможности для наиболее простого взаимодействия с другими обработчиками XML и хранилищами данных. В этом случае Спецификации должны присутствовать с XML в кодировке UTF-16, а приложения должны не важна на самом деле кодировка, так как большинство обработчиков XML (включая SQL Server) выводит кодировку по нескольким первым байтам значения. XML-данных, полученный от драйвер OLE DB для SQL Server с помощью БАЙТОВ, XML, или привязки IUNKNOWN, всегда закодированы в UTF-16 с BOM и без внедренной декларации кодировки.  
  
 Преобразование данных основными службами OLE DB (**IDataConvert**) не применяются к типу DBTYPE_XML.  
  
 Проверка производится при отсылке данных на сервер. Проверки на стороне клиента и кодирование изменения должны обрабатываться приложением. Рекомендуется не обрабатывать XML-данные непосредственно, но вместо этого следует использовать чтения DOM или SAX для его обработки.  
  
 Типы DBTYPE_NULL и DBTYPE_EMPTY могут быть привязаны только для входных параметров. Они не могут быть привязаны для выходных параметров или результатов. При привязке входных параметров следует установить состояние DBSTATUS_S_ISNULL или DBSTATUS_S_DEFAULT.  
  
 DBTYPE_XML можно преобразовать в DBTYPE_EMPTY и DBTYPE_NULL, DBTYPE_EMPTY можно преобразовать в DBTYPE_XML, но DBTYPE_NULL нельзя преобразовать в DBTYPE_XML. Это согласуется с DBTYPE_WSTR.  
  
 DBTYPE_IUNKNOWN является поддерживаемой привязки (как показано в таблице выше), но не существует преобразований между типами DBTYPE_XML и DBTYPE_IUNKNOWN. DBTYPE_IUNKNOWN нельзя использовать с DBTYPE_BYREF.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Добавления и изменения для наборов строк OLE DB  
 Драйвер OLE DB для SQL Server добавляет новые значения или изменяет многие из основных наборов строк схемы OLE DB.  
  
#### <a name="the-columns-and-procedureparameters-schema-rowsets"></a>Наборы строк схем COLUMNS и PROCEDURE_PARAMETERS  
 Дополнения к наборам строк схемы COLUMNS и PROCEDURE_PARAMETERS добавлены следующие столбцы:  
  
|Имя столбца|Тип|Description|  
|-----------------|----------|-----------------|  
|SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Имя каталога, в котором определена коллекция схем XML. Имеет значение NULL для столбца не XML или нетипизированный XML-столбец.|  
|SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Имя схемы, в которой определена коллекция схем XML. Имеет значение NULL для столбца не XML или нетипизированный XML-столбец.|  
|SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML. Имеет значение NULL для столбца не XML или нетипизированный XML-столбец.|  
  
#### <a name="the-providertypes-schema-rowset"></a>Набор строк схемы PROVIDER_TYPES  
 В наборе строк схемы PROVIDER_TYPES значение параметра COLUMN_SIZE имеет значение 0 для **xml** тип данных, а DATA_TYPE равен DBTYPE_XML.  
  
#### <a name="the-ssxmlschema-schema-rowset"></a>Набор строк схемы SS_XMLSCHEMA  
 Для клиентов добавлен новый набор строк схемы SS_XMLSCHEMA для получения информации о схеме XML. Набор строк SS_XMLSCHEMA содержит следующие столбцы:  
  
|Имя столбца|Тип|Description|  
|-----------------|----------|-----------------|  
|SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Каталог, которому принадлежит коллекция XML.|  
|SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Схема, которой принадлежит коллекция XML.|  
|SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML для типизированных XML-столбцов, NULL для всех остальных столбцов.|  
|TARGETNAMESPACEURI|DBTYPE_WSTR|Имя целевого пространства имен схемы XML.|  
|SCHEMACONTENT|DBTYPE_WSTR|Содержимое схемы XML.|  
  
 Для каждой схемы XML область действия ограничивается именем каталога, именем схемы, именем коллекции схем и URI-идентификатором целевого пространства имен. Кроме того, задан новый идентификатор GUID с именем DBSCHEMA_XML_COLLECTIONS. Количество ограничений и столбцы с ограничениями для набора строк схемы SS_XMLSCHEMA определены следующим образом.  
  
|GUID|Количество ограничений|Столбцы с ограничениями|  
|----------|----------------------------|------------------------|  
|DBSCHEMA_XML_COLLECTIONS|4|SCHEMACOLLECTION_CATALOGNAME<br /><br /> SCHEMACOLLECTION_SCHEMANAME<br /><br /> SCHEMACOLLECTIONNAME<br /><br /> TARGETNAMESPACEURI|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Добавления и изменения для наборов свойств OLE DB  
 Драйвер OLE DB для SQL Server добавляет новые значения или изменяет многие из основных свойств OLE DB наборов.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Набор свойств DBPROPSET_SQLSERVERPARAMETER  
 Чтобы обеспечить поддержку **xml** драйвер OLE DB для SQL Server через OLE DB, тип данных реализует новый набор свойств DBPROPSET_SQLSERVERPARAMETER, который содержит следующие значения.  
  
|Название|Тип|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Имя каталога (базы данных), где определена коллекция схем XML. Часть идентификатора трехкомпонентного имени SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Имя схемы XML в коллекции схемы XML. Часть идентификатора трехкомпонентного имени SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML в каталоге, представляющее собой часть трехчастного идентификатора имени SQL.|  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Набор свойств DBPROPSET_SQLSERVERCOLUMN  
 Для поддержки создания таблиц в **ITableDefinition** интерфейс, драйвер OLE DB для SQL Server добавляет к набору свойств DBPROPSET_SQLSERVERCOLUMN три новых столбца.  
  
|Название|Тип|Description|  
|----------|----------|-----------------|  
|SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME|VT_BSTR|Для типизированных столбцов XML данное свойство содержит строку, представляющую имя каталога, где хранится схема XML. Для других типов столбцов это свойство возвращает пустую строку.|  
|SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME|VT_BSTR|Для типизированных столбцов XML данное свойство содержит строку, представляющую имя схемы XML, задающей этот столбец.|  
|SSPROP_COL_XML_SCHEMACOLLECTIONNAME|VT_BSTR|Для типизированных столбцов XML данное свойство содержит строку, представляющую имя коллекции схем XML, определяющей значение.|  
  
 Подобно значениям SSPROP_PARAM, все эти свойства являются необязательными и по умолчанию пусты. SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME и SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME можно задавать только при заданном свойстве SSPROP_COL_XML_SCHEMACOLLECTIONNAME. При передаче данных в формате XML на сервер, если эти значения включены, они будут проверены на существование (допустимость) в текущей базе данных, а экземпляр данных проверяется по схеме. Во всех случаях, чтобы данные были допустимыми, эти столбцы должны быть все одновременно пусты или все одновременно заполнены.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Добавления и изменения для интерфейсов OLE DB  
 Драйвер OLE DB для SQL Server добавляет новые значения или изменяет многие из основных интерфейсов OLE DB.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Интерфейс ISSCommandWithParameters  
 Чтобы обеспечить поддержку **xml** драйвер OLE DB для SQL Server через OLE DB, тип данных реализует ряд изменений, включая добавление [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md) интерфейса. Этот новый интерфейс наследует основной интерфейс OLE DB **ICommandWithParameters**. Помимо трех методов, наследуемых от **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**, и **SetParameterInfo**; **ISSCommandWithParameters** предоставляет [GetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md) и [SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) методы, используемые для обработки конкретного сервера типы данных.  
  
> [!NOTE]  
>  **ISSCommandWithParameters** интерфейс также позволяет использовать новые SSPARAMPROPS структуры.  
  
#### <a name="the-icolumnsrowset-interface"></a>Интерфейс IColumnsRowset  
 Драйвер OLE DB для SQL Server добавляет следующие [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-определенные столбцы в наборе строк, возвращенных **IColumnRowset::GetColumnsRowset** метод. Эти столбцы содержат трехчастное имя коллекции схем XML. Для столбцов не в формате XML и нетипизированных столбцов XML все три данных столбца по умолчанию имеют значение NULL.  
  
|Имя столбца|Тип|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Каталог, которому принадлежит коллекция схем XML.<br /><br /> В противном случае — значение NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Схема, которой принадлежит коллекция схем XML. В противном случае — значение NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Имя коллекции схем XML для типизированных XML-столбцов, NULL — для всех остальных столбцов.|  
  
#### <a name="the-irowset-interface"></a>Интерфейс IRowset  
 Экземпляр XML в XML-столбце извлекается с помощью **IRowset::GetData** метод. В зависимости от привязки, указанной клиентом, экземпляр XML может быть получен в виде типа DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML, DBTYPE_STR, DBTYPE_BYTES или как интерфейс через DBTYPE_IUNKNOWN. Если потребитель задает тип DBTYPE_BSTR, DBTYPE_WSTR или DBTYPE_VARIANT, поставщик преобразует экземпляр XML в запрошенный пользователем тип и помещает в местонахождение, заданное соответствующей привязкой.  
  
 Если потребитель задает DBTYPE_IUNKNOWN и задает *pObject* аргумент значение NULL или наборы *pObject* аргумент IID_ISequentialStream, поставщик возвращает **ISequentialStream** потребителю интерфейс, чтобы потребитель мог направить данные XML из столбца. **ISequentialStream** возвращает XML-данные как поток символов Юникода.  
  
 При возврате значения XML, привязанного к DBTYPE_IUNKNOWN, поставщик передает значение размера `sizeof (IUnknown *)`. Такое поведение согласуется с подходом, который используется при передаче привязанного столбца как DBTYPE_IUnknown или DBTYPE_IDISPATCH, а также по DBTYPE_IUNKNOWN/ISequentialStream, когда не удается определить точный размер столбца.  
  
#### <a name="the-irowsetchange-interface"></a>Интерфейс IRowsetChange  
 Потребитель может изменить экземпляр XML в столбце двумя способами. Первый — объект хранилища **ISequentialStream** созданные поставщиком. Потребитель может вызвать **ISequentialStream::Write** метод для непосредственного изменения экземпляра XML, возвращенный поставщиком.  
  
 Второй подход **IRowsetChange::SetData** или **IRowsetChange::InsertRow** методы. При таком подходе экземпляр XML в буфере потребителя можно задать привязкой типа DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML или DBTYPE_IUNKNOWN.  
  
 Если указано DBTYPE_BSTR, DBTYPE_WSTR или DBTYPE_VARIANT поставщик сохраняет экземпляр XML в буфере потребителя в соответствующий столбец.  
  
 Если указан DBTYPE_IUNKNOWN/ISequentialStream, если потребитель не задал объект хранилища, потребитель должен создать **ISequentialStream** заранее, привязать XML-документ с объектом, а затем передать Объект поставщика через **IRowsetChange::SetData** метод. Потребитель может также создать хранилища объекта, установить аргумент pObject равным IID_ISequentialStream, создать **ISequentialStream** и затем передайте **ISequentialStream** объект **IRowsetChange::SetData** метод. В обоих случаях поставщик может получить объект XML через **ISequentialStream** объекта и вставить ее в нужный столбец.  
  
#### <a name="the-irowsetupdate-interface"></a>Интерфейс IRowsetUpdate  
 **IRowsetUpdate** интерфейс предоставляет функциональность отсроченных изменений. Данные, доступные наборам строк не предоставляются другим транзакциям пока потребитель не вызовет метод **IRowsetUpdate::Update** метод.  
  
#### <a name="the-irowsetfind-interface"></a>Интерфейс IRowsetFind  
 **IRowsetFind::FindNextRow** метод не работает с **xml** тип данных. Когда **IRowsetFind::FindNextRow** вызывается и *hAccessor* аргумент задает столбец типа DBTYPE_XML, будет возвращен результат DB_E_BADBINDINFO. Это происходит независимо от типа столбца, в котором производится поиск данных. Для любого другого типа привязки **FindNextRow** возвращает результат DB_E_BADCOMPAREOP, если столбец для поиска **xml** тип данных.  
 
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для компонентов SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [ISSCommandWithParameters & #40; OLE DB & #41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
