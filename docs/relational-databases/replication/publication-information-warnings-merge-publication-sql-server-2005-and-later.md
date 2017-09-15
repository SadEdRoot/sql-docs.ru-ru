---
title: "Сведения о публикации, предупреждения (публикации слиянием, SQL Server 2005 и более поздние версии) | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 943f84af82aca8829571243927adf6dc4799ad96
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a>Сведения о публикации, предупреждения (публикации слиянием, SQL Server 2005 и более поздние версии)
  Вкладка **Предупреждения** доступна для распространителей, работающих с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] или более поздними версиями. Вкладка **Предупреждения** позволяет выполнять следующие задачи для выбранных публикаций:  
  
-   включить предупреждения;  
  
-   указать пороговые значения для предупреждений;  
  
-   указать оповещения, связанные с предупреждениями;  
  
## <a name="warnings-thresholds-and-alerts"></a>Предупреждения, пороговые значения и оповещения  
 По умолчанию монитор репликации отображает предупреждения для неинициализированных подписок: состояние **Неинициализированная подписка** отображается в виде предупреждения в столбце **Состояние** страниц, содержащих сведения о подписке. Для публикаций слиянием можно указать, ведут ли следующие дополнительные условия к предупреждениям.  
  
-   Приближение даты истечения срока подписки.  
  
     Это соответствует параметру **Предупреждать, если действие подписки истекает до порогового значения**. Если указанное пороговое значение достигнуто или превышено, состояние подписки отображается как **Срок действия скоро истекает или истек** (в том случае если не требуется отобразить более важную информацию).  
  
-   Превышение заданного времени синхронизации.  
  
     Это относится к параметрам **Предупреждать при превышении порогового значения длины слияния для удаленных соединений** и **Предупреждать при превышении порогового значения длины слияния для соединений по локальной сети**. Можно установить оба этих порога, но во время синхронизации используется только один из них. Агент слияния использует порог, соответствующий типу соединения.  
  
     Если указанное пороговое значение достигнуто или превышено, состояние подписки отображается как **Продолжительное слияние** (в том случае если не требуется отобразить более приоритетную информацию).  
  
-   Невозможность обработки заданного числа строк за указанное время.  
  
     Это относится к параметрам **Предупреждать, если число строк слияния в секунду снижается ниже порогового значения для удаленных соединений** и **Предупреждать при превышении порогового значения длины слияния для соединений по локальной сети.** Можно установить оба этих порога, но во время синхронизации используется только один из них. Агент слияния использует порог, соответствующий типу соединения.  
  
     Если указанное пороговое значение достигнуто или превышено, состояние подписки отображается как **Критическое для производительности** (в случае если не требуется отобразить более приоритетные сведения).  
  
 При включении предупреждения задается пороговое значение. Например, включая предупреждение **Предупреждать при превышении порогового значения длины слияния для соединений по локальной сети**, необходимо задать допустимый максимум времени для синхронизации слиянием.  
  
 Достижение порогового значения помимо отображения предупреждения в мониторе репликации может также вызывать системное предупреждение. Предупреждения определяются нажатием кнопки **Настройка предупреждений** и указанием сведений в диалоговом окне **Настройка предупреждений репликации** .  
  
## <a name="options"></a>Параметры  
 **Включено**  
 Выберите, чтобы включить предупреждение и указать пороговое значение.  
  
 **Предупреждение**  
 Включите параметр предупреждения для данного предупреждения по репликации.  
  
 **Предупреждение**  
 Описание предупреждения, связанного с пороговым значением.  
  
 **Порог**  
 Укажите пороговое значение.  
  
 **Настройка предупреждений**  
 Выберите строку в сетке **Предупреждения** и нажмите кнопку **Настройка предупреждений** для запуска диалогового окна **Настройка предупреждений репликации** . Это диалоговое окно позволяет определить оповещение, связанное с выбранным пороговым значением и предупреждением.  
  
 **Отменить изменения**  
 Нажмите эту кнопку для отмены всех произведенных изменений предупреждениях и пороговых значениях.  
  
> [!NOTE]  
>  Нажатие кнопки **Отменить изменения** не затрагивает предупреждения, определенные в диалоговом окне **Настройка предупреждений репликации** .  
  
 **Сохранить изменения**  
 Нажмите эту кнопку для сохранения всех произведенных изменений предупреждений и пороговых значений.  
  
## <a name="see-also"></a>См. также:  
 [Запуск монитора репликации](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для публикации (монитор репликации)](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Наблюдение за производительностью с помощью монитора репликации](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Наблюдение за репликацией](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Настройка пороговых значений и предупреждений в мониторе репликации](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  