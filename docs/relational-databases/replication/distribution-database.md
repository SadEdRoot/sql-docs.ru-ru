---
title: База данных распространителя | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
caps.latest.revision: 26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9ed2c61eed380a6ec98e3aacb2b3017af9397b74
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="distribution-database"></a>База данных распространителя
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В базе данных распространителя хранятся метаданные и данные журнала для всех типов репликации, а также транзакции для репликации транзакций.  
  
 В большинстве случаев достаточно одной базы данных распространителя. Однако если несколько издателей используют один распространитель, то имеет смысл для каждого издателя создать базу данных распространителя. Это гарантирует то, что данные, проходящие через каждую базу данных распространителя, будут различаться. Для каждого распространителя можно указать базу данных с помощью мастера настройки распространителя. При необходимости в окне **Свойства распространителя** можно указать дополнительные базы данных распространителя.  
  
## <a name="options"></a>Параметры  
 **Имя базы данных распространителя**  
 Введите имя базы данных распространителя. По умолчанию, для базы данных распространителя задано имя «distribution». Максимальная длина имени — 128 символов. Имя должно быть уникальным в пределах экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме того, оно должно соответствовать правилам для идентификаторов. Дополнительные сведения см. в разделе [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 **Папка для файла базы данных распространителя** и **Папка для журнала базы данных распространителя**  
 Введите путь для базы данных распространителя и файлов журналов. Эти пути должны быть локальными по отношению к распространителю и должны начинаться с буквы диска и двоеточия (например C:). Буквы подключенных дисков и сетевые пути являются недопустимыми.  
  
> [!NOTE]  
>  Время, которое требуется для записи транзакций, можно уменьшить (и тем самым повысить производительность репликации) путем размещения журнала базы данных распространителя на отдельном диске.  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
