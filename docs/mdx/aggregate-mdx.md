---
title: Статистическое выражение (MDX) | Документы Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31fc7fe749d8e14f0e18ea88128d984875cdaa31
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578426"
---
# <a name="aggregate-mdx"></a>Aggregate (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает значение, вычисленное статистической обработкой ячеек, возвращаемых выражением набора. Если числовое выражение отсутствует, функция статистически обрабатывает каждую меру в контексте текущего запроса, используя статистический оператор, заданный для каждой меры. Если числовое выражение предоставлено, эта функция сначала вычисляет, затем суммирует числовое выражение для каждой ячейки в заданном наборе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Aggregate(Set_Expression [ ,Numeric_Expression ])  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Numeric_Expression*  
 Допустимое числовое выражение (обычно многомерное выражение координат ячейки), возвращающее число.  
  
## <a name="remarks"></a>Примечания  
 Если задан набор пустых кортежей или пустой набор, функция возвращает пустое значение.  
  
 В следующей таблице описаны как **статистические** результаты, возвращаемые функцией различных статистических функций.  
  
|Статистический оператор|Результат|  
|--------------------------|------------|  
|SUM|Возвращает сумму значений в наборе.|  
|Count|Возвращает количество значений в наборе.|  
|Max|Возвращает максимальное значение в наборе.|  
|Min|Возвращает минимальное значение в наборе.|  
|Полуаддитивные статистические функции|Вычисляет полуаддитивные статистические функции над набором после проецирования формы на ось времени.|  
|Количество различных|Возвращает статистическое вычисление по данным из таблицы фактов, включаемым во вложенный куб, если ось среза содержит набор.<br /><br /> Возвращает число различных объектов для каждого элемента набора. Результат зависит от безопасности ячеек, которые будут обрабатываться, но не от безопасности ячеек, которые требуются для вычисления. Безопасность ячейки в наборе создает ошибку, безопасность ячейки уровнем ниже гранулярности заданного набора не учитывается. Вычисления над набором вызывают ошибку. Вычисления со степенью гранулярности ниже гранулярности набора не учитываются. Счетчик различных объектов в наборе, включающий в себя элемент и один или более его дочерних объектов, возвращает счетчик различных фактов, использовавшихся в дочернем элементе.|  
|Атрибуты, которые нельзя вычислять|Возвращает сумму значений.|  
|Смешанные статистические функции|Не поддерживаются, вызывают ошибку.|  
|Унарные операторы|Не учитываются; значения суммируются.|  
|Вычисляемые меры|Задается порядок вычисления для применения вычисляемой меры.|  
|Вычисляемые элементы|Используются обычные правила, приоритет у последнего порядка вычисления.|  
|Назначения|Назначения обрабатываются статистически соответственно статистической функции обработки мер. Если функция статистической обработки мер является счетчиком различных объектов, назначение суммируется.|  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается сумма `Measures.[Order Quantity]` член, суммарный за первые восемь месяцев календарного 2003, содержащихся в `Date` измерения, от **Adventure Works** куба.  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 В следующем примере выполняются статистические вычисления за первые два месяца второго полугодия 2003 календарного года.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 В следующем примере возвращается количество посредников, продажи которых снизились по сравнению с предыдущим периодом, на основании выбранных пользователем значений элемента State-Province, вычисленных с помощью агрегатной функции. **Hierarchize** и **DrillDownLevel** функции используются для возвращения показателей падения продаж для категорий продуктов в измерении Product.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>См. также  
 [PeriodsToDate &#40;многомерных Выражений&#41;](../mdx/periodstodate-mdx.md)   
 [Дочерние элементы &#40;многомерных Выражений&#41;](../mdx/children-mdx.md)   
 [Hierarchize &#40;многомерных Выражений&#41;](../mdx/hierarchize-mdx.md)   
 [Число &#40;задать&#41; &#40;многомерных Выражений&#41;](../mdx/count-set-mdx.md)   
 [Фильтр &#40;многомерных Выражений&#41;](../mdx/filter-mdx.md)   
 [AddCalculatedMembers &#40;многомерных Выражений&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel &#40;многомерных Выражений&#41;](../mdx/drilldownlevel-mdx.md)   
 [Свойства &#40;многомерных Выражений&#41;](../mdx/properties-mdx.md)   
 [PrevMember &#40;многомерных Выражений&#41;](../mdx/prevmember-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40;многомерных Выражений&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
