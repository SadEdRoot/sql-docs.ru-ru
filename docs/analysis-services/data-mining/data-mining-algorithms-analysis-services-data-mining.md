---
title: "Алгоритмы интеллектуального анализа данных (службы Analysis Services — Интеллектуальный анализ данных) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- clustering [Data Mining]
- learning algorithms
- data mining [Analysis Services], models
- algorithms [data mining]
- mining models [Analysis Services], algorithms
- inductive learning
- mining models [Analysis Services], creating
- data mining [Analysis Services], algorithms
- machine learning algorithms [Analysis Services]
ms.assetid: ed1fc83b-b98c-437e-bf53-4ff001b92d64
caps.latest.revision: 74
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 85f1333bc1f9674dcdb5274e0b2768c401fd2d7c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-mining-algorithms-analysis-services---data-mining"></a>Алгоритмы интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)
  В интеллектуальном анализе данных (или машинном обучении) *алгоритм* — это набор эвристики и вычислений, который создает на основе данных модель. Чтобы создать модель, алгоритм сначала анализирует предоставленные данные, осуществляя поиск определенных закономерностей и тенденций. Алгоритм применяет результаты этого анализа ко множеству итераций, чтобы подобрать оптимальные параметры для создания модели интеллектуального анализа данных. Затем эти параметры применяются ко всему набору данных, чтобы выявить пригодные к использованию закономерности и получить подробную статистику.  
  
 Модель интеллектуального анализа данных, создаваемая алгоритмом из предоставленных данных, может иметь различные формы, включая следующие.  
  
-   Набор кластеров, описывающих связи вариантов в наборе данных.  
  
-   Дерево решений, которое предсказывает результат и описывает, какое влияние на этот результат оказывают различные критерии.  
  
-   Математическую модель, прогнозирующую продажи.  
  
-   Набор правил, описывающих группирование продуктов в транзакции, а также вероятности одновременной покупки продуктов.  
  
 В интеллектуальном анализе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используются наиболее популярные и изученные методы выявления закономерностей в данных. Например, алгоритм кластеризации методом К-средних является одним из старейших алгоритмов кластеризации и широко применяется во многих инструментах и со многими реализациями и параметрами. При этом алгоритм кластеризации методом К-средних, реализованный в интеллектуальном анализе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , был разработан группой Microsoft Research, а затем оптимизирован для работы со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Все алгоритмы интеллектуального анализа данных Майкрософт доступны для гибкой настройки и программирования с использованием предоставляемых API. С помощью компонентов интеллектуального анализа данных в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]можно также автоматизировать создание, обучение и переобучение моделей.  
  
 Кроме того, поддерживается использование сторонних алгоритмов, соответствующих спецификации OLE DB для интеллектуального анализа данных. Имеется также возможность разрабатывать собственные алгоритмы, которые можно зарегистрировать в качестве служб, а затем использовать в платформе интеллектуального анализа данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="choosing-the-right-algorithm"></a>Выбор правильного алгоритма  
 Выбор правильного алгоритма для использования в конкретной аналитической задаче может быть достаточно сложным. В то время как можно использовать различные алгоритмы для выполнения одной и той же задачи, каждый алгоритм выдает различный результат, а некоторые алгоритмы могут выдавать более одного типа результатов. Например, можно использовать алгоритм дерева принятия решений [!INCLUDE[msCoName](../../includes/msconame-md.md)] не только для прогнозирования, но также в качестве способа уменьшения количества столбцов в наборе данных, поскольку дерево принятия решений может идентифицировать столбцы, не влияющие на конечную модель интеллектуального анализа данных.  
  
### <a name="choosing-an-algorithm-by-type"></a>Выбор алгоритма по типу  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Интеллектуальный анализ данных включает указанные ниже типы алгоритмов.  
  
-   **Алгоритмы классификации** осуществляют прогнозирование одной или нескольких дискретных переменных на основе других атрибутов в наборе данных.  
  
-   **Регрессивные алгоритмы** осуществляют прогнозирование одной или нескольких непрерывных числовых переменных, например прибыли или убытков, на основе других атрибутов в наборе данных.  
  
-   **Алгоритмы сегментации** делят данные на группы или кластеры элементов, имеющих схожие свойства.  
  
-   **Алгоритмы взаимосвязей** осуществляют поиск корреляции между различными атрибутами в наборе данных. Наиболее частым применением этого типа алгоритма является создание правил взаимосвязи, которые могут использоваться для анализа потребительской корзины.  
  
-   **Алгоритмы анализа последовательностей** обобщают часто встречающиеся в данных последовательности, такие как серия переходов по веб-сайту или событий, зарегистрированных в журнале перед ремонтом оборудования.  
  
 Однако ничто не заставляет пользователя ограничиваться одним алгоритмом в своих решениях. Опытные аналитики часто используют один алгоритм для выявления наиболее эффективных входных данных (то есть переменных), после чего применяют другой алгоритм для прогнозирования определенного результата на основе этих данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Интеллектуальный анализ данных позволяет на базе одной структуры интеллектуального анализа построить много моделей таким образом, что в рамках одного решения для интеллектуального анализа данных можно было использовать алгоритм кластеризации, модель дерева решений, а также модель упрощенного алгоритма Байеса для получения разных представлений данных. В одном решении также можно использовать несколько алгоритмов для выполнения отдельных задач. Например, с помощью регрессии можно получать финансовые прогнозы, а с помощью алгоритма нейронной сети выполнять анализ факторов, влияющих на прогнозы.  
  
### <a name="choosing-an-algorithm-by-task"></a>Выбор алгоритма по задаче  
 Чтобы облегчить выбор алгоритмов для решения определенной задачи, в следующей таблице приведены типы задач, для решения которых обычно используется каждый алгоритм.  
  
|Примеры задач|Подходящие алгоритмы Майкрософт|  
|-----------------------|---------------------------------|  
|**Прогнозирование дискретного атрибута:**<br /><br /> Пометка клиентов из списка потенциальных покупателей как хороших и плохих кандидатов.<br /><br /> Вычисление вероятности отказа сервера в течение следующих шести месяцев.<br /><br /> Классификация вариантов развития болезней пациентов и исследование связанных факторов.|[Алгоритм дерева принятия решений (Майкрософт)](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)<br /><br /> [Упрощенный алгоритм Байеса (Майкрософт)](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)<br /><br /> [Алгоритм кластеризации (Майкрософт)](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)<br /><br /> [Алгоритм нейронной сети (Майкрософт)](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)|  
|**Прогнозирование непрерывного атрибута:**<br /><br /> Прогноз продаж на следующий год.<br /><br /> Прогноз количества посетителей сайта с учетом прошлых лет и сезонных тенденций.<br /><br /> Формирование оценки риска с учетом демографии.|[Алгоритм дерева принятия решений (Майкрософт)](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)<br /><br /> [Алгоритм временных рядов (Майкрософт)](../../analysis-services/data-mining/microsoft-time-series-algorithm.md)<br /><br /> [Алгоритм линейной регрессии (Майкрософт)](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)|  
|**Прогнозирование последовательности:**<br /><br /> Анализ маршрута перемещения по веб-сайту компании.<br /><br /> Анализ факторов, ведущих к отказу сервера.<br /><br /> Отслеживание и анализ последовательностей действий во время посещения поликлиники с целью формулирования рекомендаций по общим действиям.|[Алгоритм кластеризации последовательностей (Майкрософт)](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)|  
|**Нахождение групп общих элементов в транзакциях:**<br /><br /> Использование анализа потребительской корзины для определения мест размещения продуктов.<br /><br /> Выявление дополнительных продуктов, которые можно предложить купить клиенту.<br /><br /> Анализ данных опроса, проведенного среди посетителей события, с целью выявления того, какие действия и стенды были связаны, чтобы планировать будущие действия.|[Алгоритм взаимосвязей (Майкрософт)](../../analysis-services/data-mining/microsoft-association-algorithm.md)<br /><br /> [Алгоритм дерева принятия решений (Майкрософт)](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)|  
|**Нахождение групп схожих элементов:**<br /><br /> Создание профилей рисков для пациентов на основе таких атрибутов, как демография и поведение.<br /><br /> Анализ пользователей по шаблонам просмотра и покупки.<br /><br /> Определение серверов, которые имеют аналогичные характеристики использования.|[Алгоритм кластеризации (Майкрософт)](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)<br /><br /> [Алгоритм кластеризации последовательностей (Майкрософт)](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)|  
  
## <a name="related-content"></a>См. также  
 В приведенной ниже таблице содержатся ссылки на ресурсы по обучению применению каждого из алгоритмов интеллектуального анализа данных, используемых в интеллектуальном анализе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|||  
|-|-|  
|**Общее описание алгоритма**|Объясняет работу алгоритма и содержит примеры возможных бизнес-сценариев, в которых этот алгоритм может быть полезен.|  
||[Алгоритм взаимосвязей (Майкрософт)](../../analysis-services/data-mining/microsoft-association-algorithm.md)<br /><br /> [Алгоритм кластеризации (Майкрософт)](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)<br /><br /> [Алгоритм дерева принятия решений (Майкрософт)](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)<br /><br /> [Алгоритм линейной регрессии (Майкрософт)](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)<br /><br /> [Алгоритм логистической регрессии (Майкрософт)](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)<br /><br /> [Упрощенный алгоритм Байеса (Майкрософт)](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)<br /><br /> [Алгоритм нейронной сети (Майкрософт)](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)<br /><br /> [Алгоритм кластеризации последовательностей (Майкрософт)](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)<br /><br /> [Алгоритм временных рядов (Майкрософт)](../../analysis-services/data-mining/microsoft-time-series-algorithm.md)|  
|**Технический справочник**|Содержит технические данные о реализации алгоритма со ссылками на соответствующую литературу при необходимости. Содержит список параметров, с помощью которых можно управлять работой алгоритма и изменять результаты в модели. Описывает требования к данным и содержит советы по повышению производительности, когда это возможно.|  
||[Технический справочник по алгоритму взаимосвязей (Майкрософт)](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму кластеризации (Майкрософт)](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму дерева принятия решений (Майкрософт)](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму линейной регрессии (Майкрософт)](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму логистической регрессии (Майкрософт)](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Технический справочник по упрощенному алгоритму Байеса (Майкрософт)](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму нейронной сети (Майкрософт)](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму кластеризации последовательностей (Майкрософт)](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [Технический справочник по алгоритму временных рядов (Майкрософт)](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|**Содержимое модели**|Описывает, каким образом данные структурируются для каждого типа модели и объясняет, как интерпретировать данные, хранящиеся в каждом из узлов.|  
||[Содержимое моделей интеллектуального анализа данных для моделей взаимосвязей (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей кластеризации (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей дерева принятия решений (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей линейной регрессии (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей логистической регрессии (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-logistic-regression-models.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей упрощенного алгоритма Байеса (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей нейронных сетей (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей кластеризации последовательностей (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)<br /><br /> [Содержимое моделей интеллектуального анализа данных для моделей временных рядов (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)|  
|**Запросы интеллектуального анализа данных**|Содержит примеры запросов, которые могут быть использованы с моделями каждого типа. Содержит описание запросов содержимого, позволяющих получить подробные сведения о закономерностях в модели, а также прогнозирующих запросов, позволяющих строить прогнозы на основе этих закономерностей.|  
||[Примеры запросов моделей взаимосвязей](../../analysis-services/data-mining/association-model-query-examples.md)<br /><br /> [Примеры запросов к модели кластеризации](../../analysis-services/data-mining/clustering-model-query-examples.md)<br /><br /> [Примеры запросов к модели дерева принятия решений](../../analysis-services/data-mining/decision-trees-model-query-examples.md)<br /><br /> [Примеры запросов модели линейной регрессии](../../analysis-services/data-mining/linear-regression-model-query-examples.md)<br /><br /> [Примеры запросов модели логистической регрессии](../../analysis-services/data-mining/logistic-regression-model-query-examples.md)<br /><br /> [Примеры запросов к модели упрощенного алгоритма Байеса](../../analysis-services/data-mining/naive-bayes-model-query-examples.md)<br /><br /> [Примеры запросов к модели нейронной сети](../../analysis-services/data-mining/neural-network-model-query-examples.md)<br /><br /> [Примеры запросов к модели кластеризации последовательностей](../../analysis-services/data-mining/sequence-clustering-model-query-examples.md)<br /><br /> [Примеры запросов моделей временных рядов](../../analysis-services/data-mining/time-series-model-query-examples.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|**Раздел**|**Description**|  
|---------------|---------------------|  
|Определение алгоритма, используемого моделью интеллектуального анализа данных|[запросить параметры, используемые для создания модели интеллектуального анализа данных](../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md)|  
|Создание пользовательского подключаемого алгоритма|[Подключаемые алгоритмы](../../analysis-services/data-mining/plugin-algorithms.md)|  
|Исследование модели с помощью средства просмотра конкретного алгоритма|[Средства просмотра моделей интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-model-viewers.md)|  
|Просмотр содержимого модели с помощью общего формата таблицы|[Просмотр модели в средстве просмотра деревьев содержимого общего вида (Майкрософт)](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)|  
|Сведения о настройке данных и использовании алгоритмов для создания моделей|[Структуры интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)<br /><br /> [Модели интеллектуального анализа данных (службы Analysis Services — интеллектуальный анализ данных)](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a>См. также  
 [Средства интеллектуального анализа данных](../../analysis-services/data-mining/data-mining-tools.md)  
  
  
