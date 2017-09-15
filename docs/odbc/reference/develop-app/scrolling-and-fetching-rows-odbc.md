---
title: "Прокрутка и выборка строк (ODBC) | Документы Microsoft"
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
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5b5a9aefccf51cc4b3aac1aeba02c7878c6dceed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="scrolling-and-fetching-rows-odbc"></a>Прокрутка и выборка строк (ODBC)
При использовании прокручиваемого курсора, вызовите приложений **SQLFetchScroll** позицию строки курсора и fetch. **SQLFetchScroll** поддерживает прокрутку относительных (следующего, предыдущего и относительно * n * строк), абсолютный прокрутки (имя, Фамилия, а строку * n *), и позиционирование по закладке. *FetchOrientation* и *FetchOffset* аргументов в **SQLFetchScroll** укажите какие набора строк для выборки, как показано на следующих диаграммах.  
  
 ![Выборка следующего, предыдущего, первого и последнего наборов строк](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Выборка следующего, предыдущего, первого и последнего набора строк**  
  
 ![Выборка абсолютных, относительных и закладками строк](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Выборка абсолютных, относительных и закладками набора строк**  
  
 **SQLFetchScroll** помещает курсор в указанную строку и возвращает строки в наборе строк, начиная с этой строки. Если указанный набор строк накладывается на конец результирующего набора, возвращается частичный набор строк. Если указанный набор строк перекрывается начала результата набором первый набор строк в результирующем наборе обычно возвращается; Дополнительные сведения см. [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) описание функции.  
  
 В некоторых случаях приложение может потребоваться курсор без получения всех данных. Например он может потребоваться проверка наличия строки или просто получить закладка для строки не перенос других данных по сети. Для этого он задает атрибут инструкции SQL_ATTR_RETRIEVE_DATA SQL_RD_OFF. Переменная, привязанное к столбцу закладки (если таковые имеются) всегда обновляется, независимо от значения этого атрибута инструкции.  
  
 После получения набора строк, приложение может вызвать **SQLSetPos** позицию для конкретной строки в набор строк или обновления строки в наборе строк. Дополнительные сведения об использовании **SQLSetPos**, в разделе [обновление данных с помощью SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Прокрутка поддерживается в ODBC 2. *x* драйверы с **SQLExtendedFetch**. Дополнительные сведения см. в разделе [блочных курсоров, Прокручиваемые курсоры и обратной совместимости](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)в приложении G: драйвер рекомендации для обеспечения обратной совместимости.