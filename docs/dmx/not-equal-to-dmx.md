---
title: '&lt;&gt; (Не равно) (DMX) | Документы Microsoft'
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
dev_langs:
- DMX
helpviewer_keywords:
- not equal operator (<>)
- <> (not equal to operator)
ms.assetid: df0e7901-9e31-452a-af14-471f5130c09d
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b36e2dfec16ad7941032c0220b605a276aeb82ab
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ltgt-not-equal-to-dmx"></a>&lt;&gt; (Не равно) (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Выполняет операцию сравнения, определяющую, является ли значение одного выражения неравным значению другого выражения расширений интеллектуального анализа данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DMX_Expression <> DMX_Expression  
```  
  
#### <a name="parameters"></a>Параметры  
 *DMX_Expression*  
 Допустимое выражение расширений интеллектуального анализа данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение равно TRUE, если оба аргумента не равны NULL, и значение первого аргумента не равно значению второго. Логическое значение равно FALSE, если оба аргумента не равны NULL и значение первого аргумента равно значению второго. Логическое значение равно NULL, если один или оба аргумента имеют значение NULL.  
  
## <a name="see-also"></a>См. также  
 [Операторы сравнения &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-comparison.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; Справочник по операторам](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;расширений интеллектуального анализа данных&#41;](../dmx/operators-dmx.md)  
  
  
