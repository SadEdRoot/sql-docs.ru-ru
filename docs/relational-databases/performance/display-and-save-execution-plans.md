---
title: Отображение и сохранение планов выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 08/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Showplan results
- execution plans [SQL Server]
- queries [SQL Server], tuning
- execution plans [SQL Server], how-to topics
- SQL Server Management Studio [SQL Server], execution plans
- tuning queries [SQL Server]
ms.assetid: bcd6f094-c613-4835-ae19-4caaadb4bb17
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f37e5474f2cd531e95c2fa6de8a430ba1fd1c470
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="display-and-save-execution-plans"></a>Отображение и сохранение планов выполнения
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе объясняется, как отображать планы выполнения и как сохранять их в файл формата XML в среде Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Планы выполнения служат для графического отображения методов получения данных, выбранных оптимизатором запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Планы выполнения представляют стоимость выполнения определенных инструкций и запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде значков, а не таблиц, формируемых с помощью инструкций [SET SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md) и [SET SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md). Графический подход очень полезен для понимания характеристик производительности запроса.  

 Хотя оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] формирует только один план выполнения, существуют понятия **расчетного** плана выполнения и **фактического** плана выполнения.
 -  [Расчетный план выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md) возвращает план выполнения, созданный оптимизатором запросов во время компиляции. При формировании расчетного плана выполнения не выполняется никаких запросов или пакетов, поэтому расчетный план выполнения не содержит сведений времени выполнения, таких как фактические метрики использования ресурса и предупреждения времени выполнения. 
 -  [Фактический план выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md) возвращает план выполнения, созданный с помощью оптимизатора запросов, после завершения выполнения запросов или пакетов. Этот план включает сведения времени выполнения, такие как метрики использования ресурса и предупреждения времени выполнения.  

 Дополнительные сведения см. в разделе [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md).
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Отображение предполагаемого плана выполнения](../../relational-databases/performance/display-the-estimated-execution-plan.md)  
  
-   [Отображение действительного плана выполнения](../../relational-databases/performance/display-an-actual-execution-plan.md)  
  
-   [Сохранение плана выполнения в формате XML](../../relational-databases/performance/save-an-execution-plan-in-xml-format.md)  
  
  
