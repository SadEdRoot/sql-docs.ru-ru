---
title: Обновление монитора активности заданий | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 652fa02e7410d9d62f8b4787c87bb02bc0e88816
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="job-activity-monitor-refresh"></a>Обновление монитора активности заданий
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Настройки обновления** используется для настройки частоты получения монитором активности заданий новых данных об активности сервера. Монитор активности заданий должен выполнять запросы на контролируемом сервере для получения данных для сетки монитора активности заданий. Если интервал автообновления составляет менее 30 секунд, время выполнения этих запросов может влиять на производительность сервера.  
  
 Для открытия данного диалогового окна выберите пункт **Просмотреть настройки обновления**в разделе **Состояние** монитора активности заданий.  
  
## <a name="options"></a>Параметры  
 **Автоматическое обновление каждые**  
 Выберите, чтобы включить автоматическое обновление сведений монитора активности. По умолчанию эта настройка отключена.  
  
 **секунд**  
 Количество секунд между попытками автообновления. Значение по умолчанию — 60 секунд. При установке значения 5 или менее обновление будет производиться каждые 5 секунд.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за активностью заданий](http://msdn.microsoft.com/library/71cb432b-631d-4b8b-9965-e731b3d8266d)  
  
  
