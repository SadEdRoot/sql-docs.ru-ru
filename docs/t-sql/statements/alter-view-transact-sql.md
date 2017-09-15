---
title: "ALTER VIEW (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_VIEW_TSQL
- ALTER VIEW
dev_langs:
- TSQL
helpviewer_keywords:
- indexed views [SQL Server], modifying
- views [SQL Server], modifying
- modifying views
- ALTER VIEW statement
ms.assetid: 03eba220-13e2-49e3-bd9d-ea9df84dc28c
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 006b9fce1e13833c977d26d4bc0f13a602f2c96c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-view-transact-sql"></a>ALTER VIEW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Изменяет ранее созданное представление, в том числе индексированное. Инструкция ALTER VIEW не влияет на зависимые хранимые процедуры или триггеры и не изменяет разрешения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER VIEW [ schema_name . ] view_name [ ( column [ ,...n ] ) ]   
[ WITH <view_attribute> [ ,...n ] ]   
AS select_statement   
[ WITH CHECK OPTION ] [ ; ]  
  
<view_attribute> ::=   
{   
    [ ENCRYPTION ]  
    [ SCHEMABINDING ]  
    [ VIEW_METADATA ]       
}   
```  
  
## <a name="arguments"></a>Аргументы  
 *schema_name*  
 Имя схемы, которой принадлежит представление.  
  
 *view_name*  
 Представление, которое нужно изменить.  
  
 *столбец*  
 Имя столбца или разделенные запятыми имена нескольких столбцов, входящих в состав указанного представления.  
  
> [!IMPORTANT]  
>  Заданные для столбца разрешения сохраняются только в том случае, если после выполнения инструкции ALTER VIEW имя столбца остается таким же, каким оно было до этого.  
  
> [!NOTE]  
>  В столбцах представления разрешения для имени столбца применяются с инструкцией CREATE VIEW или ALTER VIEW вне зависимости от источника базовых данных. Например, если были предоставлены разрешения для **SalesOrderID** столбец в инструкции CREATE VIEW, инструкция ALTER VIEW может переименовать **SalesOrderID** столбцов, таких как **OrderRef**и все же иметь разрешения, связанные с использованием представления **SalesOrderID**.  
  
 ENCRYPTION  
 **Применяется к**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
 Шифрует записи в [sys.syscomments](../../relational-databases/system-compatibility-views/sys-syscomments-transact-sql.md) , содержащего текст инструкции ALTER VIEW. Предложение WITH ENCRYPTION предотвращает публикацию представления при репликации SQL Server.  
  
 SCHEMABINDING  
 Привязывает представление к схеме базовой таблицы или таблиц. Если аргумент SCHEMABINDING указан, изменить базовые таблицы таким образом, чтобы это повлияло на определение представления, нельзя. Для удаления зависимостей из таблицы, которую требуется изменить, вначале нужно изменить или удалить само представление. При использовании предложения SCHEMABINDING, *select_statement* должен включать двухкомпонентные имена (*схемы***.** *объекта*) из таблицы, представления или определяемой пользователем функции, на которые ссылаются. Все указанные в инструкции объекты должны находиться в одной базе данных.  
  
 Представления или таблицы, входящие в представление, созданное при помощи предложения SCHEMABINDING, не могут быть удалены, пока это представление не будет удалено или изменено так, что больше не будет привязано к схеме. В противном случае компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] выдаст ошибку. Кроме того, выполнение инструкций ALTER TABLE для таблиц, входящих в представления, связанные со схемами, завершается неудачей, если эти инструкции влияют на определение представления.  
  
 VIEW_METADATA  
 Указывает, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвратит в API-интерфейсы DB-Library, ODBC и OLE DB сведения метаданных о представлении вместо базовой таблицы или таблиц, когда метаданные режима обзора затребованы для запроса, который ссылается на представление. Метаданные режима просмотра — это дополнительные метаданные, которые экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращает клиентским API-интерфейсам DB-Library, ODBC и OLE DB. Эти метаданные позволяют клиентским API-интерфейсам реализовывать обновляемые клиентские курсоры. Метаданные режима обзора содержат сведения о базовой таблице, которой принадлежат столбцы в результирующем наборе.  
  
 Для представлений, созданных с применением предложения VIEW_METADATA, метаданные режима обзора возвращают имя представления, а не имена базовых таблиц при описании столбцов из представления в результирующем наборе.  
  
 При создании представления с предложением WITH VIEW_METADATA, все ее столбцы, за исключением **timestamp** столбца, поддерживают обновление, если триггеры UPDATE INSTEAD OF или INSERT имеет представление. Дополнительные сведения см. в разделе «Примечания» в [CREATE VIEW & #40; Transact-SQL & #41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
 AS  
 Действия, которые должны быть выполнены в представлении.  
  
 *select_statement*  
 Инструкция SELECT, которая определяет представление.  
  
 WITH CHECK OPTION  
 Заставляет все инструкции изменения данных, выполняемых для представления критериям, заданным в *select_statement*.  
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения об инструкции ALTER VIEW см. в заметках [CREATE VIEW & #40; Transact-SQL & #41; ](../../t-sql/statements/create-view-transact-sql.md).  
  
> [!NOTE]  
>  Если предыдущее определение представления было создано с использованием предложения WITH ENCRYPTION или CHECK OPTION, эти параметры будут действовать только в том случае, если они включены в инструкцию ALTER VIEW.  
  
 При изменении текущего представления с помощью инструкции ALTER VIEW компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] осуществляет монопольную блокировку схемы представления. Если блокировка предоставлена, и с представлением в настоящий момент не работает ни один пользователь, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] удаляет все копии представления из кэша процедур. Существующие планы, ссылающиеся на представление, остаются в кэше, но при обращении к ним выполняется повторная компиляция.  
  
 Инструкцию ALTER VIEW можно выполнять для индексированных представлений, однако она удаляет все индексы представления.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции ALTER VIEW необходимо как минимум разрешение ALTER на объект.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается представление `EmployeeHireDate`, содержащее фамилии и имена всех сотрудников, а также даты их приема на работу. Представлению предоставляются необходимые разрешения, но требования изменяются таким образом, чтобы из базы данных извлекались сведения только о сотрудниках, принятых на работу до определенной даты. Для замены представления используется инструкция `ALTER VIEW`.  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE VIEW HumanResources.EmployeeHireDate  
AS  
SELECT p.FirstName, p.LastName, e.HireDate  
FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
ON e.BusinessEntityID = p.BusinessEntityID ;  
GO  
  
```  
  
 Представление нужно изменить так, чтобы оно включало только сотрудников, принятых на работу до `2002` года. Если не использовать инструкцию ALTER VIEW, а удалить представление и создать его заново, нужно будет повторно выполнить инструкцию GRANT и любые другие инструкции, работающие с разрешениями данного представления.  
  
```  
ALTER VIEW HumanResources.EmployeeHireDate  
AS  
SELECT p.FirstName, p.LastName, e.HireDate  
FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
ON e.BusinessEntityID = p.BusinessEntityID  
WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md)   
 [УДАЛИТЬ ПРЕДСТАВЛЕНИЕ & #40; Transact-SQL & #41;](../../t-sql/statements/drop-view-transact-sql.md)   
 [Создание хранимой процедуры](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Внесение изменений в схемы баз данных публикации](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
