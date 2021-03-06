---
title: TopCount (расширения интеллектуального анализа данных) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TOPCOUNT
dev_langs:
- DMX
helpviewer_keywords:
- TopCount function
ms.assetid: cbe031c9-4ff0-45df-9810-ebaebacf161d
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 48a53d01219290dd50bd192a6ee2adf5b51ad7b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="topcount-dmx"></a>TopCount (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Возвращает заданное в инструкции количество верхних строк в порядке убывания их ранга как указано в выражении.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
TopCount(<table expression>, <rank expression>, <count>)  
```  
  
## <a name="applies-to"></a>Объект применения  
 Выражение, возвращающее таблицу, такие как \<таблице ссылку на столбец >, или функции, возвращающей таблицу.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 \<Таблица выражения >  
  
## <a name="remarks"></a>Замечания  
 Значение, которое предоставляется свойством \<ранжирования выражение > аргумент определяет порядок убывания ранга строк, полученных из \<таблицы выражение > аргумента и количество верхних строк, которые указаны в \<count > возвращается аргумент.  
  
 Функция TopCount первоначально предназначалась для проведения ассоциативных прогнозов и правило, она возвращает те же результаты, как инструкция, включающая **выбрать первые** и **ORDER BY** предложения. При использовании получат более высокую производительность ассоциативного прогнозирования **прогнозирования (расширения интеллектуального анализа данных)** функции, которая поддерживает Указание количества возвращаемых прогнозов.  
  
 Однако существуют ситуации, где может по-прежнему необходимо использовать TopCount. Например, расширения интеллектуального анализа данных не поддерживает **ВЕРХНЕЙ** квалификатор в инструкции подзапроса выборки. [PredictHistogram &#40;расширений интеллектуального анализа данных&#41; ](../dmx/predicthistogram-dmx.md) функция также не поддерживает добавление **ВЕРХНЕЙ**.  
  
## <a name="examples"></a>Примеры  
 Следующие примеры являются прогнозирующими запросами к модели взаимосвязей, которая создается с помощью [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Запросы возвращают одинаковые результаты, но в первом примере используется TopCount во втором примере используется функция Predict.  
  
 Чтобы понять, как работает TopCount, возможно, лучше будет сначала выполнить прогнозирующий запрос, который возвращает только вложенную таблицу.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  В этом примере значение, заданное в качестве входных данных, содержит знак одинарной кавычки, а значит, его нужно экранировать и добавить перед ним еще один знак кавычки. При отсутствии уверенности в синтаксических конструкциях, используемых для вставки escape-символа, запросы можно создавать с помощью построителя прогнозирующих запросов. При выборе значения из раскрывающегося списка необходимый escape-символ вставляется автоматически. Дополнительные сведения см. в разделе [создать одноэлементный запрос в конструкторе интеллектуального анализа данных](../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md).  
  
 Пример результатов:  
  
|Модель|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Фляга для воды|2866|0.192620472|0.175205052|  
|Ремонтный комплект|2113|0.142012232|0.132389356|  
|Камера шины для велосипеда Mountain|1992|0.133879965|0.125304948|  
|Велосипед Mountain-200|1755|0.117951475|0.111260823|  
|Камера шины для шоссейного велосипеда|1588|0.106727603|0.101229538|  
|Велосипедная шапочка|1473|0.098998589|0.094256014|  
|Набор крыльев для велосипеда Mountain|1415|0.095100477|0.090718432|  
|Держатель фляги для велосипеда Mountain|1367|0.091874454|0.087780332|  
|Держатель фляги для шоссейного велосипеда|1195|0.080314537|0.077173962|  
  
 Функция TopCount принимает результаты этого запроса и возвращает заданное число строк с наименьшими значениями.  
  
```  
SELECT   
TopCount  
    (  
    Predict ([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $SUPPORT,  
    3)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Функция TopCount первый аргумент является имя столбца таблицы. В этом примере вложенной таблицы возвращается путем вызова функции прогнозирования и использовать аргумент INCLUDE_STATISTICS.  
  
 Функция TopCount второй аргумент является столбец во вложенной таблице, которая используется для упорядочивания результатов. В этом примере параметр INCLUDE_STATISTICS возвращает столбцы $SUPPORT, $PROBABILTY и $ADJUSTED PROBABILITY. В данном примере используется столбец $SUPPORT для ранжирования результатов.  
  
 Третий аргумент функции TopCount указывает количество строк, которые возвращаются в виде целого числа. Чтобы получить три верхних продукта, упорядоченных по столбцу $SUPPORT, введите 3.  
  
 Пример результатов:  
  
|Модель|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.29…|0.25…|  
|Фляга для воды|2866|0.19…|0.17…|  
|Ремонтный комплект|2113|0.14…|0.13…|  
  
 Однако данный тип запроса может повлиять на производительность в производственных условиях. Причина этого заключается в том, что запрос получает из алгоритма полный набор прогнозов, сортирует их и возвращает первые 3.  
  
 Следующий пример демонстрирует альтернативную инструкцию, которая возвращает тот же результат, но выполняется значительно быстрее. Этот пример заменяет TopCount функции прогноза, которая принимает количество прогнозов в качестве аргумента. В этом примере также используется **$SUPPORT** ключевое слово для получения непосредственно столбца вложенной таблицы.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3, $SUPPORT)  
```  
  
 Результаты содержат первые 3 прогноза, отсортированные по значению поддержки. Можно заменить $SUPPORT на $PROBABILITY или $ADJUSTED_PROBABILITY, чтобы получить прогнозы, ранжированные по вероятности или скорректированной вероятности. Дополнительные сведения см. в разделе **прогнозирования (расширения интеллектуального анализа данных)**.  
  
## <a name="see-also"></a>См. также  
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)   
 [BottomCount &#40;расширений интеллектуального анализа данных&#41;](../dmx/bottomcount-dmx.md)   
 [TopPercent &#40;расширений интеллектуального анализа данных&#41;](../dmx/toppercent-dmx.md)   
 [TopSum &#40;расширений интеллектуального анализа данных&#41;](../dmx/topsum-dmx.md)  
  
  
