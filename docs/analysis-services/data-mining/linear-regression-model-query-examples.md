---
title: Примеры запросов модели линейной регрессии | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e967bcb024a20c09105447780e5d672d4dc843fa
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="linear-regression-model-query-examples"></a>Примеры запросов модели линейной регрессии
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  К модели интеллектуального анализа данных можно создать два вида запросов: запросы содержимого, возвращающие подробные сведения о закономерностях, обнаруженных при анализе, и прогнозирующие запросы, использующие закономерности, содержащиеся в модели, для прогнозирования новых данных. Например, запрос содержимого предоставит дополнительные сведения о формуле регрессии, а прогнозирующий запрос определит, подходит ли к модели новая точка данных. Запрос также позволяет получить метаданные, описывающие модель.  
  
 В этом разделе описывается процесс создания запросов к моделям, основанным на алгоритме линейной регрессии (Майкрософт).  
  
> [!NOTE]  
>  Поскольку линейная регрессия основана на частном случае алгоритма дерева принятия решений (Майкрософт), у них много общего, и некоторые модели деревьев решений с непрерывными прогнозируемыми атрибутами могут содержать формулы регрессии. Дополнительные сведения см. в разделе [Технический справочник по алгоритму дерева принятия решений (Майкрософт)](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md).  
  
 **Запросы содержимого**  
  
 [Определение параметров, использованных в модели, с помощью набора строк схемы интеллектуального анализа данных](#bkmk_Query1)  
  
 [Получение формулы регрессии модели с помощью расширений интеллектуального анализа данных](#bkmk_Query2)  
  
 [Возвращение только коэффициента для данной модели](#bkmk_Query3)  
  
 **Прогнозирующие запросы**  
  
 [Прогнозирование дохода с помощью одноэлементного запроса](#bkmk_Query4)  
  
 [Использование прогнозирующих функций в модели регрессии](#bkmk_Query5)  
  
##  <a name="bkmk_top"></a> Получение сведений о модели линейной регрессии  
 Структура модели линейной регрессии чрезвычайно проста: модель интеллектуального анализа данных представляет данные в виде одного узла, определяющего формулу регрессии. Дополнительные сведения см. в разделе [Содержимое моделей интеллектуального анализа данных для моделей логистической регрессии (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-logistic-regression-models.md).  
  
 [Вернуться в начало](#bkmk_top)  
  
###  <a name="bkmk_Query1"></a> Пример запроса 1. Определение параметров, использованных в модели, с помощью набора строк схемы интеллектуального анализа данных  
 Используя запросы к набору строк схемы интеллектуального анализа данных, можно получать метаданные модели. Они включают в себя, например, время создания модели, время ее последней обработки, имя структуры интеллектуального анализа данных, на которой основана данная модель, и имя столбца, назначенного в качестве прогнозируемого атрибута. Также можно возвратить параметры, которые были использованы при первичном создании модели.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_PredictIncome'  
```  
  
 Образец результатов.  
  
|MINING_PARAMETERS|  
|------------------------|  
|COMPLEXITY_PENALTY=0.9,<br /><br /> MAXIMUM_INPUT_ATTRIBUTES=255,<br /><br /> MAXIMUM_OUTPUT_ATTRIBUTES=255,<br /><br /> MINIMUM_SUPPORT=10,<br /><br /> SCORE_METHOD=4,<br /><br /> SPLIT_METHOD=3,<br /><br /> FORCE_REGRESSOR=|  
  
> [!NOTE]  
>  Значение параметра, "`FORCE_REGRESSOR =` ", указывает, что текущее значение параметра FORCE_REGRESSOR равно NULL.  
  
 [Вернуться в начало](#bkmk_top)  
  
###  <a name="bkmk_Query2"></a> Пример запроса 2. Получение формулы регрессии модели  
 Следующий запрос возвращает содержимое модели интеллектуального анализа данных с линейной регрессией, построенной для того же источника данных «Целевая рассылка», который использовался в пособии [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Эта модель предсказывает доход клиента на основании возраста.  
  
 Запрос возвращает содержимое узла модели интеллектуального анализа данных, содержащего формулу регрессии. Каждая переменная и коэффициент хранятся в отдельной строке вложенной таблицы NODE_DISTRIBUTION. Для просмотра полной формулы регрессии в [средстве просмотра деревьев (Майкрософт)](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md)нужно щелкнуть узел **(Все)** и открыть **Условные обозначения интеллектуального анализа данных**.  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION as t  
FROM LR_PredictIncome.CONTENT  
```  
  
> [!NOTE]  
>  При ссылках на отдельные столбцы вложенной таблицы в таких запросах, как `SELECT <column name> from NODE_DISTRIBUTION`, некоторые столбцы, например **SUPPORT** или **PROBABILITY**, нужно заключать в квадратные скобки, чтобы отличать их от одноименных зарезервированных ключевых слов.  
  
 Ожидаемый результат:  
  
|t.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VARIANCE|t.VALUETYPE|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|Годовой доход|Missing|0|0,000457142857142857|0|1|  
|Годовой доход|57220,8876687257|17484|0,999542857142857|1041275619,52776|3|  
|Возраст|471,687717702463|0|0|126.969442359327|7|  
|Возраст|234,680904692439|0|0|0|8|  
|Возраст|45,4269617936399|0|0|126,969442359327|9|  
||35793,5477381267|0|0|1012968919,28372|11|  
  
 Для сравнения, в окне **Условные обозначения интеллектуального анализа данных**формула регрессии показана в следующем виде:  
  
 `Yearly Income = 57,220.919 + 471.688 * (Age - 45.427)`  
  
 Можно видеть, что в окне **Условные обозначения интеллектуального анализа данных**некоторые числа округлены; однако по существу таблица NODE_DISTRIBUTION и окно **Условные обозначения интеллектуального анализа данных** содержат одни и те же значения.  
  
 Значения в столбце VALUETYPE сообщают, какая информация содержится в каждой строке. Это полезно при программной обработке результатов. В следующей таблице показаны типы значений, которые являются выводом формулы линейной регрессии.  
  
|VALUETYPE|  
|---------------|  
|1 (отсутствует)|  
|3 (непрерывный)|  
|7 (коэффициент)|  
|8 (рост оценки)|  
|9 (статистика)|  
|7 (коэффициент)|  
|8 (рост оценки)|  
|9 (статистика)|  
|11 (отсекаемый отрезок)|  
  
 Дополнительные сведения о назначении каждого из типов значений в моделях регрессии см. в разделе [Содержимое моделей интеллектуального анализа данных для моделей линейной регрессии (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).  
  
 [Вернуться в начало](#bkmk_top)  
  
###  <a name="bkmk_Query3"></a> Пример запроса 3. Возвращение только коэффициента для модели  
 Используя перечисление VALUETYPE, можно вернуть только коэффициент уравнения регрессии, как показано в следующем запросе:  
  
```  
SELECT FLATTENED MODEL_NAME,  
    (SELECT ATTRIBUTE_VALUE, VALUETYPE  
     FROM NODE_DISTRIBUTION  
     WHERE VALUETYPE = 11)   
AS t  
FROM LR_PredictIncome.CONTENT  
```  
  
 Этот запрос возвращает две строки — одну из содержимого модели интеллектуального анализа данных и одну из вложенной таблицы, с коэффициентом. Столбец ATTRIBUTE_NAME сюда не включается, потому что для коэффициента он всегда пустой.  
  
|MODEL_NAME|t.ATTRIBUTE_VALUE|t.VALUETYPE|  
|-----------------|------------------------|-----------------|  
|LR_PredictIncome|||  
|LR_PredictIncome|35793,5477381267|11|  
  
 [Вернуться в начало](#bkmk_top)  
  
## <a name="making-predictions-from-a-linear-regression-model"></a>Прогнозирование по модели линейной регрессии  
 Прогнозирующие запросы к модели линейной регрессии можно строить с помощью вкладки «Прогнозирование моделей интеллектуального анализа данных» конструктора интеллектуального анализа данных. Построитель прогнозирующих запросов доступен как в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , так и в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Можно также создавать запросы к моделям регрессии с помощью надстроек интеллектуального анализа данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] для Excel или [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] для Excel. Надстройки интеллектуального анализа данных для Excel не создают моделей регрессии, но позволяют просматривать любые модели интеллектуального анализа данных, хранящиеся в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], и создавать запросы к ним.  
  
 [Вернуться в начало](#bkmk_top)  
  
###  <a name="bkmk_Query4"></a> Пример запроса 4. Прогнозирование дохода с помощью одноэлементного запроса  
 Проще всего создать отдельный запрос к модели регрессии с помощью диалогового окна **Ввод одноэлементного запроса** . Например, можно построить следующий DMX-запрос, взяв подходящую модель регрессии, выбрав **Одноэлементный запрос**, а затем введя **20** в качестве значения атрибута **Возраст**.  
  
```  
SELECT [LR_PredictIncome].[Yearly Income]  
From   [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 Образец результатов.  
  
|Годовой доход|  
|-------------------|  
|45227,302092176|  
  
 [Вернуться в начало](#bkmk_top)  
  
###  <a name="bkmk_Query5"></a> Пример запроса 5. Использование прогнозирующих функций в модели регрессии  
 В моделях линейной регрессии можно использовать многие стандартные прогнозирующие функции. Далее приводится пример добавления некоторых описательных статистических показателей к результатам прогнозирующего запроса. По этим результатам можно понять, что в данной модели наблюдается значительное отклонение от средней величины.  
  
```  
SELECT  
  ([LR_PredictIncome].[Yearly Income]) as [PredIncome],  
  (PredictStdev([LR_PredictIncome].[Yearly Income])) as [StDev1]  
From  
  [LR_PredictIncome]  
NATURAL PREDICTION JOIN  
(SELECT 20 AS [Age]) AS t  
```  
  
 Образец результатов.  
  
|Годовой доход|StDev1|  
|-------------------|------------|  
|45227,302092176|31827,1726561396|  
  
 [Вернуться в начало](#bkmk_top)  
  
## <a name="list-of-prediction-functions"></a>Список прогнозирующих функций  
 Все алгоритмы [!INCLUDE[msCoName](../../includes/msconame-md.md)] поддерживают общий набор функций. Однако алгоритм линейной регрессии [!INCLUDE[msCoName](../../includes/msconame-md.md)] поддерживает дополнительные функции, приведенные в следующей таблице.  
  
|||  
|-|-|  
|прогнозирующую функцию|Использование|  
|[IsDescendant & #40; расширений интеллектуального анализа данных & #41;](../../dmx/isdescendant-dmx.md)|Определяет, является ли узел дочерним для другого узла модели.|  
|[IsInNode & #40; расширений интеллектуального анализа данных & #41;](../../dmx/isinnode-dmx.md)|Указывает, содержит ли заданный узел текущий вариант.|  
|[PredictHistogram & #40; расширений интеллектуального анализа данных & #41;](../../dmx/predicthistogram-dmx.md)|Возвращает прогнозируемое значение или набор значений для указанного столбца.|  
|[PredictNodeId & #40; расширений интеллектуального анализа данных & #41;](../../dmx/predictnodeid-dmx.md)|Возвращает параметр Node_ID для каждого случая.|  
|[PredictStdev & #40; расширений интеллектуального анализа данных & #41;](../../dmx/predictstdev-dmx.md)|Возвращает стандартное отклонение для прогнозируемого значения.|  
|[PredictSupport & #40; расширений интеллектуального анализа данных & #41;](../../dmx/predictsupport-dmx.md)|Возвращает опорное значение для указанного состояния.|  
|[PredictVariance & #40; расширений интеллектуального анализа данных & #41;](../../dmx/predictvariance-dmx.md)|Возвращает дисперсию указанного столбца.|  
  
 Список общих функций для всех алгоритмов [!INCLUDE[msCoName](../../includes/msconame-md.md)] см. в статье [Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md). Дополнительные сведения об использовании этих функций см. в разделе [Справочник по расширениям интеллектуального анализа данных](../../dmx/data-mining-extensions-dmx-function-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Алгоритм линейной регрессии Майкрософт](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md)   
 [Технический справочник по алгоритму линейной регрессии Майкрософт](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [Содержимое модели интеллектуального анализа данных для модели линейной регрессии & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
