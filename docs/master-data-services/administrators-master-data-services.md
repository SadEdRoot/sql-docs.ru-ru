---
title: "Администраторы (службы Master Data Services) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
caps.latest.revision: 14
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: c4944d4a47c7581c1273d21e5dbf3df59ae258a3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/07/2017

---
# <a name="administrators-master-data-services"></a>Администраторы (службы Master Data Services)
  В этой статье описываются типы администраторов в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]: администраторы моделей, администраторы сущностей и суперпользователь.  
  
## <a name="model-administrators"></a>Администраторы модели  
 В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор модели — это пользователь, имеющий разрешение **Администратор** , назначенное для объекта модели верхнего уровня на вкладке **Model Objects** (Объекты модели). Если у пользователя есть разрешение **Администратор** для конкретной модели, оно переопределяет все разрешения для дочерних объектов модели (разрешения для объектов и элементов модели).  
  
-   Если пользователь имеет доступ к функциональной области **Обозреватель** , то он может добавлять, удалять и обновлять все основные данные в этой области.  
  
-   Если пользователь имеет доступ к другим функциональным областям, то он может выполнять все административные задачи, доступные в функциональной области.  
  
 Каждая модель может иметь несколько администраторов. Каждый пользователь может быть администратором одной, нескольких или всех моделей в развертывании [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Сделать пользователя администратором модели можно в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] либо с помощью программных средств. Дополнительные сведения см. в разделе [Создание администратора модели (службы Master Data Services)](../master-data-services/create-a-model-administrator-master-data-services.md).  
  
## <a name="entity-administrators"></a>Администраторы сущностей  
 В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]администратор сущности — это пользователь, имеющий разрешения администратора, назначенные объекту сущности верхнего уровня на вкладке Model Objects (Объекты модели). Если у пользователя есть разрешения администратора на сущности, они превосходят и игнорируют другие разрешения на дочерние объекты сущности (разрешения на объекты и элементы модели).  
  
-   Если пользователь имеет доступ к функциональной области **Обозреватель** , то он может добавлять, удалять и обновлять все основные данные в этой области.  
  
-   Если для изменений сущности требуется утверждение администратора, администратор сущности может просмотреть и утвердить или отклонить набор изменений.  
  
 У каждой сущности может быть несколько администраторов. Каждый пользователь может быть администратором одной, нескольких или всех сущностей.  
  
 Сделать пользователя администратором сущности можно с помощью [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] либо программных средств. Дополнительные сведения см. в разделе [Создание администратора сущностей (службы Master Data Services)](../master-data-services/create-an-entity-administrator-master-data-services.md).  
  
## <a name="master-data-services-super-user"></a>Суперпользователь Master Data Services  
 В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]пользователю можно назначить разрешения для функциональной области "Суперпользователь". Пользователь с разрешениями для функциональной области "Суперпользователь" получает права администратора для всех моделей, а также для всех остальных функциональных областей. Сведения о разрешениях для функциональных областей см. в разделе [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md).  
  
 Суперпользователь по умолчанию задается для **учетной записи администратора** при создании базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] с помощью [мастера создания базы данных (диспетчер конфигурации служб Master Data Services)](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
 Суперпользователь может выполнять следующие задачи:  
  
-   получать доступ ко всем функциональным областям;  
  
-   добавлять, удалять и обновлять все основные данные для всех моделей в функциональной области **Обозреватель** .  
  
 Разрешения суперпользователя можно назначить нескольким пользователям или группам пользователей.  
  
## <a name="comparing-administrator-types"></a>Сравнение типов администраторов  
  
|Тип администратора|Description|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Суперпользователь|Разрешения, назначенные в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , не влияют на доступ администратора.<br /><br /> Может быть суперпользователем на основе разрешений функциональной области, назначенных ему явно, либо на основе разрешений, полученных в результате членства в некоторой группе.<br /><br /> Автоматически имеет все разрешения на все модели.<br /><br /> Автоматически имеет доступ ко всем функциональным областям.|  
|Администратор модели|Может быть администратором модели на основе разрешений администратора, назначенных ему явно, либо на основе разрешений, полученных в результате членства в некоторой группе.<br /><br /> Имеет доступ только к тем функциональным областям, к которым разрешен доступ.<br /><br /> Автоматически имеет все разрешения на все объекты и элементы в конкретной модели.|  
|Администратор сущности|Может быть администратором сущности на основе разрешений администратора, назначенных ему явно, либо на основе разрешений, полученных в результате членства в некоторой группе.<br /><br /> Имеет доступ только к тем функциональным областям, к которым разрешен доступ.<br /><br /> Автоматически имеет все разрешения на все объекты и элементы в конкретной сущности.<br /><br /> Может утвердить набор ожидающих изменений, если для изменений сущности требуется утверждение.|  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись блога [Security Improvements](http://go.microsoft.com/fwlink/p/?LinkId=615376)(Улучшения безопасности) на портале msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Создание администратора модели (службы Master Data Services)](../master-data-services/create-a-model-administrator-master-data-services.md)   
 [Создание базы данных служб Master Data Services](../master-data-services/install-windows/create-a-master-data-services-database.md)   
 [Уведомления (службы Master Data Services)](../master-data-services/notifications-master-data-services.md)  
  
  