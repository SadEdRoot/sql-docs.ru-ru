---
title: ParallelPeriod (многомерные Выражения) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8cde031af19fff309520cd72e145b6c04dc19d9c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580826"
---
# <a name="parallelperiod-mdx"></a>ParallelPeriod (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает элемент предыдущего периода, расположенный в той же относительной позиции, что и заданный элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ParallelPeriod( [ Level_Expression [ ,Index [ , Member_Expression ] ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Index*  
 Допустимое числовое выражение, указывающее количество параллельных периодов для отставания.  
  
 *Member_Expression.*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Примечания  
 Несмотря на сходство с [Cousin](../mdx/cousin-mdx.md) функции **ParallelPeriod** функции более тесно связана с временным рядом. **ParallelPeriod** функция берет предок заданного элемента на заданном уровне, находит родственный элемент предка с указан и наконец возвращает параллельный период среди потомков того же уровня заданного элемента.  
  
 **ParallelPeriod** функция имеет следующие значения по умолчанию:  
  
-   Если ни выражение уровня, ни выражение элемента указано, значение элемента по умолчанию используется текущий элемент первой иерархии первого измерения с типом *время* в группе мер.  
  
-   Если выражение уровня указано, но выражение элемента не указано, значение элемента по умолчанию — *Level_Expression*. **Hierarchy.CurrentMember**.  
  
-   Значение Index по умолчанию равно 1.  
  
-   Уровень по умолчанию соответствует уровню родительского элемента для указанного элемента.  
  
 **ParallelPeriod** функция эквивалентна следующей инструкции многомерных Выражений:  
  
 `Cousin(Member_Expression, Ancestor(Member_Expression, Level_Expression) .Lag(Numeric_Expression))`  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается параллельный период для октября 2003 г. с отставанием в три периода, основанный на квартальном уровне, будет возвращен январь 2003 г.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Quarter]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 В следующем примере возвращается параллельный период для октября 2003 г. с отставанием в три периода, основанный на полугодовом уровне, будет возвращен апрель 2002 г.  
  
```  
SELECT ParallelPeriod ([Date].[Calendar].[Calendar Semester]  
   , 3  
   , [Date].[Calendar].[Month].[October 2003])  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
