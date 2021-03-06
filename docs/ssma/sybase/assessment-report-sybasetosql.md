---
title: Оценка отчетов (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 777fab9d35118b4cffab8ed8f947a4e91cb2480d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="assessment-report-sybasetosql"></a>Оценка отчетов (SybaseToSQL)
Окно отчета оценки показывает результаты преобразования объектов базы данных для [!INCLUDE[tsql](../../includes/tsql_md.md)] синтаксис, и поможет оценить сложность и стоимость проектов миграции.  
  
Доступ к отчету оценки, выбирать объекты для преобразования в обозревателе метаданных источника, щелкните правой кнопкой мыши **баз данных**, а затем выберите **создать отчет**.  
  
## <a name="options"></a>Параметры  
**Преобразование статистики**  
Показывает статистику типом оператора преобразования. В этой области отображается только тогда, когда объект группы, например схемы, или на панели слева выбран объект без кода.  
  
**Объекты по категориям**  
Показывает статистику преобразования по типу объекта. В этой области отображается только тогда, когда объект группы, например схемы, или на панели слева выбран объект без кода.  
  
**Статистика**  
Показывает статистику преобразования для выбранного объекта. В этой области отображается только при выборе отдельного объекта с кодом на панели слева. Может потребоваться развернуть **статистики** для просмотра этой панели.  
  
**Источник навигации**  
Показывает код ASE для выбранного объекта, а также код, который не был преобразован в [!INCLUDE[tsql](../../includes/tsql_md.md)]. В этой области отображается только при выборе отдельного объекта с кодом на панели слева.  
  
Щелкните номера строк, чтобы установить или снять закладки. Используйте кнопки в верхней части области перемещаться по коду.  
  
**Целевой навигации**  
Показывает что преобразование [!INCLUDE[tsql](../../includes/tsql_md.md)] код для выбранного объекта и сообщения об ошибках для кода, который не был преобразован. В этой области отображается только при выборе отдельного объекта с кодом на панели слева.  
  
Щелкните номера строк, чтобы установить или снять закладки. Используйте кнопки в верхней части области перемещаться по коду.  
  
**Панель сообщений**  
Показывает ошибки, предупреждения и информационные сообщения, которые создаются при создании отчета оценки. Сообщения группируются по номеру. Чтобы просмотреть код, который вызвал ошибку, нажмите кнопку **ошибка**, **предупреждение**, или **сведения**, разверните категорию сообщений и нажмите кнопку сообщения.  
  
