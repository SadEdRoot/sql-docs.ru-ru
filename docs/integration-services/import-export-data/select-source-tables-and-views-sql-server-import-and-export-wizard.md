---
title: "Выбор исходных таблиц и представлений (мастер импорта и экспорта SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.impexpwizard.selectsourcetablesandviews.f1"
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
caps.latest.revision: 96
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 88
---
# Выбор исходных таблиц и представлений (мастер импорта и экспорта SQL Server)
  После того как вы укажете, хотите ли вы скопировать всю таблицу, или после определения запроса в мастере импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] откроется страница **Выбор исходных таблиц и представлений**. На этой странице выберите существующие таблицы и представления, которые нужно скопировать. Затем следует сопоставить исходные таблицы с новыми или существующими целевыми таблицами. При необходимости можно проверить, правильно ли сопоставлены отдельные столбцы, и открыть предпросмотр образца данных.

> [!TIP] Если вам нужно скопировать несколько баз данных или объекты базы данных, отличные от таблиц и представлений, вместо мастера импорта и экспорта используйте мастер копирования базы данных. Дополнительные сведения см. в разделе [Использование мастера копирования базы данных](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="screen-shot---what-you-see-if-youre-going-to-copy-tables"></a>Снимок экрана: представление, отображаемое при копировании таблиц  
 На следующем снимке экрана показана страница **Выбор исходных таблиц и представлений** мастера, которая открывается после выбора параметра **Скопировать данные из одной или нескольких таблиц или представлений** на странице **Выбор копирования таблицы или запроса**. В списке показаны все таблицы и представления, доступные в источнике данных.
 
В этом примере пользователь хочет скопировать таблицу **Sales.Customer** из источника в новую таблицу **Sales.CustomerNew** в месте назначения. 
   
 ![Select tables page of the Import and Export Wizard](../../integration-services/import-export-data/media/select-tables1.png "Select tables page of the Import and Export Wizard")
  
## <a name="screen-shot---what-you-see-if-you-provided-a-query"></a>Снимок экрана: представление, отображаемое при определении запроса  
 На следующем снимке экрана показана страница **Выбор исходных таблиц и представлений** мастера, которая открывается после выбора параметра **Написать запрос, указывающий данные для передачи** на странице **Выбор копирования таблицы или запроса** и последующего указания запроса на странице **Определение исходного запроса**. Список содержит только одну строку, где элемент в столбце "Источник" представляет указанный вами запрос.
 
В этом примере пользователь хочет скопировать результаты запроса в таблицу **Sales.CustomerNew** в месте назначения.  
    
 ![Select tables page of the Import and Export Wizard](../../integration-services/import-export-data/media/select-tables2.png "Select tables page of the Import and Export Wizard")  

## <a name="select-source-and-destination-tables"></a>Выбор исходных и целевых таблиц 
**Источник**  
С помощью флажков выберите из списка таблицы и представления для копирования в место назначения. По умолчанию данные из источника данных копируются без изменений. При создании новой целевой таблицы схема также копируется из источника данных без изменений.

Если подается запрос, список содержит только один элемент с именем \[Query\]. 

**Назначение**  
 Выберите из списка целевую таблицу для каждой исходной таблицы или запроса либо введите имя таблицы, которую мастер должен создать. Если выбирается существующая целевая таблица, она должна включать столбцы с типами данных, совместимыми с исходными данными.  

> [!NOTE] Если в этой точке работы мастера вы создадите целевую таблицу в базе данных назначения вручную, используя внешнее средство (например, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]), новая таблица не сразу появится в списке доступных целевых таблиц. Чтобы обновить список целевых таблиц, вернитесь на страницу **Выбор назначения**, еще раз выберите целевую базу данных, чтобы обновить список доступных таблиц и представлений, и снова перейдите на страницу **Выбор исходных таблиц и представлений**.  

## <a name="select-source-and-destination-tables-for-excel"></a>Выбор исходных и целевых таблиц для Excel

### <a name="excel-source-tables"></a>Исходные таблицы Excel
В список исходных таблиц и представлений для источника данных Excel входит два типа объектов Excel.
-   **Листы**. После имен листов следует символ доллара ($), например **Лист1$**.
-   **Именованные диапазоны**. Именованные диапазоны (если таковые имеются) указываются по имени.

Если требуется загрузить данные из определенного неименованного диапазона ячеек или в него, например из диапазона **[Лист1$A1:B4]** или в него, необходимо написать запрос. Вернитесь на страницу **Выбор копирования таблицы или запроса** и выберите вариант **Написать запрос, указывающий данные для передачи**.

Если в качестве исходной таблицы указан лист или диапазон, драйвер считывает *непрерывный* блок ячеек, начиная с первой непустой ячейки в верхнем левом углу листа или диапазона. Поэтому в исходных данных не должно быть пустых строк. Например, пустой строки не должно быть между заголовками столбцов и строками данных. Если после заголовка следуют пустые строки в верхней части листа над данными, выполнить запрос к листу не удастся. В Excel необходимо присвоить имя диапазону данных и выполнить запрос к именованному диапазону, а не к листу.

### <a name="excel-destination-tables"></a>Целевые таблицы Excel
При экспорте данных в Excel можно указать назначение одним из следующих трех способов.
-   **Лист**. Чтобы указать лист, добавьте в конец имени листа символ $ и окружите сроку разделителями, например **[Лист1$]**.
-   **Именованный диапазон**. Чтобы указать именованный диапазон, используйте имя диапазона, например **Мой_диапазон**.
-   **Неименованный диапазон**. Чтобы указать диапазон ячеек, которым не были заданы имена, добавьте символ $ после имени листа, добавьте спецификацию диапазона и окружите строку разделителями, например **[Лист1$A1:B4]**.

## <a name="special-considerations-for-excel-sources-and-destinations"></a>Особые замечания, касающиеся Excel в качестве источника и назначения
Если Excel используется в качестве источника или назначения, рекомендуется выбрать пункт **Изменить сопоставления** и проверить сопоставления типов данных на странице **Сопоставления столбцов**. 

**Типы данных в книгах Excel**. Excel не является обычной базой данных. У его столбцов нет фиксированных типов данных. Мастер распознает только ограниченный набор данных типов в Excel — числовой, денежный, логический, дата и время, строковый (255 символов или меньше) и типа memo (более 255 символов). Мастер считывает определенное количество строк (по умолчанию восемь строк) в источнике данных Excel для определения типа данных каждого столбца.

Если мастеру приходится выполнить явное преобразование типа данных для загрузки в Excel или из него, обычно отображается страница **Просмотр сопоставления типов данных**, где можно просмотреть эти преобразования. В число этих преобразований могут входить следующие.
-   Преобразование между числовыми столбцами Excel с плавающей запятой двойной точности и числовыми столбцами других типов.
-   Преобразование между строковыми столбцами Excel в Юникоде и строковыми столбцами в формате с конкретными кодовыми страницами, отличными от Юникода.
-   Преобразование между строковыми столбцами Excel длиной в 255 символов и строковыми столбцами другой длины.

### <a name="special-considerations-for-excel-sources"></a>Особые замечания, касающиеся источников Excel
**Значения NULL или отсутствующие значения в импортированных данных**. Если столбец Excel в первых восьми строках, выбранных мастером, содержит смешанные типы данных (например, числовые значения с текстовыми значениями), в качестве типа данных столбца будет выбран преобладающий тип данных, а для ячеек, содержащих данные других типов, будет возвращено значение NULL. Изменить это поведение мастера невозможно.

**Усеченные строки в импортированных данных**. Когда мастер определяет, что столбец Excel содержит текстовые данные, он выбирает тип данных столбца (строковый или memo) на основании самого длинного значения, отобранного в первых восьми строках. Если мастер не находит значений длиннее 255 символов в выбираемых строках, он считает, что столбец является строковым с длиной 255 символов, а не столбцом типа memo, и усекает значения длиннее 255 символов. Чтобы импортировать данные из столбца типа memo без усечения, этот столбец должен содержать по меньшей мере одно значение длиннее 255 символов в первых восьми строках.

### <a name="special-considerations-for-excel-destinations"></a>Особые замечания, касающиеся назначений Excel
**Указание существующего диапазона**. При указании существующего диапазона в качестве назначения появится сообщение об ошибке, если диапазон недостаточно широк (то есть если в нем меньше столбцов, чем в исходных данных). Если же указываемый диапазон недостаточно велик (то есть содержит меньше строк, чем исходные данные), мастер продолжит записывать строки и расширит определение диапазона для соответствия новому числу строк.

**Сохранение данных типа memo (ntext)**. Чтобы успешно сохранять в столбцы Excel строки, имеющие длину более 255 символов, мастер должен распознать тип данных целевого столбца как **memo**, а не как **string**.
-   Если в целевой таблице уже содержатся строки данных, то в столбце типа memo в первых восьми строках, которые проверит мастер, должна содержаться по меньшей мере одна строка со значением, имеющим длину более 255 символов.
-   Если целевая таблица создается в ходе работы мастера, в инструкции **CREATE TABLE** необходимо использовать **LONGTEXT** (или один из его синонимов) в качестве типа данных для столбца типа memo. Проверьте инструкцию **CREATE TABLE**, нажав кнопку **Изменить SQL** рядом с параметром **Создать целевую таблицу** на странице **Сопоставления столбцов**.

## <a name="optionally-edit-column-mappings-and-preview-sample-data"></a>При необходимости можно изменить сопоставления столбцов и просмотреть образец данных.
**Изменение сопоставлений**   
Нажмите кнопку **Изменить сопоставления**, чтобы вызвать диалоговое окно **Сопоставления столбцов** для выбранной таблицы. В диалоговом окне **Сопоставления столбцов** можно выполнять следующие действия:
-   просмотреть сопоставление отдельных столбцов между источником и местом назначения;
-   скопировать отдельное подмножество столбцов, установив флажок **пропустить** для тех столбцов, копировать которые не нужно.

Дополнительные сведения см. в разделе [Сопоставления столбцов](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).  

**Предварительный просмотр**  
Нажмите кнопку **Предварительный просмотр**, чтобы открыть предварительный просмотр до 200 строк образца данных в диалоговом окне **Предварительный просмотр данных**. Таким образом вы убедитесь, что мастер будет копировать именно необходимые данные. Дополнительные сведения см. в разделе [Предварительный просмотр данных](../../integration-services/import-export-data/preview-data-dialog-box-sql-server-import-and-export-wizard.md).  
  
После просмотра данных может потребоваться изменить параметры, выбранные на предыдущих страницах мастера. Для этого вернитесь на страницу **Выбор исходных таблиц и представлений** и нажмите кнопку **Назад**, чтобы вернуться к предыдущим страницам, где можно изменить выбранные параметры.  

## <a name="whats-next"></a>Дальнейшие действия  
 После того как вы выберете существующие таблицы и представления, которые нужно скопировать, и сопоставите их с местами назначения, откроется страница **Сохранение и запуск пакета**. На этой странице можно указать, нужно ли немедленно запустить операцию копирования. В зависимости от конфигурации, также можно сохранить пакет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], созданный с помощью мастера, чтобы настроить и использовать его позднее. Дополнительные сведения см. в разделе [Сохранение и запуск пакета](../../integration-services/import-export-data/save-and-run-package-sql-server-import-and-export-wizard.md).  