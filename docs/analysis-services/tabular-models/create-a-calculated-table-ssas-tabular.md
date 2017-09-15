---
title: "Создание вычисляемой таблицы (табличные службы SSAS) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d7ff98a-82a9-4333-a7d3-7a95a6f2caf7
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e7db92207b2a518c3d697b997a22ed7c076cd0b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-calculated-table-ssas-tabular"></a>Создание вычисляемой таблицы (табличные службы SSAS)
  *Вычисляемая таблица* представляет собой объект, вычисляемый на основе выражения или запроса DAX и наследуемый (полностью или частично) от других таблиц в той же модели.  
  
 Основной задачей, решаемой с помощью вычисляемых таблиц, является подключение ролевого измерения в определенном контексте, чтобы представить его в виде структуры запроса в клиентских приложениях.  Как вы помните, ролевое измерение — это таблица, подключаемая в нескольких контекстах. В качестве классического примера можно привести таблицу Date, которая представляется как OrderDate, ShipDate или DueDate в зависимости от связи по внешнему ключу. Создав вычисляемую таблицу для ShipDate, вы получите автономную таблицу, к которой можно отправлять запросы и с которой можно работать так же, как с любой другой таблицей.  
  
 Вторым вариантом использования вычисляемых таблиц является настройка отфильтрованного набора строк либо подмножества или супермножества столбцов из других существующих таблиц. Это позволяет сохранить исходную таблицу без изменений, создавая ее варианты для решения определенных задач.  
  
 Для максимально эффективного использования вычисляемых таблиц потребуются определенные знания DAX. При работе с выражениями таблицы полезным будем знать, что вычисляемая таблица содержит один раздел с DAXSource, выражение которого является выражением DAX.  
Для каждого столбца, возвращаемого выражением, имеется один столбец CalculatedTableColumn, где SourceColumn — это имя возвращенного столбца (аналогично с DataColumn для невычисляемых таблиц).  
  
## <a name="how-to-create-a-calculated-table"></a>Создание вычисляемой таблицы  
  
1.  Во-первых убедитесь, что табличная модель имеет уровень совместимости 1200 или выше. Он указан в свойстве **Уровень совместимости** модели в SSDT.  
  
2.  Перейдите в представление данных. В представлении диаграммы создать вычисляемую таблицу нельзя.  
  
3.  Выберите **Таблица** > **Новая вычисляемая таблица**.  
  
4.  Введите или вставьте выражение DAX (ниже приведено несколько примеров).  
  
5.  Дайте таблице имя.  
  
6.  Создайте связи с другими таблицами в модели. Если вам нужна помощь с выполнением этого шага, см. статью [Создание связи между двумя таблицами (табличные службы SSAS)](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
7.  Добавьте ссылки на таблицу в вычислениях или выражениях вашей модели либо воспользуйтесь функцией **Анализ в Excel** для нерегламентированного анализа данных.  
  
### <a name="replicate-a-role-playing-dimension"></a>Репликация ролевого измерения  
 В строке формулы введите формулу DAX, которая получает копию другой таблицы. Когда вычисляемая таблица будет заполнена, присвойте ей описательное имя и настройте отношение, которое использует внешний ключ, относящийся к роли. Например, в базе данных Adventure Works можно создать вычисляемую таблицу дат выполнения и использовать DueDateKey в качестве основания связи с таблицей фактов.  
  
```  
=DimDate  
```  
  
### <a name="summarized-or-filtered-dataset"></a>Сводный или отфильтрованный набор данных  
 В строке формул введите выражение DAX, которое фильтрует, суммирует или иным образом обрабатывает набор данных, чтобы он содержал нужные вам строки. В этом примере выполняется группировка по цвету и валюте.  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### <a name="superset-using-columns-from-multiple-tables"></a>Супермножество для столбцов из нескольких таблиц  
 В строке формул введите выражение DAX, которое объединяет столбцы из нескольких таблиц. В этом случае результатом запроса является список категорий продуктов по каждой валюте.  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## <a name="see-also"></a>См. также  
 [Уровень совместимости табличных моделей в службах Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Выражения анализа данных &#40; DAX &#41; в службах Analysis Services](http://msdn.microsoft.com/library/abb336c9-3346-4cab-b91b-90f93f4575e5)   
 [Основные сведения о DAX в табличных моделях (табличные службы SSAS)](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  