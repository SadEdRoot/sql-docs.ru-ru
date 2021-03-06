---
title: IsInNode (расширения интеллектуального анализа данных) | Документы Microsoft
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
- IsInNode
dev_langs:
- DMX
helpviewer_keywords:
- IsInNode function
ms.assetid: 47b2114f-9ad6-45cc-9498-193ad6fa5288
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: e32d63a25264f0aeee1480c07d8a7973518f074a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="isinnode-dmx"></a>IsInNode (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Указывает, содержит ли заданный узел текущий вариант.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsInNode(<NodeID>)  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Тип Boolean.  
  
## <a name="remarks"></a>Замечания  
 **IsInNode** используется только в [SELECT FROM &#60;модели&#62;. СЛУЧАИ &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-cases-dmx.md) и [SELECT FROM &#60;модель&#62;. SAMPLE_CASES &#40;расширений интеллектуального анализа данных&#41; ](../dmx/select-from-model-sample-cases-dmx.md) запросов.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает все варианты, использованные при создании модели и связанные с узлом, заданным функцией IsInNode.  
  
```  
Select * from [TM Decision Tree].Cases  
WHERE IsInNode('0')  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; функции ссылки](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Функции &#40;расширений интеллектуального анализа данных&#41;](../dmx/functions-dmx.md)   
 [Общие функции прогнозирования &#40;расширений интеллектуального анализа данных&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
