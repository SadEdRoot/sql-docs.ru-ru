---
title: "Спарклайны и гистограммы (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rtp.rptdesigner.sparklines.f1
- "10544"
ms.assetid: b287436b-fa48-4970-a1a7-1dbcb86e7411
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6021dec1c7d072041710c62a533d4e19ead4aa53
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="sparklines-and-data-bars-report-builder-and-ssrs"></a>Спарклайны и гистограммы (построитель отчетов и службы SSRS)
  Sparkline-графики и гистограммы — это небольшие простые диаграммы, которые содержат много сведений в небольшом пространстве и часто бывают встроены в текст.   
    
  В отчетах [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] спарклайны и гистограммы часто используются в таблицах и матрицах. Их преимуществом является возможность просматривать большое их количество одновременно и быстро сравнивать их друг с другом, без необходимости просматривать каждое изображение отдельно. На них удобно смотреть выбросы, строки, отличающиеся от других. Хотя они небольшие, каждый спарклайн часто представляет множественные точки данных, часто во времени. Гистограммы могут представлять несколько точек данных, но, как правило, иллюстрируют только одну. Каждый спарклайн обычно представляет отдельный ряд. Спарклайн нельзя добавить к группе сведений в таблице. Sparkline-графики отображают статистические данные, поэтому должны входить в ячейку, которая связана с группой. Sparkline-графики и гистограммы данных имеют одни и те же основные элементы диаграммы категорий, рядов и значений, но не содержат какие-либо условные обозначения, линии осей, метки или деления.  
  
 ![rs_SparklineExample](../../reporting-services/report-design/media/rs-sparklineexample.gif "rs_SparklineExample")  
  
 Чтобы начать работу со спарклайнами, см. раздел [Учебник. Добавление спарклайна в отчет (построитель отчетов)](../../reporting-services/tutorial-add-a-sparkline-to-your-report-report-builder.md) и видеоролики [Инструкции. Создание спарклайна в таблице](http://go.microsoft.com/fwlink/?LinkId=197092) и [Спарклайны, линейчатые диаграммы и индикаторы в построителе отчетов](http://technet.microsoft.com/bi/video/ff877165) .  
  
> [!NOTE]  
>  Спарклайны и гистограммы можно опубликовать вместе с родительской таблицей, матрицей или списком, а также отдельно как элемент отчета. Узнайте больше об [элементах отчета](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md).  
  
##  <a name="KindsofSparklines"></a> Типы sparkline-графиков  
 Можно создать практически столько же типов sparkline-графиков, сколько и обычных диаграмм. Обычно нельзя создать трехмерный sparkline-график. Можно создать версию спарклайн-графика для следующих полных диаграмм:  
  
-   [Гистограмма с накоплением &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md): Basic, нормированные и нормированные гистограммы.  
  
-   [Графики &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/line-charts-report-builder-and-ssrs.md): Все, кроме трехмерного график.  
  
-   [Диаграммы с областями &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/area-charts-report-builder-and-ssrs.md): Все, кроме трехмерных диаграмм с областями  
  
-   [Круговые диаграммы &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md): И кольцевые диаграммы, плоские и трехмерные, но не других форм, такие как воронкообразная и Пирамидальная диаграммы.  
  
-   [Диаграммы диапазонов (построитель отчетов и службы SSRS)](../../reporting-services/report-design/range-charts-report-builder-and-ssrs.md). Биржевая диаграмма, диаграмма "японские свечи", линейчатая диаграмма погрешностей и блочная диаграмма.  
  
##  <a name="DataBars"></a> Гистограммы  
 Гистограммы обычно используются для представления одной точки данных, хотя могут представлять и несколько, как обычные линейчатые диаграммы. Часто они содержат несколько рядов без категорий или групп рядов.  
  
 ![rs_DataBars](../../reporting-services/report-design/media/rs-databars.gif "rs_DataBars")  
  
 В этом примере использована линейчатой диаграммы с накоплениями в каждой гистограмме, хотя только одна из них иллюстрирует больше чем одну точку данных. Например три разных цвета на ней могут показывать задачи трех уровней приоритетов, а длина представляет собой общее число задач, назначенных каждому. Если в этом случае использовать нормированную гистограмму, каждый столбец будет заполнять ячейку и разные цвета будут представлять проценты от общего объема для каждого уровня приоритета.  
  
 Можно сделать версию гистограммы для следующих полных диаграмм:  
  
-   [Линейчатые диаграммы &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md): Basic, с накоплением и 100% линейчатые диаграммы с накоплением.  
  
-   [Гистограмма с накоплением &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md): Basic, с накоплением и нормированная гистограмма с накоплением. Гистограмма может быть и sparline-графиком и гистограммой.  
  
##  <a name="AlignDatainTableMatrix"></a> Выравнивание данных спарклайнов в таблице или матрице  
 При вставке спарклайна в таблицу или матрицу обычно важно выровнять каждую точку на графике с точками на других графиках в столбце. Иначе будет сложно сравнивать данные из разных строк. Например, при сравнении месячных данных о продажах для разных продавцов в компании надо будет выровнять данные по месяцу. Если работник не работал в апреле, там не будет данных для него. Чтобы показать пробел для этого месяца и просмотреть данные следующих месяцев, необходимо провести выравнивание с данными других сотрудников. Это можно сделать путем выравнивания по горизонтальной оси. Дополнительные сведения см. в разделе о sparkline-график в [область выражения для итогов, статистические выражения и встроенных коллекций &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)и в разделе [выравнивание данных в диаграмме в таблице или матрице &#40; Построитель отчетов и службы SSRS &#41; ](../../reporting-services/report-design/align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md).  
  
 Также для сравнения по строкам данные нужно выравнивать вертикально, то есть высота столбцов или линий на спарклайнах или гистограммах должна быть задана относительно высоты всех остальных столбцов или линий на других спарклайнах или гистограммах. Иначе нельзя будет сравнивать строки между собой.  
  
 ![rs_SparklineAlignData](../../reporting-services/report-design/media/rs-sparklinealigndata.gif "rs_SparklineAlignData")  
  
 На этом изображении на гистограмме отображаются значения продаж за день для всех сотрудников. Обратите внимание, что для дней, когда у сотрудников нет продаж, на гистограмме остается пустая область и выравниваются последующие дни. Это пример горизонтального выравнивания. Также обратите внимание, что для некоторых работников столбец короткий и ни один столбец не достигает вершины ячейки. Это пример вертикального выравнивания, без которого в строках с невысокими столбцами короткие столбцы удлиняются для заполнения всей высоты ячейки.  
  
##  <a name="UnderstandScope"></a> Основные сведения о данных, используемых в спарклайнах и гистограммах  
 При добавлении спарклайна или гистограммы в таблицу или матрицу это интерпретируется как *вложение* одной области в другую. Вложение означает, что данные в спарклайне или гистограмме управляются набором данных таблицы или матрицы. Дополнительные сведения см. в разделе [Вложенные области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/nested-data-regions-report-builder-and-ssrs.md).  
  
##  <a name="ConvertSparklinetoChart"></a> Преобразование спарклайн-графиков или гистограмм в полную диаграмму  
 Поскольку спарклайны и гистограммы являются просто видами диаграмм, то при необходимости их можно преобразовать в полную диаграмму, щелкнув правой кнопкой мыши диаграмму и выбрав пункт **Преобразовать в полную диаграмму**. После этого линии осей, метки, деления и условные обозначения добавляются автоматически.  
  
> [!NOTE]  
>  Преобразовать полную диаграмму в спарклайн-график или гистограмму одним щелчком нельзя. Однако можно создать спарклайн-график или гистограмму из полной диаграммы, просто удалив все элементы, которые не присутствуют на спарклайн-графике или гистограмме.  
  
##  <a name="HowTo"></a> Инструкции  
 [Добавление спарклайнов и гистограмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
 [Выравнивание данных в диаграмме в таблице или матрице (построитель отчетов и службы SSRS)](../../reporting-services/report-design/align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
### <a name="other-how-to-topics-for-charts"></a>Другие инструкции для диаграмм  
 Поскольку sparkline-графики или гистограммы являются разновидностью диаграмм, следующие инструкции могут оказаться полезными при работе с ними.  
  
 [Добавление диаграммы в отчет (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)  
  
 [Добавление пустых точек на диаграмму (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
 [Добавление или удаление полей из диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-or-remove-margins-from-a-chart-report-builder-and-ssrs.md)  
  
 [Изменение типа диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/change-a-chart-type-report-builder-and-ssrs.md)  
  
 [Задание цветов диаграммы с помощью палитры (построитель отчетов и службы SSRS)](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)  
  
 [Отображение всплывающих подсказок для ряда (построитель отчетов и службы SSRS)](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
 [Задание логарифмической шкалы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-a-logarithmic-scale-report-builder-and-ssrs.md)  
  
 [Задание интервала оси (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  
  
 [Указание согласованных цветов для нескольких фигурных диаграмм (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Учебник: Добавление спарклайна в отчет &#40; Построитель отчетов &#41;](../../reporting-services/tutorial-add-a-sparkline-to-your-report-report-builder.md)   
  
  