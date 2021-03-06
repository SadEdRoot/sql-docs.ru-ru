---
title: Изменение часовых поясов и параметров часов на сервере отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: subscriptions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- time zones [Reporting Services]
- clocks [Reporting Services]
- schedules [Reporting Services], clock settings
- schedules [Reporting Services], time zones
ms.assetid: 69a19468-baa1-40f6-b158-8afdab0f8968
caps.latest.revision: 22
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f9e613a2212a852f386343de6463d06b9b57b3ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="change-time-zones-and-clock-settings-on-a-report-server"></a>Изменение часовых поясов и настроек часов на сервере отчетов
  Сервер отчетов всегда использует локальное время компьютера, на котором он установлен. Задать для сервера отчетов другой часовой пояс нельзя. Если клиентское приложение обращается к серверу отчетов, работающему в другом часовом поясе, запланированная операция выполняется в соответствии с часовым поясом сервера отчетов. На страницах управления диспетчером отчетов и службами SharePoint часовой пояс указывается на каждой странице расписания, чтобы пользователь точно знал, когда будет выполнена запланированная операция. Например, на странице для создания пользовательского расписания указано «Время выражено в (UTC-08:00) по тихоокеанскому времени (США и Канада)».  
  
## <a name="changing-the-time-zone-native-mode"></a>Изменение часового пояса (собственный режим)  
 Изменения часового пояса на компьютере, на котором размещен сервер отчетов, вступают в силу только после перезапуска службы сервера отчетов.  
  
 Значения отметки времени существующих моментальных снимков журнала отчета синхронизируются с новым параметром часового пояса. Если вы создали моментальный снимок журнала отчета в 9:00 и затем перевели часовой пояс на один часовой пояс вперед, отметка времени на созданном моментальном снимке изменится с 9:00 на 10:00.  
  
 Временные параметры расписаний остаются прежними, за исключением того, что расписания сопоставляются с новым часовым поясом. Например если запланированная задача должна была запуститься в 2:00 по стандартному тихоокеанскому времени, а часовой пояс изменили на восточно-австралийское стандартное время, то задача будет выполнена в 2:00 по восточно-австралийскому стандартному времени.  
  
 Значения отметок времени, являющихся свойствами (например время создания папки или элемента связанного отчета), не синхронизируются с новым значением часового пояса. Если элемент создан 25 июня в 9:00, после чего будет изменен часовой пояс или время, отметка времени останется прежней.  
  
## <a name="changing-the-time-zone-sharepoint-mode"></a>Изменение часового пояса (режим интеграции с SharePoint)  
 Конфигурация часового пояса для режима интеграции с SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] управляется как часть региональных настроек SharePoint. Дополнительные сведения см. в разделе [Загрузка пакета обновления 1 (SP1) для SharePoint Server 2010 (http://technet.microsoft.com/library/cc824907.aspx)](http://technet.microsoft.com/library/cc824907.aspx).  
  
## <a name="changing-the-clock-settings"></a>Изменение времени  
 Изменение показаний часов компьютера не влияет на значения существующих отметок времени (например, если перевести часы на 1 час вперед, отметки времени моментальных снимков журналов отчетов не изменятся). Перед тем как обработчик планирования и доставки примет новое значение времени, возможна задержка длительностью 10 секунд. Фактическая длительность задержки может оказаться иной, если изменены параметры интервала опроса в файлах конфигурации.  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка службы сервера отчетов](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)   
 [Расписания](../../reporting-services/subscriptions/schedules.md)  
  
  
