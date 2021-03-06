---
title: Идентификаторы (многомерные Выражения) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- formats [Analysis Services]
- Multidimensional Expressions [Analysis Services], identifiers
- identifiers [MDX]
- MDX [Analysis Services], identifiers
- delimited identifiers [MDX]
- regular identifiers [MDX]
- formats [Analysis Services], identifiers
ms.assetid: 739a8a67-bef3-4b56-961d-ee96cfc36b5b
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a04d387c0ee40d825fddf3c50f02793e722cdbc8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="identifiers-mdx"></a>Идентификаторы (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Идентификатор — это имя [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] объекта. Каждый объект служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] должен иметь идентификатор. Это относится к кубам, измерениям, иерархиям, уровням, элементам и т.п. Идентификатор можно использовать для обращения к объекту в инструкциях многомерных выражений.  
  
 В зависимости от имени объекта его идентификатор будет либо обычным, либо с разделителем.  
  
> [!NOTE]  
>  Идентификаторы обычных и с разделителями должны содержать от 1 до 100 символов.  
  
## <a name="using-regular-identifiers"></a>Обычные идентификаторы  
 Обычный идентификатор — это имя объекта, заданное в соответствии с нижеприведенными правилами форматирования обычных идентификаторов. Обычный идентификатор можно использовать с разделителями и без разделителей.  
  
### <a name="formatting-rules-for-regular-identifiers"></a>Правила форматирования обычных идентификаторов  
  
1.  Первым символом должен быть один из следующих.  
  
    -   Буква в соответствии с определением стандарта Юникод 2.0. Помимо букв других языков в состав Юникода входят латинские символы от «a до z» и от «A до Z».  
  
    -   Символ подчеркивания (_).  
  
2.  Далее могут идти следующие символы:  
  
    -   Буквы, определенные стандартом Юникод 2.0.  
  
    -   Десятичные цифры из набора символов Basic Latin или другого набора символов национального языка.  
  
    -   Символ подчеркивания (_).  
  
3.  В качестве идентификатора не может выступать зарезервированное ключевое слово многомерных выражений. Зарезервированные слова в многомерных выражениях не зависят от регистра. Дополнительные сведения см. в разделе [зарезервированные ключевые слова &#40;синтаксис многомерных Выражений&#41;](../mdx/reserved-keywords-mdx-syntax.md).  
  
4.  Внутри идентификаторов запрещается использовать символы пробела или специальные символы.  
  
### <a name="examples-of-regular-identifiers"></a>Примеры обычных идентификаторов  
 В следующей инструкции многомерных выражений идентификаторы `Measures`, `Product` и `Style` соответствуют правилам форматирования обычных идентификаторов. Для них не требуются разделители.  
  
 `SELECT Measures.MEMBERS ON COLUMNS,`  
  
 `Product.Style.CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
 При необходимости в обычных идентификаторах можно использовать разделители. В следующей инструкции многомерных выражений обычные идентификаторы `Measures`, `Product` и `Style` корректно разделены с помощью квадратных скобок.  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Product].[Style].CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
## <a name="using-delimited-identifiers"></a>Использование идентификаторов с разделителями  
 Идентификаторы, не соответствующие правилам форматирования обычных идентификаторов, всегда должны выделяться квадратными скобками ([]).  
  
> [!NOTE]  
>  Разделители используются только для идентификаторов. Их нельзя использовать для ключевых слов независимо от того, зарезервированы или нет эти слова в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Идентификаторы с разделителями используются в следующих случаях.  
  
-   Если в имени или в части имени объекта используется зарезервированное слово.  
  
     Рекомендуется не использовать зарезервированные ключевые слова в качестве имен объектов. Баз данных, обновленных из предыдущих версий [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] могут содержать идентификаторы, которые включают слова, не зарезервированные в ранней версии, но являются зарезервированными словами для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. До изменения идентификатора можно обращаться к объекту по идентификатору с разделителем.  
  
-   Если в имени объекта присутствуют символы, недопустимые для использования в идентификаторах.  
  
     Службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] позволяют использовать в идентификаторе с разделителем любой символ из текущей кодовой страницы. Однако не рекомендуется использовать специальные символы в имени объекта без разбора, поскольку это может сделать инструкции и скрипты многомерных выражений трудными для понимания и обслуживания.  
  
### <a name="formatting-rules-for-delimited-identifiers"></a>Правила форматирования идентификаторов с разделителями  
 Тело идентификатора с разделителем может содержать любую комбинацию символов из текущей кодовой страницы, в том числе сами символы разделителя. Если тело идентификатора с разделителями содержит символы разделителя, необходимо особое выделение.  
  
-   Если тело идентификатора содержит только открывающую квадратную скобку ([), особого выделения не требуется.  
  
-   Если тело идентификатора содержит закрывающую квадратную скобку (]), необходимо указать две таких скобки (]]).  
  
### <a name="examples-of-delimited-identifiers"></a>Примеры идентификаторов с разделителями  
 В следующем примере инструкции многомерных выражений идентификаторы `Sales Volume`, `Sales Cube` и `select` являются идентификаторами с разделителями.  
  
 `-- The [Sales Volume] and [Sales Cube] identifiers contain a space.`  
  
 `SELECT Measures.[Sales Volume]`  
  
 `FROM [Sales Cube]`  
  
 `WHERE Product.[select]`  
  
 `-- The [select] identifier is a reserved keyword.`  
  
 В следующем примере объект имеет имя `Total Profit [Domestic]`. Для обращения к нему необходимо использовать следующий идентификатор с разделителем.  
  
 `[Total Profit [Domestic]]]`  
  
 Обратите внимание, что открывающую квадратную скобку перед идентификатором `Domestic` не нужно изменять, чтобы создать идентификатор с разделителем. Однако закрывающую квадратную скобку после `Domestic` следует заменить двумя закрывающими квадратными скобками.  
  
### <a name="delimiting-identifiers-with-multiple-parts"></a>Выделенные идентификаторы с несколькими частями  
 При использовании полных имен объектов может потребоваться разделять несколько идентификаторов, составляющих имя объекта. Например, идентификатор Front Brakes в следующем коде обязательно указывается с разделителями.  
  
 SELECT [Measures].MEMBERS ON COLUMNS,  
  
 [Product].[Product].[Front Brakes] ON ROWS  
  
 FROM [Adventure Works]  
  
 Помимо этого, в предыдущем примере выделен идентификатор Measures, чтобы продемонстрировать разделение нескольких идентификаторов.  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку многомерных Выражений & #40; Многомерные Выражения & #41;](../mdx/mdx-language-reference-mdx.md)   
 [Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Синтаксис элементов &#40;многомерных Выражений&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
