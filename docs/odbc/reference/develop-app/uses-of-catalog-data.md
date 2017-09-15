---
title: "Использует данных каталога | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61a112f126eb83d40e350c5cc275f28438f15383
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="uses-of-catalog-data"></a>Использует данных каталога
Приложения используют данные каталога в различными способами. Ниже приведены некоторые распространенные варианты.  
  
-   **Создание инструкций SQL во время выполнения.** Вертикальные приложения, такие как приложение для ввода заказов, содержащих инструкции SQL, жестко. Таблицы и столбцы, используемые приложением фиксируются заранее, как инструкции, которые обращаются к этим таблицам. Например, приложение для ввода заказов обычно содержит один параметризованный **вставить** инструкции для добавления новых заказов в систему.  
  
     Универсальные приложения, такие как программы электронной таблицы, использующей ODBC для получения данных, часто создания инструкций SQL во время выполнения на основе ввода пользователя. Такое приложение может потребовать пользователю ввести имена таблиц и столбцов для использования. Однако было бы проще для пользователя, если приложение отображается список таблиц и столбцов, из которых пользователь может выбрать. Чтобы построить эти списки, приложение будет вызывать **SQLTables** и **SQLColumns** функции каталога.  
  
-   **Создание инструкций SQL во время разработки.** Для сред разработки приложения обычно позволяют программистам возможность создавать запросы к базе данных во время разработки программы. Запросы будут жестко запрограммированы в создаваемого приложения.  
  
     Также можно использовать такие среды **SQLTables** и **SQLColumns** для создания списков, из которых программист может нужные значения. Также можно использовать эти среды **SQLPrimaryKeys** и **SQLForeignKeys** автоматически определить и Показать связи между выбранными таблицами и использовать **SQLStatistics** для определения и выделите индексированные поля, чтобы программист могут создавать эффективные запросы.  
  
-   **Создав курсоров.** Может использовать приложения, драйвера или по промежуточного слоя, который предоставляет механизм Прокручиваемый курсор **SQLSpecialColumns** для определения, какие столбцы или столбец однозначно идентифицировать строку. Программа может собрать *ключей* содержит значения этих столбцов для каждой строки, выбранных. Когда приложение выполняет прокрутку к строке, он будет затем использовать эти значения для выборки самые последние данные для строки. Дополнительные сведения о Прокручиваемые курсоры и наборы ключей см. в разделе [Прокручиваемые курсоры](../../../odbc/reference/develop-app/scrollable-cursors.md).