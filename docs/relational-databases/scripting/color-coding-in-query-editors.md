---
title: Выделение цветом в редакторах запросов | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], color coding
- color coding [Query Editor]
ms.assetid: 802882dc-c997-4e3f-8a01-994bb43169ae
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ff7f872d4e50069ca952510bb311bdbe6eb82cf9
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="color-coding-in-query-editors"></a>Выделение цветом в редакторах запросов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Тексту, который вводится в редакторах кода, присваивается категория. Каждая категория идентифицируется по цвету. Цвета помогают быстро находить текст в коде. Например, комментарии выделены темно-зеленым. В следующей таблице приведены наиболее часто применяемые цвета. Чтобы просмотреть полный список цветов и их категорий, а также настроить пользовательскую цветовую схему, в меню **Сервис**выберите пункт **Параметры** . Дополнительные сведения об изменении цветов по умолчанию см. в разделе [Change Font Color, Size, and Style](../../relational-databases/scripting/change-font-color-size-and-style.md).  
  
## <a name="default-code-colors"></a>Цвета по умолчанию  
  
|Color|Категория|  
|-----------|--------------|  
|Красный|Строка SQL|  
|Темно-зеленый|Комментарий|  
|Черный на серебристом фоне|Инструкция SQLCMD|  
|Пурпурный|Системная функция|  
|Зеленый|Системная таблица, представление или функция с табличным значением. А также системные схемы sys и INFORMATION_SCHEMA.|  
|Синий|Ключевое слово|  
|Бирюзовый|Номера строк или параметр шаблона|  
|Каштановый|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранимая процедура|  
|Темно-серый|Операторы|  
  
## <a name="status-bar"></a>Строка состояния  
 Можно назначить зарегистрированным серверам или серверам компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в обозревателе объектов различные цвета в строке состояния редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Это поможет идентифицировать, к какому серверу подключено каждое из окон редактора, когда одновременно открыто много окон. Дополнительные сведения о настройке цветов строки состояния см. в статье [Строка состояния (редактор запросов компонента Database Engine)](../../relational-databases/scripting/status-bar-database-engine-query-editor.md).  
  
 В некоторых редакторах строка состояния не отображается, либо не поддерживается несколько цветов.  
  
  
