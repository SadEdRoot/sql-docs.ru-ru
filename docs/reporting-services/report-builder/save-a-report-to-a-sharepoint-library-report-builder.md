---
title: "Сохранение отчета в библиотеке SharePoint (построитель отчетов) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6e87cb6c8daa8744b676d5ed78ed8339705f28e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a>Сохранение отчета в библиотеке SharePoint (построитель отчетов)
  Чтобы сохранить отчет на сервере отчетов, настроенном для режима интеграции с SharePoint, необходимо перейти на сервер SharePoint и установить соединение с сервером отчетов. В определении отчета все ссылки на элементы, связанные с отчетом, должны использовать переменные, относящиеся к серверу отчетов SharePoint. Связанные элементы включают вложенные отчеты, детализированные отчеты и ресурсы (например, изображения, хранящиеся в Интернете). Дополнительные сведения см. в разделе [Указание путей к внешним элементам (построитель отчетов и службы SSRS)](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Необходимо обладать разрешением **Член** или **Владелец** на сайте SharePoint для задания свойств проекта.  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a>Сохранение отчета на сайте SharePoint  
  
1.  В построителе отчетов нажмите кнопку **Сохранить**. **Сохранить как***\<элемент отчета >* откроется диалоговое окно.  
  
    > [!NOTE]  
    >  Во время повторного сохранения отчет автоматически сохраняется в предыдущем расположении. Чтобы изменить расположение, используйте параметр **Сохранить как** .  
  
2.  Также можно щелкнуть ссылку **Последние сайты и серверы** , чтобы вывести список недавно использовавшихся серверов отчета и сайтов SharePoint.  
  
3.  Выберите сайт SharePoint и щелкните **Сохранить**.  
  
    > [!NOTE]  
    >  Если не сохранять измененный отчет в течение более 10 часов, он отключается от сервера без сохранения. Если это произойдет, в правой нижней строке состояния щелкните **Отключение**, затем щелкните **Подключение**. Последний сервер будет в списке доступных серверов. Выберите его, и отчет вновь подключится.  
  
## <a name="see-also"></a>См. также  
 [Поиск, просмотр и управление отчетами &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  