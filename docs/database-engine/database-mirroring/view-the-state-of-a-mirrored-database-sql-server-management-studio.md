---
title: Просмотр состояния зеркального отображения базы данных (среда SQL Server Management Studio) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e0bdfdc0f78cda06af9b44a313c82c5f97e4b2fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a>Просмотр состояния зеркального отображения базы данных (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Во время сеанса зеркального отображения базы данных можно просмотреть его состояние на странице **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a>Просмотр состояния сеанса зеркального отображения базы данных  
  
1.  После подключения к экземпляру основного сервера в обозревателе объектов щелкните имя сервера, чтобы развернуть дерево сервера.  
  
2.  Раскройте узел **Базы данных**и выберите базу данных для зеркального отображения.  
  
3.  Щелкните базу данных правой кнопкой мыши, выберите **Задачи**, а затем **Зеркальное отображение**. Откроется страница **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
4.  После начала зеркального отображения на панели **Состояние** отражается та же информация о состоянии сеанса зеркального отображения, что и при выборе страницы **Зеркальное отображение** или нажатии кнопки **Обновить** . Возможны следующие состояния.  
  
    |Состояния|Объяснение|  
    |------------|-----------------|  
    |\<пусто>|Не существует ни одного сеанса зеркального отображения, а сведения об активности не представлены на странице **Зеркальное отображение** .|  
    |Пауза|Основная база данных запущена, но не посылает никаких записей журнала на зеркальный сервер. Зеркальное отображение базы данных недоступно.|  
    |Нет соединения|Экземпляр основного сервера не может подключиться к другому участнику или следящему серверу (если он есть).|  
    |Синхронизация|Содержимое зеркальной базы данных отстает от содержимого основной базы данных. Экземпляр основного сервера отправляет записи журнала на экземпляр зеркального сервера, который применяет эти изменения к зеркальной базе данных для выполнения наката.<br /><br /> В начале сеанса зеркального отображения базы данных основная и зеркальная базы данных синхронизированы.|  
    |Отработка отказа|Процесс отработки отказа вручную (смена ролей) начался на экземпляре основного сервера, но еще не был принят зеркальным сервером.|  
    |синхронизировано;|Зеркальная база данных содержит те же данные, что и основная база данных. Ручная и автоматическая отработка отказа возможна *только* в этом состоянии.|  
  
## <a name="see-also"></a>См. также:  
 [Состояния зеркального отображения (SQL Server)](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
  
