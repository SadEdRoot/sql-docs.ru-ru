---
title: NULL и UNKNOWN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, pdw, sql-database
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
caps.latest.revision: 5
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 53908dd59ebe1aede15a6725db10c49d61212e7e
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="null-and-unknown-transact-sql"></a>NULL и UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL указывает на то, что значение неизвестно. NULL отличается от пустого или нулевого значения. Два значения NULL считаются эквивалентными. Сравнения между двумя значениями NULL или между значением NULL и каким-либо иным значением возвращают неизвестную величину, так как значение каждого из значений NULL неизвестно.  
  
 Значение NULL обычно указывает на то, что данные неизвестны, неприменимы или будут добавлены позже. Например, на момент размещения клиентом заказа может быть неизвестно его отчество.  
  
 Обратите внимание на следующие особенности значений NULL:  
  
-   для проверки наличия значения NULL в предложении WHERE запроса используются ключевые слова IS NULL или IS NOT NULL;  
  
-   значения NULL могут появиться в столбце явным указанием значения NULL в инструкции INSERT или UPDATE или пропуском указания столбца в инструкции INSERT;  
  
-   значения NULL не могут применяться в тех случаях, когда необходимо отличать одну строку таблицы от другой, например в качестве первичного или внешнего ключа, или распределять строки, например в качестве ключа распределения.  
  
 Если в данных присутствуют значения NULL, логические операторы и операторы сравнения могут возвращать, кроме TRUE или FALSE, также и третий результат — UNKNOWN. Эта тройственная логика является источником многих проблем в приложениях. Логические операторы в логическом выражении, включающие значения UNKNOWN, будут возвращать UNKNOWN, за исключением случаев, когда результат оператора не зависит от выражения UNKNOWN. В таблицах содержатся примеры такого поведения.  
  
 В следующей таблице показаны результаты применения оператора AND к двум логическим выражениям, когда одно выражение возвращает UNKNOWN.  
  
|Выражение 1|Выражение 2|Результат|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 В следующей таблице показаны результаты применения оператора OR к двум логическим выражениям, когда одно выражение возвращает UNKNOWN.  
  
|Выражение 1|Выражение 2|Результат|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>См. также:  
 [AND (Transact-SQL)](../../t-sql/language-elements/and-transact-sql.md)   
 [OR (Transact-SQL)](../../t-sql/language-elements/or-transact-sql.md)   
 [NOT (Transact-SQL)](../../t-sql/language-elements/not-transact-sql.md)   
 [IS NULL (Transact-SQL)](../../t-sql/queries/is-null-transact-sql.md)  
  
  
