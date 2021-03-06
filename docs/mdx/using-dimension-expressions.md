---
title: Использование выражений измерений | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f680c5478eb1ee03fd69506d669fbc49c91c0241
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582496"
---
# <a name="using-dimension-expressions"></a>Использование выражений измерений
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Как правило, выражения измерений и иерархий используются при передаче параметров в функции многомерных выражений для получения элементов, наборов или кортежей из иерархии.  
  
 Выражения измерений могут быть только простыми выражениями, так как являются идентификаторами объектов. В разделе [выражений &#40;многомерных Выражений&#41; ](../mdx/expressions-mdx.md) объяснение простых и сложных выражений.  
  
## <a name="dimension-expressions"></a>Выражения измерений  
 Выражение измерения содержит идентификатор измерения или функцию измерения.  
  
 Выражения измерений редко используются самостоятельно. Обычно нужно задать иерархию в измерении. Единственное исключение — измерение Measures, в котором нет иерархий.  
  
 В следующем примере показан вычисляемый элемент, в котором выражение [Measures] используется с функциями .Members и Count(), чтобы получить количество элементов в измерении Measures:  
  
 `WITH MEMBER [Measures].[MeasureCount] AS`  
  
 `COUNT([Measures].MEMBERS)`  
  
 `SELECT [Measures].[MeasureCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Идентификатор измерения представлен как *Dimension_Name* в форме БЭКУСА-Наура, используемой для описания инструкций многомерных Выражений.  
  
## <a name="hierarchy-expressions"></a>Выражения иерархии  
 Аналогично выражение иерархии содержит идентификатор иерархии или функцию иерархии. В следующем примере показано использование выражения иерархии [Дата].[Календарь] с функциями .Levels и .Count, чтобы возвратить количество уровней в иерархии «Календарь» измерения «Дата»:  
  
 `WITH MEMBER [Measures].[CalendarLevelCount] AS`  
  
 `[Date].[Calendar].Levels.Count`  
  
 `SELECT [Measures].[CalendarLevelCount] ON 0`  
  
 `FROM [Adventure Works]`  
  
 Чаще всего выражения иерархии используются вместе с функцией .Members, чтобы получить все элементы иерархии. В следующем примере возвращаются все элементы иерархии [Дата].[Календарь] по оси строк:  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Идентификатор иерархии представлен как *Dimension_Name **.** Hierarchy_Name* в форме БЭКУСА-Наура, используемой для описания инструкций многомерных Выражений.  
  
## <a name="see-also"></a>См. также  
 [Выражения &#40;многомерных Выражений&#41;](../mdx/expressions-mdx.md)  
  
  
