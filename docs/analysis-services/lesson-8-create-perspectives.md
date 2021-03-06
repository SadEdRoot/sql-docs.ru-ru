---
title: Занятие 9 Создание перспектив | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e917e817768571e1959ae6163743ecdad0409af
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-8-create-perspectives"></a>Занятие 8. Создание перспектив
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии будет создана перспектива «Продажи через Интернет». Перспектива определяет просматриваемое подмножество модели, реализующее точки наблюдения, которые сосредоточены на определенном аспекте бизнеса либо предназначены для использования в конкретном приложении. Когда пользователь подключается к модели с помощью перспективы, они видят только те объекты модели (таблицы, столбцы, меры, иерархии и ключевые показатели эффективности) как поля, определенные в перспективе.  
  
Перспективы Internet Sales, создаваемая на этом занятии, исключает объект таблицы DimCustomer. При создании перспективы, которая исключает из представления определенные объекты, такие объекты продолжают существовать в модели, однако они не видны в списке полей клиентского средства создания отчетов. Вычисляемые столбцы и меры, как входящие в перспективу, так и нет, все равно смогут проводить вычисления с использованием данных из исключенного объекта.  
  
Цель этого занятия — описать создание перспектив и ознакомиться со средствами разработки табличных моделей. Если потом развернуть эту модель и включить дополнительные таблицы, можно создать дополнительные перспективы для определения разных точек обзора модели, например, инвентаризации и продажи. Дополнительные сведения см. в разделе [Перспективы](../analysis-services/tabular-models/perspectives-ssas-tabular.md).  
  
Предполагаемое время выполнения этого занятия: **5 минут**.  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 7: Создание ключевых показателей эффективности](../analysis-services/lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Создание перспектив  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Создание перспективы «Продажи через Интернет»  
  
1.  Нажмите кнопку **модель** меню > **перспективы** > **Создание и управление**.  
  
2.  В диалоговом окне **Перспективы** щелкните **Создать перспективу**.  
  
3.  Дважды щелкните **новую перспективу** заголовок столбца и переименовать **продажи через Интернет**.  
  
4.  Выберите все таблицы *за исключением* **DimCustomer**.  
  
    ![как табличных lesson8-перспектив](../analysis-services/media/as-tabular-lesson8-perspectives.png)
  
    В одном из следующих занятий будет использовать функции анализа в Excel для проверки этой перспективы. Список полей сводной таблицы Excel будет содержать все таблицы, за исключением того, в таблице DimCustomer.  

## <a name="whats-next"></a>Дальнейшие действия
Перейдите к следующему занятию: [занятии 9: создание иерархий](../analysis-services/lesson-9-create-hierarchies.md).
  
  
  
  
