---
title: Добавление моделей интеллектуального анализа данных в структуру (службы Analysis Services — Интеллектуальный анализ данных) | Документы Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c32140e639a0e79b8736036392104f593a305b30
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="add-mining-models-to-a-structure-analysis-services---data-mining"></a>Добавление моделей интеллектуального анализа данных в структуру (службы Analysis Services — интеллектуальный анализ данных)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Структура интеллектуального анализа данных должна поддерживать несколько моделей интеллектуального анализа данных. Поэтому после выхода из мастера можно открыть структуру и добавить в нее новые модели интеллектуального анализа данных. Каждый раз при создании модели можно использовать другой алгоритм, изменять параметры или применять фильтры для использования другого подмножества данных.  
  
## <a name="adding-new-mining-models"></a>Добавление моделей интеллектуального анализа данных  
 Если для создания новой модели интеллектуального анализа данных используется мастер интеллектуального анализа данных, по умолчанию сначала необходимо создать структуру интеллектуального анализа данных. Мастер интеллектуального анализа данных позволяет добавить в структуру начальную модель интеллектуального анализа данных. Однако не обязательно создавать модель сразу. Если создать только структуру, не нужно решать, какой столбец использовать в качестве прогнозируемого атрибута или как использовать данные в конкретной модели. Вместо этого можно просто настроить общую структуру данных, которую предполагается использовать в дальнейшем, а затем с помощью средства [Data Mining Designer](../../analysis-services/data-mining/data-mining-designer.md) добавлять новые модели интеллектуального анализа данных, основанные на этой структуре.  
  
> [!NOTE]  
>  В языке расширений интеллектуального анализа данных инструкция CREATE MINING MODEL начинается с модели интеллектуального анализа данных. Это значит, что после выбора модели интеллектуального анализа данных службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически создают базовую структуру. Затем к этой структуре можно добавлять новые модели интеллектуального анализа данных с помощью инструкции ALTER STRUCTURE… ADD MODEL.  
  
## <a name="choosing-an-algorithm"></a>Выбор алгоритма  
 Если новая модель интеллектуального анализа данных добавляется в существующую структуру, вначале необходимо выбрать алгоритм интеллектуального анализа данных для этой модели. Выбор алгоритма очень важен, потому что у каждого алгоритма свой способ анализа данных и свои требования.  
  
 Если выбран алгоритм, несовместимый с данными, выдается предупреждение. В некоторых случаях придется пропустить столбцы, которые алгоритм не может обработать. В некоторых случаях алгоритм выполнит эту корректировку автоматически. Например, если структура содержит числовые данные, а алгоритм может работать только с дискретными значениями, он сгруппирует числовые значения в дискретные интервалы. В некоторых случаях необходимо вначале скорректировать данные вручную путем выбора ключа или прогнозируемого атрибута.  
  
 При создании новой модели менять алгоритм необязательно. Часто можно получить очень разные результаты с одним и тем же алгоритмом, фильтруя данные или меняя такие параметры, как метод кластеризации или минимальный размер набора элементов. Рекомендуется поэкспериментировать с несколькими моделями, чтобы понять, какие параметры дают наилучшие результаты.  
  
 Помните, что новые модели должны быть обработаны, прежде чем ими можно будет пользоваться.  
  
## <a name="specifying-the-usage-of-columns-in-a-new-mining-model"></a>Определение использования столбцов в новой модели интеллектуального анализа данных  
 Если новая модель интеллектуального анализа данных добавляется к существующей структуре интеллектуального анализа данных, необходимо вначале указать, как должен использоваться в модели каждый столбец. В зависимости от типа выбранного алгоритма, некоторые варианты могут использоваться по умолчанию. Если для столбца не указан тип использования, то этот столбец не будет включен в структуру интеллектуального анализа данных. Однако данные столбца должны быть по-прежнему доступны для детализации, если модель ее поддерживает.  
  
 Столбец структуры интеллектуального анализа данных, используемый моделью (не настроенный их пропущенный), должен быть ключевым столбцом, входным столбцом или прогнозируемым столбцом, значения которого используются в качестве входов модели.  
  
-   Ключевые столбцы содержат уникальный идентификатор для каждой строки в таблице. Некоторые модели интеллектуального анализа данных, например модели, основанные на алгоритмах кластеризации последовательностей и временных рядов, могут содержать несколько ключевых столбцов. Однако эти несколько ключей не являются составными в реляционном смысле, а должны быть выбраны для обеспечения поддержки анализа временных рядов и кластера последовательностей.  
  
-   Входные столбцы предоставляют данные, на основе которых осуществляется прогнозирование. Мастер интеллектуального анализа данных предоставляет функцию **Предложить** , которая включается при выборе прогнозируемого столбца. Если нажать эту кнопку, мастер считывает прогнозируемые значения и определяет, какие другие столбцы в структуре будут хорошими переменными. Мастер отвергнет ключевые или другие столбцы с большим количеством уникальных значений и предложит столбцы, которые, как кажется, хорошо коррелируют с выходными данными.  
  
     Эта функция особенно удобна, если база данных содержит больше столбцов, чем нужно для модели интеллектуального анализа данных. Функция **Предложить** вычисляет численный показатель, от 0 до 1, описывающий связь между каждым столбцом в наборе данных и прогнозируемым столбцом. На основе этого показателя функция предполагает столбцы для использования в качестве входных для модели интеллектуального анализа данных. При использовании функции **Предложить** можно использовать предполагаемые столбцы, изменить выбор в соответствии с потребностями или пропустить предположения.  
  
-   Прогнозируемые столбцы содержат данные, которые прогнозирует модель интеллектуального анализа данных. Можно выбрать несколько столбцов в качестве прогнозируемых атрибутов. Модели кластеризации являются исключением — прогнозируемый атрибут для них необязателен.  
  
     В зависимости от типа модели может потребоваться, чтобы прогнозируемый столбец принадлежал к определенному типу данных. Например, для модели линейной регрессии прогнозируемый столбец должен быть числовым, а упрощенному алгоритму Байеса требуется дискретное значение (дискретными должны быть и все входные значения).  
  
## <a name="specifying-column-content"></a>Указание содержимого столбцов  
 Для некоторых столбцов нужно также задавать *содержимое столбца*. При интеллектуальном анализе данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] алгоритм обрабатывает данные из столбца в соответствии со свойством «Тип содержимого» этого столбца. Например, если в данных есть столбец «Доход», нужно указать, что этот столбец содержит непрерывный числовой показатель, задав для него тип содержимого «Непрерывный». Можно также указать, что числа в столбце «Доход» следует сгруппировать в контейнеры, задав тип содержимого «Дискретизированный». По желанию можно задать точное число контейнеров. Можно создавать различные модели, которые будут по-разному обрабатывать столбцы. Например, одна модель может разбивать множество всех заказчиков на три возрастных группы, а другая — на десять.  
  
## <a name="see-also"></a>См. также  
 [Структуры интеллектуального анализа данных и &#40; Службы Analysis Services — Интеллектуальный анализ данных &#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Создание реляционной структуры](../../analysis-services/data-mining/create-a-relational-mining-structure.md)   
 [Свойства модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-properties.md)   
 [Столбцы модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-columns.md)  
  
  
