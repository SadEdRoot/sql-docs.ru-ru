---
title: Страница "Выполнение" (мастеры групп доступности AlwaysOn) | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.failoverwizard.progress.f1
- sql13.swb.adddatabasewizard.progress.f1
- sql13.swb.addreplicawizard.progress.f1
- sql13.swb.newagwizard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1fe9313834f9e6cc4f3af9364c9e1aecebe6cbdc
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768570"
---
# <a name="progress-page-always-on-availability-group-wizards"></a>Страница "Выполнение" (мастеры групп доступности AlwaysOn)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Используйте это диалоговое окно для просмотра шагов мастера [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , запущенного в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Индикатор выполнения указывает относительный прогресс шагов мастера.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Дополнительные сведения**  
 Щелкните стрелку вниз, чтобы отобразить сетку выполнения, в которой по порядку отображены любые завершенные шаги, за которыми отображается текущая операция. Сетка содержит следующие столбцы:  
  
 **Название**  
 Отображает фразу, которая описывает конкретный шаг.  
  
 **Состояние**  
 Показывает результат завершенных шагов и процент завершения текущего шага.  
  
|Результат|Описание|  
|------------|-----------------|  
|**Ошибка**|Указывает, что при выполнении операции в этом шаге произошла ошибка. Щелкните ссылку, чтобы отобразить диалоговое окно с сообщением, описывающим ошибку.|  
|**Выполняется (** *процент завершения* **)**|Указывает, что операция происходит сейчас и выполняет оценку процентной доли завершения этого шага.|  
|**Успешно**|Указывает, что операция, выполнявшаяся в этом шаге, завершилась успешно.|  
  
 **Меньше сведений**  
 Выберите, чтобы скрыть сетку хода выполнения.  
  
 **Отмена**  
 Нажмите, чтобы пропустить любые остающиеся операции и завершить работу мастера.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления базы данных в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
-   [Использование мастера отработки отказа группы доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
