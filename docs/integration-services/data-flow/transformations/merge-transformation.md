---
title: "Преобразование «Слияние» | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.mergetrans.f1
- sql13.dts.designer.mergetransformation.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- merging data [Integration Services]
- Merge transformation
- combining datasets
- datasets [Integration Services], merging
ms.assetid: cff8690c-07ac-46a0-aab5-20bd4848c677
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4b557efa62075f7b88e6b70cf5950546444b95d8
ms.openlocfilehash: 4c3eead08bb91d43f83782682a122da278ac051f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/19/2017

---
# <a name="merge-transformation"></a>преобразование «Слияние»
  Преобразование «Слияние» объединяет два упорядоченных набора данных в один. Строки из каждого набора данных вставляются в выходной набор на основе значений их ключевых столбцов.  
  
 Включая преобразование «Слияние» в поток данных, можно выполнить следующие задачи:  
  
-   Произвести слияние данных из двух источников данных, таких как таблицы и файлы.  
  
-   Создать сложные наборы данных при помощи вложенных преобразований «Слияние».  
  
-   Произвести повторное слияние строк после исправления ошибок в данных.  
  
 Преобразование «Слияние» похоже на преобразование «Объединить все». Используйте преобразование «Объединить все» вместо преобразования «Слияние» в следующих случаях:  
  
-   Входы преобразования не упорядочены.  
  
-   Объединенный выход не требует упорядочения.  
  
-   Преобразование имеет более двух входов.  
  
## <a name="input-requirements"></a>Требования к входным данным  
 Преобразованию «Слияние» необходимы отсортированные входные данные. Дополнительные сведения об этом важном требовании см. в статье [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Кроме того, преобразование «Слияние» требует, чтобы у объединенных столбцов входных данных совпадали метаданные. Например, нельзя произвести слияние столбца числового типа данных со столбцом символьного типа. Если данные представляют собой тип строковых данных, длина столбца при вторичном входе должна быть меньше или равна длине столбца при первичном входе, с которым происходит слияние.  
  
 Пользовательский интерфейс для преобразования «Слияние» в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] автоматически сопоставляет столбцы с одинаковыми метаданными. Затем можно вручную сопоставить столбцы с совместимыми типами данных.  
  
 Это преобразование имеет два входа и один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-merge-transformation"></a>Настройка преобразования «Слияние»  
 Свойства могут устанавливаться через конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или с помощью программных средств.  
  
 Дополнительные сведения о параметрах, задаваемых программно, см. в следующих разделах:  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о способах задания свойств см. в следующих разделах:  
  
-   [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
-   [Сортировка данных для слияния и преобразования соединения слиянием](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="merge-transformation-editor"></a>редактор преобразования «Слияние»
  **Редактор преобразования «Слияние»** используется для указания столбцов из двух отсортированных наборов данных для слияния.  
  
> [!IMPORTANT]  
>  Преобразованию «Слияние» необходимы отсортированные входные данные. Дополнительные сведения об этом важном требовании см. в разделе [Сортировка данных для преобразований "Слияние" и "Соединение слиянием"](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
### <a name="options"></a>Параметры  
 **Имя выходного столбца**  
 Позволяет указать имя выходного столбца.  
  
 **Вход слияния 1**  
 Позволяет выбрать столбец в качестве входа слияния 1.  
  
 **Вход слияния 2**  
 Позволяет выбрать столбец в качестве входа слияния 2.  
  
## <a name="see-also"></a>См. также:  
 [Преобразование «Соединение слиянием»](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [UNION All Transformation](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  