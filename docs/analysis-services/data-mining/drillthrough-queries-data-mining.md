---
title: "Запросы детализации (интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AllowDrillThrough property
- drillthrough [Analysis Services]
- drillthrough [DMX]
ms.assetid: 246c784b-1b0c-4f0b-96f7-3af265e67051
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1cb15acfcc31572a34c6bf2fe6c3ec75101a9fd0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="drillthrough-queries-data-mining"></a>Запросы детализации (интеллектуальный анализ данных)
  *Запрос детализации* позволяет извлекать сведения из базовых вариантов или данных структуры, отсылая запрос в модель интеллектуального анализа данных. Детализация применяется в том случае, если нужно просмотреть варианты, использованные для обучения модели, в отличие от вариантов, которые используются для ее проверки, либо чтобы просмотреть дополнительных сведения из данных варианта.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предусматривает два различных варианта детализации.  
  
-   Детализация до **вариантов модели**  
  
     Детализация до вариантов модели используется для детализации из шаблона в модели, например кластера или ветви дерева принятий решений, и последующего просмотра сведений об отдельных вариантах.  
  
-   Детализация до **вариантов структуры**  
  
     Детализация до вариантов структуры используется в том случае, когда структура содержит сведения, которые могут не быть доступными в модели. Например, не используются контактные сведения покупателей в модели кластеризации, даже если эти данные включены в структуру. Однако после создания модели может потребоваться получить контактные сведения покупателей, сгруппированных в определенный кластер.  
  
 В данном разделе будут приведены примеры создания таких запросов.  
  
 [Использование детализации в конструкторе интеллектуального анализа данных](#bkmk_Designer)  
  
 [Создание запросов детализации с помощью расширений интеллектуального анализа данных](#bkmk_DMX)  
  
 [Вопросы, связанные с использованием детализации](#bkmk_Considerations)  
  
-   [Проблемы безопасности](#bkmk_Security)  
  
-   [Ограничения](#bkmk_Limits)  
  
##  <a name="bkmk_Designer"></a> Использование детализации в конструкторе интеллектуального анализа данных  
 Возможность детализации предусмотрена в модели интеллектуального анализа данных, и при наличии соответствующих разрешений во время просмотра модели можно щелкнуть узел в соответствующем средстве просмотра и получить подробные сведения о вариантах в данном узле.  
  
 [Детализация до данных вариантов из модели интеллектуального анализа данных](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
 Если при обработке структуры интеллектуального анализа данных обучающие варианты кэшировались и у пользователя есть необходимые разрешения, то можно получать сведения из вариантов модели и структуры интеллектуального анализа данных, включая столбцы, не включенные в модель интеллектуального анализа данных.  
  
##  <a name="bkmk_DMX"></a> Создание запросов детализации с помощью расширений интеллектуального анализа данных  
 Можно выполнять детализацию данных варианта путем создания запроса расширений интеллектуального анализа данных в том случае, если у вас имеются разрешения для модели или для структуры. Примеры синтаксиса для создания запросов детализации в расширении интеллектуального анализа данных содержатся в следующих разделах:  
  
 [Создание запросов детализации с помощью расширений интеллектуального анализа данных](../../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)  
  
##  <a name="bkmk_Considerations"></a> Вопросы, связанные с использованием детализации  
  
-   Если используется мастер интеллектуального анализа данных, то включить детализацию можно на его последней странице. По умолчанию детализация отключена. Дополнительные сведения см. в разделе [Завершение работы мастера (мастер интеллектуального анализа данных)](http://msdn.microsoft.com/library/6aef1548-35eb-42fd-ae87-63650a79eda1).  
  
-   Возможность детализации можно добавить в существующую модель интеллектуального анализа данных, но в этом случае модель необходимо обработать повторно, чтобы изменения вступили в силу.  
  
-   Детализация работает посредством получения информации об обучающих вариантах структуры интеллектуального анализа данных. Эта информация была кэширована при обработке структуры. Поэтому, если произвести удаление всех кэшированных данных изменением свойства <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> на **ClearAfterProcessing**, детализация работать не будет. Чтобы разрешить детализацию до столбцов структуры, нужно изменить значение свойства <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> на **KeepTrainingCases** , а затем выполнить повторную обработку структуры.  
  
-   Если детализация разрешена в модели интеллектуального анализа данных, но не разрешена в структуре, то сведения можно просматривать только из вариантов модели, но не из структуры интеллектуального анализа данных.  
  
###  <a name="bkmk_Security"></a> Вопросы безопасности, связанные с детализацией  
 Для детализации до вариантов структуры из модели необходимо, чтобы как в структуре, так и в модели интеллектуального анализа данных свойство [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) имело значение **True**. Более того, необходимо быть членом роли, обладающей разрешением на детализацию как в структуре, так и в модели. Дополнительные сведения о создании ролей см. в разделе [Конструктор ролей (службы Analysis Services — многомерные данные)](http://msdn.microsoft.com/library/e8ba42db-0565-4d68-b3ab-0c63d8d07192). см.  
  
 Разрешения на детализацию устанавливаются отдельно для структуры и для модели. Разрешение на детализацию модели позволяет проводить детализацию на основе модели, даже если у пользователя нет разрешения на детализацию структуры. Разрешения на детализацию структуры предоставляют дополнительную возможность включать столбцы структуры в запросы детализации с помощью функции [StructureColumn (DMX)](../../dmx/structurecolumn-dmx.md).  
  
> [!NOTE]  
>  Если включить детализацию как структуры, так и модели интеллектуального анализа данных, то любой пользователь, являющийся членом роли с разрешениями детализации в модели, также видит столбцы в структуре, даже если эти столбцы не входят в модель интеллектуального анализа данных. Поэтому, чтобы защитить конфиденциальные данные, необходимо настроить в представлении источника данных маскирование персональных данных и разрешать доступ к детализации структуры интеллектуального анализа данных только при необходимости.  
  
###  <a name="bkmk_Limits"></a> Ограничения по детализации  
  
-   Приведенные ниже ограничения относятся к операциям по детализации с моделью и зависят от алгоритма, с помощью которого была создана модель.  
  
|Имя алгоритма|Проблема|  
|--------------------|-----------|  
|Упрощенный алгоритм Байеса (Майкрософт)|Не поддерживается. В этих алгоритмах не назначаются варианты для отдельных узлов содержимого.|  
|Алгоритм нейронной сети (Майкрософт)|Не поддерживается. В этих алгоритмах не назначаются варианты для отдельных узлов содержимого.|  
|Алгоритм логистической регрессии (Майкрософт)|Не поддерживается. В этих алгоритмах не назначаются варианты для отдельных узлов содержимого.|  
|Алгоритм линейной регрессии (Майкрософт)|Поддерживается. Однако, поскольку модель содержит только один узел, **All**, при детализации возвращаются все обучающие варианты модели. Если задан большой обучающий набор, то загрузка результатов может занять много времени.|  
|Алгоритм временных рядов (Майкрософт)|Поддерживается. Однако нельзя выполнять детализацию структуры или данных вариантов с помощью **Средства просмотра моделей интеллектуального анализа данных** в конструкторе интеллектуального анализа данных. Вместо этого необходимо создать DMX-запрос.<br /><br /> Кроме того, нельзя выполнять детализацию по конкретным узлам или писать DMX-запросы для получения вариантов из конкретных узлов модели временных рядов. Данные вариантов можно извлечь либо из модели, либо из структуры по другим критериям, например по значениям атрибутов.<br /><br /> Можно также получить даты вариантов в модели с помощью функции [Журнал (DMX)](../../dmx/lag-dmx.md).<br /><br /> Просмотреть узлы ARTXP и ARIMA, созданные алгоритмом временных рядов (Майкрософт), может быть проще с помощью [средства просмотра деревьев содержимого общего вида (Майкрософт) (интеллектуальный анализ данных)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).|  
  
##  <a name="bkmk_Tasks"></a> Связанные задачи  
 Используйте следующие ссылки для работы с детализацией в конкретных сценариях.  
  
|Задача|Ссылка|  
|----------|----------|  
|Процедуры, описывающие использование детализации в конструкторе интеллектуального анализа данных|[Детализация до данных вариантов из модели интеллектуального анализа данных](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)|  
|Изменение существующей модели интеллектуального анализа данных для разрешения детализации|[включить детализацию для модели интеллектуального анализа данных](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)|  
|Включение детализации для структуры интеллектуального анализа данных с помощью предложения DMX WITH DRILLTHROUGH|[СОЗДАНИЕ СТРУКТУРЫ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ (DMX)](../../dmx/create-mining-structure-dmx.md)|  
|Сведения о присвоении разрешений, относящихся к детализации структур и моделей интеллектуального анализа данных|[Предоставление разрешений структурам интеллектуального анализа данных и моделям интеллектуального анализа данных (службы Analysis Services)](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a>См. также раздел  
 [Средства просмотра моделей интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [Запросы интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-queries.md)  
  
  