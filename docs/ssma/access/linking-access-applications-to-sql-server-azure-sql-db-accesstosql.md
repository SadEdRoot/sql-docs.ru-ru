---
title: Связывание приложения Access в SQL Server — база данных Azure SQL | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases, linking to SQL Azure
- Access databases, linking to SQL Server
- auto-increment columns
- data types, unsupported
- hyperlink columns
- linking tables
- migrating databases, post-migration issues
- post-migration issues
- reference, post-migration issues
- refreshing linked tables
- slow performance
- unlinking tables
ms.assetid: 82374ad2-7737-4164-a489-13261ba393d4
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: bcfaa4ffcaaf8a621062f0809831437647b894fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="linking-access-applications-to-sql-server---azure-sql-db-accesstosql"></a>Связывание приложения Access в SQL Server — база данных SQL Azure (AccessToSQL)
Если вы хотите использовать существующие приложения Access с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно связать исходные таблицы Access с перенесенными [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц SQL Azure. Связывание изменяет базу данных Access, страниц доступа к запросы, формы, отчеты и данные использовать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure, а не данные в базе данных.  
  
> [!NOTE]  
> Таблиц доступа остаются в Access, но не обновляются вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обновляет SQL Azure. Связь между таблицами и проверки функциональности, может потребоваться удалить доступ таблиц.  
  
## <a name="linking-access-and-sql-server-tables"></a>Связывание таблиц Access и SQL Server  
При связывании таблицы Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблице SQL Azure, базы данных Jet хранятся сведения о соединении и метаданных таблицы, но данные хранятся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Это присоединение позволяет приложения для доступа к работать с доступа к таблицам, даже если фактический таблиц и данных определены в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
> [!NOTE]  
> Если вы используете [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] проверки подлинности, пароль хранится в виде открытого текста в связанных таблицах Access. Рекомендуется использовать проверку подлинности Windows.  
  
**Чтобы связать таблицы**  
  
1.  В обозревателе метаданных доступа выберите таблицы, которые необходимо связать.  
  
2.  Щелкните правой кнопкой мыши **таблиц**, а затем выберите **ссылку**.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для доступа резервная копия исходной таблицы доступа и создает связанную таблицу.  
  
После связывания таблицы, таблицы в SSMA отображаются со значком небольшой ссылки. В режиме доступа таблицы отображаются со значком «связанный», являющийся шар со стрелкой, указывающей на него.  
  
При открытии таблицы в Access данные получаются с помощью курсора набора ключей. Поэтому для больших таблиц, все данные извлекаются только за один раз. Однако при просмотре таблицы Access загружает дополнительные данные по мере необходимости.  
  
> [!IMPORTANT]  
> Чтобы связать таблицы access с базой данных Azure, требуется собственный Client(SNAC) SQL Server версии 10.5 или более поздней версии.   
> Можно получить последнюю версию SNAC из [пакет дополнительных компонентов Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940).  
  
## <a name="unlinking-access-tables"></a>Удаление связи доступа к таблицам  
Если удалить связь таблицы Access с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблице SQL Azure, SSMA восстанавливает исходные таблицы Access и ее данных.  
  
**Чтобы разорвать связь между таблицами**  
  
1.  В обозревателе метаданных доступа выберите таблицы, которые требуется удалить.  
  
2.  Щелкните правой кнопкой мыши **таблиц**, а затем выберите **отменить связь**.  
  
## <a name="linking-tables-to-a-different-server"></a>Связывание таблиц на другой сервер  
Если вы связали открывать таблицы в одном экземпляре SQL Server, и позднее потребуется изменить ссылки на другой экземпляр, необходимо повторно связать таблицы.  
  
**Чтобы связать таблицы на другой сервер**  
  
1.  В обозревателе метаданных доступа выберите таблицы, которые требуется удалить.  
  
2.  Щелкните правой кнопкой мыши **таблиц** , а затем выберите **отменить связь**.  
  
3.  Нажмите кнопку **повторно подключиться к SQL Server** кнопку.  
  
4.  Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, к которому необходимо связать доступа к таблицам.  
  
5.  В обозревателе метаданных доступа выберите таблицы, которые необходимо связать.  
  
6.  Щелкните правой кнопкой мыши **таблиц**, а затем выберите **ссылку**.  
  
## <a name="updating-linked-tables"></a>Обновление связанных таблиц  
Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или изменяются определения таблиц SQL Azure, можно разорвать связь и повторно связывать таблицы в SSMA с помощью процедур, показанному ранее в этом разделе. Можно также обновить таблицы с помощью доступа.  
  
**Обновление связанных таблиц с помощью Access**  
  
1.  Откройте базу данных Access.  
  
2.  В **объектов** выберите **таблиц**.  
  
3.  Щелкните правой кнопкой мыши связанную таблицу, а затем выберите **Диспетчер связанных таблиц**.  
  
4.  Установите флажок рядом с каждой связанной таблицы, которую требуется обновить и нажмите кнопку **ОК**.  
  
## <a name="possible-post-migration-issues"></a>Возможные причины неполадок после миграции  
В следующих разделах список проблем, которые могут возникнуть в существующие приложения Access, после миграции баз данных с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure и затем связь между таблицами, а также причины и способы их устранения.  
  
### <a name="slow-performance-with-linked-tables"></a>Низкая производительность в связанных таблицах  
**Причина:** некоторых запросов может быть медленным после преобразования по следующим причинам:  
  
-   Приложение зависит от функций, которые не существуют в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, что приведет к тому Jet для таблицы локально для выполнения запроса SELECT.  
  
-   Запросы, которые обновляют или удаляют множество строк отправляются Jet как параметризованный запрос для каждой строки.  
  
**Решение:** преобразование медленного выполнения запросов в передаваемых запросах, хранимых процедур или представлений. Преобразование в передаваемых запросах связано со следующими проблемами:  
  
-   Не удается изменить запросы к серверу. Изменение результата запроса или добавление новых записей должны выполняться в альтернативным способом, например, задав явную **изменить** или **добавить** кнопки в форме, к которому привязана к запросу.  
  
-   Некоторые запросы требуют ввода, но передаваемые запросы не поддерживают ввод данных пользователем. Ввод данных пользователем можно получить, Visual Basic для приложений (VBA), которые запрашиваются параметры, или форму, которая используется в качестве элемента управления вводом. В обоих случаях код VBA отправляет запрос с входными данными пользователя на сервер.  
  
### <a name="auto-increment-columns-are-not-updated-until-the-record-is-updated"></a>До обновления записи не обновляются столбцов автоприращения  
**Причина:** после вызова RecordSet.AddNew в Jet, столбца автоматическим приращением доступен до обновления записи. Это не так в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Новое значение нового значения столбца идентификаторов доступен только после сохранения новой записи.  
  
**Решение:** запустите следующий код Visual Basic для приложений (VBA) перед обращением к поле удостоверения:  
  
```  
Recordset.Update  
Recordset.Move 0,  
Recordset.LastModified  
```  
  
### <a name="new-records-are-not-available"></a>Новые записи недоступны.  
**Причина:** при добавлении записи, которая позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблицу SQL Azure с помощью VBA, если поле уникального индекса таблицы имеет значение по умолчанию и не назначить значение к этому полю, новая запись не отображается до повторного открытия таблицы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или S Менное Azure. При попытке получения значения для новой записи, появляется следующее сообщение об ошибке:  
  
`Run-time error '3167' Record is deleted.`  
  
**Решение:** при открытии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure таблицы с помощью кода VBA, включают `dbSeeChanges` параметра, как показано в следующем примере:  
  
`Set rs = db.OpenRecordset("TestTable", dbOpenDynaset, dbSeeChanges)`  
  
### <a name="after-migration-some-queries-will-not-allow-the-user-to-add-a-new-record"></a>После миграции некоторых запросов не позволит пользователю добавить новую запись  
**Причина:** Если запрос не содержит все столбцы, включенные в уникальный индекс, невозможно добавить новые значения с помощью запроса.  
  
**Решение:** убедитесь, что все столбцы, входящие в хотя бы один уникальный индекс части запроса.  
  
### <a name="you-cannot-modify-a-linked-table-schema-with-access"></a>Не удается изменить схему связанной таблицы с доступом  
**Причина:** после переноса данных и связывания таблиц, пользователь не может изменить схему таблицы в Access.  
  
**Решение:** изменить схему таблицы с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], а затем обновите ссылку в Access.  
  
### <a name="hyperlink-functionality-is-lost-after-migrating-data"></a>Функциональность гиперссылки теряются после переноса данных  
**Причина:** после переноса данных, гиперссылки в столбцах потерять свои функциональные возможности и упрощается **nvarchar(max)** столбцов.  
  
**Решение:** None.  
  
### <a name="some-sql-server-data-types-are-not-supported-by-access"></a>Некоторые типы данных SQL Server не поддерживается доступ  
**Причина:** Если впоследствии обновить ваш [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или таблиц SQL Azure содержит типы данных, которые не поддерживаются службой доступа, не удается открыть таблицу в Access.  
  
**Решение:** можно определить запрос доступа, который возвращает только те строки, поддерживаемые типы данных.  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
