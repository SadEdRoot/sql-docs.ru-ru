---
title: "IsAncestor (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISANCESTOR
dev_langs:
- kbMDX
helpviewer_keywords:
- IsAncestor function
ms.assetid: 49d2fcdf-8d9a-4c79-bd00-4910ea149141
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: eb2d6dcfb4e5d0992a522c060947d942a5b48a53
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="isancestor-mdx"></a>IsAncestor (многомерные выражения)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает значение, сообщающее, является ли заданный элемент предком другого заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IsAncestor(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Аргументы  
 *Member_Expression1*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
 *Member_Expression2*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Замечания  
 **IsAncestor** возврата функцией **true** Если первый заданный элемент является предком второго заданного элемента. В противном случае функция возвращает **false**.  
  
## <a name="example"></a>Пример  
 В следующем примере возвращается **true** Если [Date]. [ Fiscal]. CurrentMember является предком January 2003:  
  
 `WITH MEMBER MEASURES.ISANCESTORDEMO AS`  
  
 `IsAncestor([Date].[Fiscal].CurrentMember, [Date].[Fiscal].[Month].&[2003]&[1])`  
  
 `SELECT MEASURES.ISANCESTORDEMO ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>См. также:  
 [Предок &#40; Многомерные Выражения &#41;](../mdx/ancestor-mdx.md)   
 [Справочник по функциям многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
