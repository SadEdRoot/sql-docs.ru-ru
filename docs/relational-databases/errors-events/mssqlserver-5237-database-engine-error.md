---
title: MSSQLSERVER_5237 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bb309a33b9c389a46bd869bb05956a4c247a95cf
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5237|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Текст сообщения|Перекрестная проверка наборов строк с помощью команды DBCC для объекта NAME (идентификатор объекта O_ID) окончилась неудачей, так как произошла внутренняя ошибка запроса.|  
  
## <a name="explanation"></a>Объяснение  
Внутренняя ошибка привела к тому, что в команде DBCC не удалось выполнить запрос для проверки индексированных представлений.  
  
## <a name="user-action"></a>Действие пользователя  
Повторно выполните команду DBCC.  
  
