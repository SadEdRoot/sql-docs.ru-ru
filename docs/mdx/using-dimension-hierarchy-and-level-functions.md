---
title: "Используя измерения, иерархии и функции уровней | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- dimensions [Analysis Services], functions
- level functions [MDX]
- hierarchy functions [MDX]
ms.assetid: e730f65a-1798-4094-9acf-2739e2505d52
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 10996fe3bec61356308a59ef78e52ecfeacca95a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="using-dimension-hierarchy-and-level-functions"></a>Функции измерений, иерархий и уровней
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Функции измерений, иерархий и уровней применяются для обхода многомерных структур в службах Analysis Services. Обычно они используются совместно с другими функциями для получения сведений об элементах измерения, иерархии или уровня.  
  
 В следующем примере показано, как использовать **. Измерение**, **. Иерархия**, и **. Уровень** функции:  
  
 `WITH`  
  
 `MEMBER MEASURES.DIMENSIONNAME AS [Date].[Calendar].CURRENTMEMBER.DIMENSION.NAME`  
  
 `MEMBER MEASURES.HIERARCHYNAME AS [Date].[Calendar].CURRENTMEMBER.HIERARCHY.NAME`  
  
 `MEMBER MEASURES.LEVELNAME AS [Date].[Calendar].LEVEL.NAME`  
  
 `SELECT`  
  
 `{MEASURES.DIMENSIONNAME, MEASURES.HIERARCHYNAME, MEASURES.LEVELNAME}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Измерения &#40; Многомерные Выражения &#41;](../mdx/dimension-mdx.md)   
 [Функции &#40; Синтаксис многомерных Выражений &#41;](../mdx/functions-mdx-syntax.md)   
 [Иерархия &#40; Многомерные Выражения &#41;](../mdx/hierarchy-mdx.md)   
 [Уровень &#40; Многомерные Выражения &#41;](../mdx/level-mdx.md)  
  
  
