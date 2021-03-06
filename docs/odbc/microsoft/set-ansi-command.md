---
title: Команды SET ANSI | Документы Microsoft
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
- set ANSI command [ODBC]
ms.assetid: cf9a01b2-14bf-458c-a73c-2a58ddef32d8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5946efa397fa6bde8c52ad69925a96f2e33f7dd4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-ansi-command"></a>Команды SET ANSI
Определяет способ между строки разной длины сравнения с =-оператор в командах Visual FoxPro SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET ANSI ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера, значение по умолчанию для Visual FoxPro — OFF). Дополняет понадобится более короткие строки с пустые значения для упростить длина строки равно тем больше времени. Две строки, затем последовательно сравниваемых символов для символа для их всей длины. Рассмотрим это сравнение.  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результат равен False (. Е.) Если SET ANSI имеет значение on, так как при заполнении «Tom» становится «Tom» и строки «Том» и «Антон» не соответствуют символ.  
  
 == Оператор использует этот метод для сравнения в команды Visual FoxPro SQL.  
  
 OFF  
 Указывает, не дополняются пробелами это более короткие строки. Сравниваются две строки символа для символов, пока не будет достигнут конец более короткие строки. Рассмотрим это сравнение.  
  
```  
'Tommy' = 'Tom'  
```  
  
 Результатом является значение True (. Если SET ANSI отключен, так как T.) процедура сравнения останавливается после «Tom».  
  
## <a name="remarks"></a>Замечания  
 SET ANSI определяет ли более короткой двух строк дополняется пробелы при сравнении строк SQL. SET ANSI не оказывает влияния на ==-оператор; При использовании оператора ==, более короткая строка дополняется всегда пустые значения для сравнения.  
  
## <a name="string-order"></a>Строка заказа  
 В командах SQL порядок слева направо между двумя строками в сравнении не irrelevantswitching строку с одной стороны, = или ==-оператор на другую не влияет на результат сравнения.  
  
## <a name="see-also"></a>См. также  
 [ВЫБЕРИТЕ - команда SQL](../../odbc/microsoft/select-sql-command.md)   
 [Команда SET EXACT](../../odbc/microsoft/set-exact-command.md)
