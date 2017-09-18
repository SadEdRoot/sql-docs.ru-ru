---
title: "NOT NULL в инструкции CREATE TABLE | Документы Microsoft"
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
- not null [ODBC]
- interoperability [ODBC], not null
ms.assetid: 3fb69943-f0c9-4ed2-aa42-20440e37e49d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc96de9df9724e500709488054b3357b3c7e50aa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="not-null-in-create-table-statements"></a>NOT NULL в инструкции CREATE TABLE
Некоторые и особенно системной базы данных, не поддерживают **NOT NULL** ограничение столбца в **CREATE TABLE** инструкции. Дополнительные сведения см. в разделе параметр SQL_NON_NULLABLE_COLUMNS в [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.