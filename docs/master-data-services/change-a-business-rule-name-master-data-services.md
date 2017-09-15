---
title: "Изменение имени бизнес-правила (службы Master Data Services) | Документы Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules [Master Data Services], changing name
ms.assetid: cffcae43-a208-443f-9f43-a0ec9e05f79c
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 0c1bc165b9c1d1fcf198c204e31de6d775932bbe
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="change-a-business-rule-name-master-data-services"></a>Изменение имени бизнес-правила (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]изменение имени бизнес-правила может потребоваться в том случае, если заданное имя не соответствует потребностям предприятия.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Должно существовать бизнес-правило. Дополнительные сведения см. в разделе [Создание и публикация бизнес-правила (службы Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md).  
  
### <a name="to-change-the-name-of-a-business-rule"></a>Изменение имени бизнес-правила  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Бизнес-правила** в раскрывающемся списке **Модель** выберите модель.  
  
4.  Из раскрывающегося списка **Сущность** выберите сущность.  
  
5.  Из раскрывающегося списка **Типы элементов** выберите тип элемента.  
  
6.  В сетке выберите строку бизнес-правила, которое необходимо изменить, и щелкните **Изменить**.  
  
7.  Введите новое имя для бизнес-правила.  
  
8.  Нажмите кнопку **Сохранить**.  
  
9. Нажмите кнопку **Опубликовать все**.  
  
10. В диалоговом окне подтверждения нажмите кнопку **ОК**. Значение в столбце **Состояние бизнес-правила**изменится на **Активно**.  
  
## <a name="see-also"></a>См. также:  
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  