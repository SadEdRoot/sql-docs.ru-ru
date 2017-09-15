---
title: "Создание, изменение и удаление расписаний | Документы Microsoft"
ms.custom: 
ms.date: 07/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
caps.latest.revision: 50
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 66a306d07b8556fe43659d4b078e2d31f3d51900
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="create-modify-and-delete-schedules"></a>Создание, изменение и удаление расписаний
  В этом подразделе представлены сведения о создании, изменении и удалении общих расписаний [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .  Для управления общими расписаниями для собственного режима используйте страницу "Расписания" на веб-портале или папку "Общие расписания" в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Для режима интеграции с SharePoint используйте страницы управления для приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Определите, используется ли расписание, одним из описанных ниже способов.  
  
-   **Веб-портал.** Изучите значения даты последнего запуска, даты следующего запуска и состояния на странице "Параметры сайта" &gt; "Общие расписания". Если расписание больше не запускается из-за завершения срока действия, дата завершения отображается в поле состояния. Дополнительные сведения см. в статье [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md).
  
-   **[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)].** Просмотреть страницу "Отчеты" для данного общего расписания. На этой странице перечислены все отчеты и общие наборы данных, использующие общее расписание. Дополнительные сведения см. в разделе [Службы Reporting Services в среде SQL Server Management Studio ](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md).
  
-  **Журналы.** Просмотрите файлы журнала выполнения или журналы трассировки, чтобы определить, запускались ли отчеты в заданные расписанием моменты времени. Дополнительные сведения см. в разделе [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="when-you-delete-a-shared-schedule"></a>Удаление общего расписания  
Общие расписания следует удалять вручную на странице "Расписания" на веб-портале или в папке "Общие расписания" в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. При удалении общего расписания, которое в данный момент используется, все ссылки на него заменяются ссылками на расписание отчета.  
 
При удалении общего расписания, используемого несколькими отчетами и подписками, сервер отчетов создаст для каждого из них отдельное расписание. В созданных расписаниях будут содержаться дата, время и шаблон повторений, которые были заданы в общем расписании. Обратите внимание, что службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не обеспечивают централизованного управления отдельными расписаниями. После удаления общего расписания придется поддерживать расписания для каждого конкретного элемента.  
  
**Примечание.**  Если вы не уверены, что общее расписание используется, удалите его в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] на веб-портале. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] предоставляет те же функции управления общим расписанием, что и диспетчер отчетов, но содержит дополнительную страницу «Отчеты» с именами всех отчетов, использующих общее расписание.  
   
 Удаление расписания и приостановка его действия в связи с истечением срока его действия — это не одно и то же. После истечения срока действия использование расписания будет приостановлено, однако его фактическое удаление не происходит. Поскольку расписания применяются для автоматического выполнения множества функций, они никогда не удаляются автоматически. Расписания с истекшим сроком действия предоставляют администратору сервера отчетов сведения о причинах внезапной остановки автоматизированного процесса. Если бы расписание по истечении срока действия удалялось, администратор сервера отчетов не смог бы правильно определить причины возникновения проблем и тратил бы лишнее время на исследование всего функционального процесса.  
 
 ## <a name="when-you-delete-a-report-specific--schedule"></a>Удаление расписания, связанного с отчетами  
Расписания, зависящие от конкретного отчета и подписки, удаляются при удалении этого отчета или подписки либо при выборе другого метода выполнения отчета или подписки. Например, если выбрать **Всегда запускать отчет с самыми последними данными** , удалится расписание, созданное для этого отчета и запускающее отчет как моментальный снимок состояния выполнения отчета.  

Расписание отчета с истекшим сроком действия остается прикрепленным к отчету. Определить, истек ли срок действия расписания, можно, проверив дату окончания его действия. Общие расписания с истекшим сроком действия остаются в списке общих расписаний. Поле «Состояние» указывает, истек ли срок действия расписания. Можно восстановить расписание, указав новую дату окончания его действия, либо удалить ссылки на него, если расписание больше не нужно.  
  
## <a name="bkmk_native"></a> Создание, удаление или изменение общего расписания (веб-портал)  
 Создание и изменение расписания заключается в установке параметров частоты, с которой оно выполняется.  
  
 Расписание может быть создано или изменено в любое время. Но если оно начинает выполняться до сохранения изменений, то используется его старая версия. Изменения, внесенные в расписание, вступают в силу только после его сохранения.  
  
 Перед изменением общего расписания его выполнение можно приостановить. В этом случае изменения вступят в силу при возобновлении его работы.  

1.  На веб-портале выберите на панели инструментов **Параметры** ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) . **Примечание.** Если кнопка **Параметры сайта** недоступна, значит отсутствуют разрешения для доступа к настройкам веб-сайта.
2.  Щелкните элемент **Параметры сайта**.  
3.  Нажмите кнопку **Расписания**.  
4.  Нажмите кнопку **Создать расписание**. Чтобы изменить существующее расписание, щелкните его имя.  
5.  Введите описательное имя расписания.  
6.  Выберите **Час**, **День**, **Неделя**или **Месяц**. Щелкните **Однократно** , чтобы расписание сработало только один раз. Дополнительные настройки появляются после задания базовых параметров расписания.  
7.  Выберите дату запуска расписания (необязательно). Значением по умолчанию является текущая дата. Можно отложить запуск расписания, выбрав более позднюю дату.  
8.  Введите дату прекращения действия расписания (необязательно). При наступлении этой даты расписание прекращает работу, но не удаляется.  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)] 

### <a name="to-delete-a-shared-schedule-web-portal"></a>Удаление общего расписания (веб-портал)  
  
1.  На веб-портале щелкните **Настройки сайта**на главной панели инструментов.     
2.  В разделе **Другие** на странице выберите пункт **Управление общими расписаниями**.  
3.  Установите флажок рядом с расписанием, которое необходимо удалить, и нажмите кнопку **Удалить**.  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a>Создание, удаление и изменение общих расписаний (среда Management Studio)  
 Общее расписание содержит расписание и шаблон повторений, которые могут использоваться любым числом опубликованных отчетов и подписок, выполняющихся на сервере отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Если одновременно выполняется много отчетов и подписок, то для них можно создать общее расписание. Если в дальнейшем будет необходимо изменить шаблон повторений или дату окончания, то это можно будет сделать всего в одном месте.  
  
 Общие расписания проще в обслуживании и обеспечивают большую гибкость при управлении запланированными операциями. Например, выполнение общего расписания можно приостанавливать и возобновлять. Кроме того, если обнаружится, что одновременно выполняется слишком много запланированных операций, можно создать несколько общих расписаний, которые могут выполняться в разное время, а затем настроить их таким образом, чтобы распределить нагрузку на сервер отчетов.  
  
### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a>Создание или изменение общего расписания (среда Management Studio)  
  
1.  Запустите среду [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] и подключитесь к экземпляру сервера отчетов:  
2.  В обозревателе объектов разверните узел сервера отчетов.  
3.  Щелкните правой кнопкой мыши папку **Общие расписания** и выберите команду **Создать расписание**. Выводится страница «Общие» диалогового окна **Создание общего расписания** .  
  
     Чтобы изменить существующее общее расписание, откройте папку "Общие расписания", щелкните правой кнопкой мыши расписание, которое необходимо изменить, и выберите пункт **Свойства**.  
  
4.  Введите описательное имя расписания.  
5.  Выберите дату запуска расписания (необязательно). Значением по умолчанию является текущая дата.  
6.  Введите дату прекращения действия расписания (необязательно). При наступлении этой даты расписание прекращает работу, но не удаляется.  
7.  Чтобы настроить повторяющееся расписание, выберите **Час**, **День**, **Неделя**или **Месяц**. Откроется окно дополнительных параметров. Используйте их для настройки частоты повторения расписания, задав нужный час, день, неделю или месяц.  
  
     Чтобы задать однократное (неповторяющееся) расписание, выберите **Однократно**и укажите **Время начала**.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a>Удаление общего расписания (среда Management Studio)  
  
1.  В обозревателе объектов разверните узел сервера отчетов.  
2.  Чтобы убедиться в том, что общее расписание не используется отчетами, разверните папку "Общие расписания", щелкните правой кнопкой мыши расписание, которое нужно изменить, и выберите пункт **Свойства**.
3. Откройте вкладку **Отчеты** , чтобы просмотреть список отчетов, использующих это расписание.
Нажмите кнопку **Отмена**.
4.  Разверните папку "Общие расписания", щелкните нужное расписание правой кнопкой и нажмите кнопку **Удалить**. Появится диалоговое окно **Удаление объектов из каталога** .  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 При удалении общего расписания, используемого несколькими отчетами и подписками, сервер отчетов создаст для каждого из них отдельное расписание. В созданных расписаниях будут содержаться дата, время и шаблон повторений, которые были заданы в общем расписании.
 
##  <a name="bkmk_sharepoint"></a> Создание общих расписаний и управление ими (режим интеграции с SharePoint)  
 Чтобы создавать, изменять и удалять общие расписания на веб-сайте SharePoint, необходимо являться администратором веб-сайта.  
  
 Конкретное расписание можно идентифицировать по его описательному имени. Если имя не указано, можно идентифицировать его через факты о расписании, такие как шаблоны повторения или дата и время запуска.  
  
> [!NOTE]  
>  Для создания общих расписаний требуется служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="create-shared-schedules-sharepoint-mode"></a>Создание общих расписаний (режим интеграции с SharePoint)  
1.  Щелкните **Действия сайта**.  
2.  Щелкните элемент **Настройки сайта**.  
3.  В разделе служб Reporting Services щелкните **Управление общими расписаниями**.  
4.  Нажмите кнопку **Добавить расписание** , чтобы открыть страницу «Свойства расписания».  
5.  Введите описательное имя расписания. На страницах приложений, используемых для работы с отчетами служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , это имя появится в раскрывающихся списках на страницах определения расписания на веб-сайте. Избегайте неудобных для чтения длинных имен. Следуйте соглашению об именах, согласно которому наиболее описательные сведения помещаются в начале имени.  
6.  Выберите частоту. В зависимости от выбранной частоты могут изменяться отображаемые на странице параметры расписания, поддерживающие частоту (например, если выбрать **Месяц**, то на странице появится название каждого месяца).  
7.  Определите расписание. В одном расписании могут поддерживаться не все сочетания расписания.  
8.  Установите дату начала и окончания.  
9. Нажмите кнопку **ОК**.  
  
### <a name="delete-shared-schedules-sharepoint-mode"></a>Удаление общих расписаний (режим интеграции с SharePoint)  
 Все расписания — и общие, и расписания отчетов — должны удаляться вручную. Если удалить общее расписание, которое используется, все ссылки на него замещаются неопределенными пользовательскими расписаниями (то есть пользовательскими расписаниями, не имеющими сведений о дате и времени).  
  
1.  Щелкните **Действия сайта**.  
2.  Щелкните элемент **Настройки сайта**.  
3.  В разделе служб Reporting Services щелкните **Управление общими расписаниями**.  
4.  Выберите расписание и нажмите кнопку **Удалить**.  
 
  
## <a name="see-also"></a>См. также  
 [Schedules](../../reporting-services/subscriptions/schedules.md)   
 [Приостановка и возобновление общих расписаний](../../reporting-services/subscriptions/pause-and-resume-shared-schedules.md)   
 [Кэшировать отчет &#40; Диспетчер отчетов &#41;](../../reporting-services/report-server/cache-a-report-report-manager.md)   
 [Добавить моментальный снимок для отчета, истории &#40; Диспетчер отчетов &#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
