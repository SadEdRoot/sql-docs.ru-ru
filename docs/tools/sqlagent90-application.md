---
title: "Приложение sqlagent90 | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9aa0fab5e21ffb7ac7b39728ed025a4b467f8102
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="sqlagent90-application"></a>sqlagent90, приложение
  Приложение **sqlagent90** запускает агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из командной строки. Обычно агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должен запускаться из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или с помощью методов SQL-DMO в приложении. Запускайте приложение **sqlagent90** из командной строки только, когда выполняется диагностика агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или если такое указание получено от основного поставщика поддержки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## <a name="arguments"></a>Аргументы  
 **-c**  
 Указывает, что агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запускается из командной строки и не зависит от диспетчера управления службами Microsoft Windows. При использовании параметра **-c** агентом [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] нельзя управлять с помощью оснастки "Службы" в элементе "Администрирование" панели управления и из диспетчера конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Этот аргумент является обязательным.  
  
 **-v**  
 Указывает, что агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работает в подробном режиме и производит запись диагностических данных в окно командной строки. Диагностические данные — это те же данные, которые записываются в журнал ошибок агента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **-i** *instance_name*  
 Указывает, что агент [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] подключается к именованному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , определенному аргументом *имя_экземпляра*.  
  
## <a name="remarks"></a>Замечания  
 После отображения сообщения с указанием авторских прав приложение **sqlagent90** отображает выводимые данные в окне командной строки, только если указан параметр **-v** . Чтобы остановить работу приложения **sqlagent90**, нажмите клавиши CTRL+C в командной строке. Не закрывайте окно командной строки перед остановкой работы приложения **sqlagent90**.  
  
## <a name="see-also"></a>См. также:  
 [Задачи автоматизированного администрирования (агент SQL Server)](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  