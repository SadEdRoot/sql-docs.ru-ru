---
title: "Создание и управление подписками для серверов отчетов в режиме интеграции с SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriptions [Reporting Services], creating
- subscriptions [Reporting Services], deleting
- subscriptions [Reporting Services], managing
ms.assetid: 44be7ee2-33ce-46e4-9d1a-a20aaf43a227
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 56e19fe33a42086ef25001f605220f970d8b226a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="create-and-manage-subscriptions-for-sharepoint-mode-report-servers"></a>Создание подписок для серверов отчетов, работающих в режиме интеграции с SharePoint, и управление этими подписками
  Вы можете создать подписки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на доставку отчетов из веб-приложения SharePoint, работающим в режиме интеграции с SharePoint. Подписки могут доставлять отчеты в библиотеку документов, папку с файлами или по электронной почте. В этой статье приведена сводка по требованиям и шагам для создания подписки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим SharePoint &#124; SharePoint 2010 и SharePoint 2013|  
  
 При создании подписки существует три способа указать ее доставку.  
  
-   **Библиотека документов**. Можно создать подписку, обеспечивающую доставку документа, основанного на исходном отчете, в библиотеку, находящуюся на том же веб-сайте SharePoint, на котором хранится исходный отчет. Нельзя доставить документ в библиотеку, размещенную на другом сервере или на другом веб-сайте внутри одной и той же коллекции веб-сайтов. Чтобы доставить документ, нужно иметь разрешение на добавление объектов в библиотеку, в которую доставляется отчет.  
  
-   **Папка с файлами.** Документ, основанный на исходном отчете, можно доставить в общую папку файловой системы. Следует выбрать существующую папку, доступную через сетевое подключение.  
  
-   **Электронная почта.** Если сервер отчетов настроен для использования модуля доставки электронной почты сервера отчетов, можно создать подписку, которая будет направлять отчет или файл экспортированного отчета (сохраненный в формате выходных данных) в папку входящих сообщений электронной почты. Если требуется получать лишь уведомления без отчета или URL-адреса отчета, снимите флажки **Включить ссылку на отчет** и **Показать отчет внутри сообщения** .  
  
 **В этом разделе:**  
  
-   [Общие требования для подписок](#bkmk_subscription_requirements)  
  
-   [Создание подписки на доставку отчета в библиотеку SharePoint](#bkmk_tosharepoint_library)  
  
-   [Создание подписки на доставку отчета в библиотеку SharePoint](#bkmk_tosharepoint_library)  
  
-   [Создание подписки на доставку на сервер отчетов по электронной почте](#bkmk_subscription_for_email)  
  
-   [Просмотр или изменение подписки](#bkmk_to_modify_subscription)  
  
-   [Удаление подписки](#bkmk_to_delete_subscription)  
  
##  <a name="bkmk_subscription_requirements"></a> Общие требования для подписок  
 Чтобы создать подписку, отчет должен использовать сохраненные учетные данные, кроме того, необходимо разрешение на просмотр отчета и создание предупреждений.  
  
 При создании подписки можно выбрать формат выходного файла. Не всякий отчет может быть адекватно представлен в любом формате. Перед выбором формата для подписки, откройте отчет и экспортируйте его в различные форматы. Убедитесь в том, что он отображается так, как предполагалось.  
  
 Чтобы иметь возможность создавать подписки **, пользователям требуются разрешения списка** Изменение элементов [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в SharePoint. Дополнительные сведения см. в разделе [Справочная таблица по разрешениям на доступ к спискам и сайтам SharePoint для элементов сервера отчетов](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
> [!IMPORTANT]  
>  Подписка, доставляющая отчет в библиотеку или в общую папку, создает новый статический файл на базе исходного отчета, но он не является определением отчета, выполняемым в веб-части «Средство просмотра отчетов». Если в исходном отчете содержатся интерактивные возможности (такие, как ссылки детализации) или динамическое содержимое, эти возможности не будут представлены в статическом файле, доставляемом в целевое расположение. Если выбрать параметр «Веб-страница», можно сохранить интерактивность, но так как документ не является RDL-файлом, выполняемым в средстве просмотра отчетов, щелчок отчета создает в сеансе браузера новые страницы, которые необходимо прокрутить до конца, чтобы вернуться на сайт.  
  
 Просто заменить расширение файла экспортируемого отчета на RDL и запустить его в веб-части «Средство просмотра отчетов» невозможно. Если нужно создать подписку, предоставляющую текущий отчет, воспользуйтесь модулем доставки электронной почты сервера отчетов и укажите параметры, предусматривающие ссылку на этот отчет.  
  
 Настройки управления версиями библиотеки, содержащей доставленный документ, определяют, создается ли новая версия документа при каждой доставке. По умолчанию настройки управления версиями включены для каждой библиотеки. Если не указать явно значение **Без контроля версий**, при доставке создается новый основной номер версии. Создаются только основные версии документа. Дополнительные версии в результате доставки по подписке никогда не создаются, даже если разрешить управление версиями, что поддерживает дополнительные версии. Если ограничить число основных версий, подлежащих хранению, старые доставки будут заменяться новыми по достижении указанного предела.  
  
 Форматы выходных данных, выбираемые для подписки, основаны на модулях подготовки отчетов, которые установлены на сервере отчетов. Допускается выбор только тех форматов выходных данных, которые поддерживаются модулями подготовки отчетов, установленными на сервере отчетов.  
  
###  <a name="bkmk_tosharepoint_library"></a> Создание подписки на доставку отчета в библиотеку SharePoint  
  
1.  Перейдите к библиотеке SharePoint, в которой содержится отчет.  
  
2.  Щелкните стрелку вниз рядом с отчетом и выберите **Управление подписками**.  
  
3.  Нажмите кнопку **Добавить подписку**.  
  
4.  В списке **Модуль доставки**выберите пункт **Библиотека документов SharePoint**.  
  
5.  В области **Библиотека документов**выберите библиотеку, размещенную на том же веб-сайте.  
  
6.  В поле **Параметры файлов**укажите имя файла и заголовок для документа, который будет создан данной подпиской.  
  
7.  В поле **Формат вывода**выберите формат приложения.  
  
     По умолчанию применяется формат веб-архива (MHTML), так как он обеспечивает формирование самодостаточных HTML-файлов, которые, однако, не сохраняют интерактивных функций отчетов, которые могут содержаться в исходных отчетах.  
  
8.  В поле **Параметры перезаписи**укажите параметр, который будет определять, следует ли выполнять перезапись файла в ходе последующих доставок. Если нужно сохранить предыдущие доставки, можно выбрать параметр **Создать файл с уникальным именем**. Для создания уникальных имен файлов к именам новых файлов будут добавляться числа.  
  
9. В поле **Событие доставки**укажите расписание или событие, инициализирующее подписку. Можно создать пользовательское расписание, выбрать общее расписание при наличии такового или инициализировать подписку всякий раз при обновлении данных отчета, выполняемого с использованием данных моментального снимка. Дополнительные сведения о расписаниях и обработке данных см. в разделе [задание параметров обработки &#40; Службы Reporting Services в SharePoint интегрированная режим &#41; ](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
10. При создании подписки на параметризованный отчет в поле **Параметры**укажите значения, которые нужно использовать в отчете при обработке подписки. Раздел параметров на этой странице не отображается, если выбранный отчет не содержит параметров. Дополнительные сведения о параметрах см. в разделе [Настройка параметров опубликованного отчета (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
###  <a name="bkmk_subscription_for_sharedfolder"></a> Создание подписки для доставки в общую папку  
  
1.  Перейдите к библиотеке SharePoint, в которой содержится отчет.  
  
2.  Щелкните стрелку вниз рядом с отчетом и выберите **Управление подписками**.  
  
3.  Нажмите кнопку **Добавить подписку**.  
  
4.  В списке **Модуль доставки**выберите пункт **Общая папка Windows**.  
  
5.  В поле **Имя файла**введите имя файла, который будет создан в общей папке.  
  
6.  В поле **Путь**введите путь к папке в формате UNC, включающем сетевое имя компьютера. В путь к папке не следует включать заключительную обратную косую черту. Путь может выглядеть следующим образом: `\\ComputerName01\Public\MyReports`, где Public и MyReports — общие папки.  
  
7.  В поле **Формат отображения**выберите формат приложения для отчета.  
  
8.  В поле **Режим записи**выберите одно из следующих значений: **Нет**, **Автоувеличение**или **Перезапись**. Эти параметры определяют, будет ли файл перезаписываться в ходе последующих доставок. Если нужно сохранить предшествующие доставки, можно выбрать параметр **Автоувеличение**. Для создания уникальных имен файлов к именам новых файлов будут добавляться числа. При выборе параметра **Нет**доставка не будет осуществляться в случае, если файл с таким именем уже существует в целевом расположении.  
  
9. В поле **Расширение файла**выберите **True** , чтобы добавить расширение файла, соответствующее формату файлов приложения, или False, чтобы создать файл без расширения.  
  
10. В полях **Имя пользователя** и **Пароль**введите учетные данные, обладающие разрешением на запись данных в общую папку.  
  
11. В поле **Событие доставки**укажите расписание или событие, инициализирующее подписку. Можно создать пользовательское расписание, выбрать общее расписание при наличии такового или инициализировать подписку всякий раз при обновлении данных отчета, выполняемого с использованием данных моментального снимка. Дополнительные сведения о расписаниях и обработке данных см. в разделе [задание параметров обработки &#40; Службы Reporting Services в SharePoint интегрированная режим &#41; ](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
12. При создании подписки на параметризованный отчет в поле **Параметры**укажите значения, которые нужно использовать в отчете при обработке подписки. Дополнительные сведения о параметрах см. в разделе [Настройка параметров опубликованного отчета (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
###  <a name="bkmk_subscription_for_email"></a> Создание подписки на доставку на сервер отчетов по электронной почте  
  
1.  Перейдите к библиотеке SharePoint, в которой содержится отчет.  
  
2.  Щелкните стрелку вниз рядом с отчетом и выберите **Управление подписками**.  
  
3.  Нажмите кнопку **Добавить подписку**.  
  
4.  В списке **Модуль доставки**выберите пункт **Электронная почта**.  
  
5.  В поле **Параметры доставки**укажите адрес электронной почты, по которому следует направлять отчет.  
  
6.  При необходимости можно изменить строку «Тема». Строка «Тема» использует встроенные параметры, отображающие имя отчета и время его обработки. Это единственные встроенные параметры, которые могут быть использованы. Эти параметры представляют собой заполнители, обеспечивающие возможность изменения текста, отображаемого в строке «Тема», но их можно заменить статическим текстом.  
  
7.  Выберите **Включить ссылку на данный отчет** , если хотите внедрить URL-адрес отчета в тело сообщения.  
  
8.  В поле **Содержимое отчета**укажите, нужно ли внедрять текст отчета в тело сообщения.  
  
     Формат подготовки отчетов и веб-браузер определяют, является ли отчет внедренным или прикрепленным. Если браузер поддерживает HTML 4.0 и MHTML, и выбран формат подготовки отчета в виде веб-архива, отчет внедряется в сообщение. Все другие форматы подготовки отчета (CSV, PDF и т. д.) рассылают отчеты в виде вложений. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не проверяют размер вложения или сообщения перед отправкой отчета. Если вложение или сообщение превышает максимальный предел, допустимый вашим почтовым сервером, отчет не будет доставлен. Для больших отчетов выберите другой вариант доставки отчетов (например, URL-адрес или уведомление).  
  
9. В поле **Событие доставки**укажите расписание или событие, инициализирующее подписку. Можно создать пользовательское расписание, выбрать общее расписание при наличии такового или инициализировать подписку всякий раз при обновлении данных отчета, выполняемого с использованием данных моментального снимка. Дополнительные сведения о расписаниях и обработке данных см. в разделе [задание параметров обработки &#40; Службы Reporting Services в SharePoint интегрированная режим &#41; ](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).  
  
10. При создании подписки на параметризованный отчет в поле **Параметры**укажите значения, которые нужно использовать в отчете при обработке подписки. Дополнительные сведения о параметрах см. в разделе [Настройка параметров опубликованного отчета (службы Reporting Services в режиме интеграции с SharePoint)](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
###  <a name="bkmk_to_modify_subscription"></a> Просмотр или изменение подписки  
  
1.  Перейдите к библиотеке SharePoint, в которой содержится отчет.  
  
2.  Щелкните стрелку вниз рядом с отчетом и выберите **Управление подписками**.  
  
3.  Каждая подписка идентифицируется типом доставки. Щелкните тип подписки, чтобы просмотреть и изменить существующие свойства.  
  
###  <a name="bkmk_to_delete_subscription"></a> Удаление подписки  
  
1.  Перейдите к библиотеке SharePoint, в которой содержится отчет.  
  
2.  Щелкните стрелку вниз рядом с отчетом и выберите **Управление подписками**.  
  
3.  Установите флажок рядом с подпиской и нажмите кнопку **Удалить**.  
  
## <a name="see-also"></a>См. также  
 [Подписки и доставка (службы Reporting Services)](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Работы с электронной почтой в службах Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)   
 [Доставка отчетов в общие папки с помощью служб Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)   
 [Доставка библиотек SharePoint в службах Reporting Services](../../reporting-services/subscriptions/sharepoint-library-delivery-in-reporting-services.md)   
 [Настройка сервера отчетов для работы с электронной почтой (диспетчер конфигурации служб Reporting Services)](http://msdn.microsoft.com/en-us/b838f970-d11a-4239-b164-8d11f4581d83)  
  
  