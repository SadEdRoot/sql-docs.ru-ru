---
title: Преобразование типов данных | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], conversions
- SQL data types [ODBC], conversions
- converting data [ODBC]
- converting data types [ODBC]
- C data types [ODBC], conversions
ms.assetid: d311fe1c-d882-4136-9fa5-220a4121e04c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0501e4bf627d8dafddfbf5020345d43135af9d6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-conversions"></a>Преобразование типов данных
Данные могут преобразовываться из одного типа в другой на одном из четырех раз: когда данные передаются из переменной одного приложения в другую (C по C) при отправке данных в переменную приложения к параметру инструкции (для SQL C), при возврате данных в столбец результирующего набора в переменную приложения (SQL в C), а при передаче данных из столбца источника данных на другой (SQL на SQL).  
  
 Любое преобразование, которое возникает, когда данные передаются из переменной одно приложение на другой выходит за рамки настоящего документа.  
  
 Приложение привязывает переменную в результирующий набор столбцов или инструкции параметр, приложение неявно задает преобразование типов данных при его выборе типа данных переменной приложения. Например предположим, что столбец содержит целочисленные данные. Если приложение связывает целочисленной переменной к столбцу, указывает, что преобразование не быть выполнено; Если приложение связывает столбец символьной переменной, он указывает, что данные преобразовать из целого символ.  
  
 ODBC определяет способ преобразования данных между каждого типа данных SQL и C. По сути ODBC, поддерживающий преобразования всех разумного, таких как символ, целое число со знаком и целое число, число с плавающей запятой и не поддерживает неверно преобразования, такие как число с плавающей запятой до даты. Необходимые драйверы для поддержки для каждого типа данных SQL, которые они поддерживают все преобразования. Полный список преобразований между типами данных SQL и C см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) и [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md) в типах данных приложение D:.  
  
 ODBC также определяет скалярную функцию для преобразования данных из одного типа данных SQL в другой. **Преобразовать** скалярная функция сопоставлен драйвером базовой скалярной функции или функции, определенные для выполнения преобразования в источнике данных. Так как эта функция сопоставлен с функциями СУБД, ODBC не определяет, как работают эти преобразования или какие преобразования должен поддерживаться. Приложение обнаруживает какие преобразования поддерживаемых конкретного драйвера и источник данных по элементам SQL_CONVERT **SQLGetInfo**. Дополнительные сведения о **преобразовать** скалярной функции в разделе [Escape-последовательности ODBC в](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md) и [явную функцию преобразования типа данных](../../../odbc/reference/appendixes/explicit-data-type-conversion-function.md).
