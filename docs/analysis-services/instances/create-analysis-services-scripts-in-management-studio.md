---
title: Создание скриптов служб Analysis Services в среде Management Studio | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28b1b0068f9ddd9bf47bc2fe93177db469c8b4f1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="create-analysis-services-scripts-in-management-studio"></a>Создание скриптов служб Analysis Services в среде Management Studio
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поддерживает функции создания скриптов, шаблоны и редакторы, используемые для разработки скриптов с объектами и задачами служб Analysis Services.  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a>Создание скриптов для задач служб Analysis Services в среде Management Studio  
 Создание скриптов для задач в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] осуществляется выбором одного из параметров "Скрипт" в диалоговом окне, соответствующем задаче. Все диалоговые окна, используемые для выполнения задач, таких как резервное копирование и восстановление базы данных, обработка объекта или создание агрегата, содержат параметр «Скрипт» в верхней части. Если выбрать один из этих параметров, создается скрипт XMLA на основе сведений и параметров в диалоговом окне.  
  
 По умолчанию скрипт создается и помещается в окно редактора запросов XMLA, но вы можете развернуть список параметров «Скрипт», чтобы направить скрипт в буфер обмена Windows или в файл.  
  
#### <a name="to-script-an-analysis-services-task"></a>Создание скрипта для задачи служб Analysis Services  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
2.  Щелкните правой кнопкой мыши базу данных и выберите команду **Резервное копирование**. Откроется диалоговое окно «Резервное копирование базы данных». Укажите имя файла резервной копии и выберите параметры для этой резервной копии.  
  
3.  Нажмите кнопку **Скрипт** в верхней части диалогового окна. Функция скриптов является частью всех диалоговых окон, относящихся к задачам, в среде Management Studio. Она имеет следующие параметры: параметр **Записать скрипт в новое окно запроса** открывает окно редактора запросов, параметр **Записать скрипт в файл** сохраняет скрипт XMLA в файл, а параметр **Записать скрипт в буфер обмена** сохраняет скрипт XMLA в буфер обмена.  
  
     Заметьте, что вариант **Записать скрипт в задание** , отображаемый в среде Management Studio, не поддерживается для скриптов служб Analysis Services.  
  
4.  Если выбрать вариант по умолчанию **Записать скрипт в новое окно запроса**, то созданный скрипт помещается в окно запроса XMLA.  
  
     Теперь вы можете закрыть диалоговое окно «Резервное копирование базы данных» и непосредственно изменить или выполнить скрипт XMLA.  
  
## <a name="script-analysis-services-objects-in-management-studio"></a>Создание скриптов для объектов служб Analysis Services в среде Management Studio  
 Создать сценарий для объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно, если щелкнуть правой кнопкой мыши объект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрать пункт **Используя CREATE**, **Используя ALTER**или **Используя DELETE**. Любой их этих параметров может выводить результат в окно или в файл, но, вне зависимости от того, куда направлен скрипт, он будет иметь форму скрипта DDL в упаковщике XML для аналитики. Основное преимущество этих скриптов состоит в том, что их можно запустить для любого указанного сервера. Кроме того, можно изменять имена скриптов и запускать скрипты на повторяющейся основе для массового создания, изменения или удаления объектов.  
  
 Скрипты можно создавать для элементов базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в том числе источников данных, представлений источников данных, кубов, измерений, структур интеллектуального анализа данных и ролей.  
  
 Для работы со скриптами необходимо иметь представление об XML для аналитики (XMLA). Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] имеет функцию автоматического создания скрипта XMLA, необходимого для создания таких объектов, как кубы. Эта функция автоматизации позволяет упростить изучение XML для аналитики. Дополнительные сведения об использовании XMLA см. в разделе [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md). Дополнительные сведения об использовании XMLA см. в разделе [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).  
  
> [!IMPORTANT]  
>  При написании скрипта для объекта роли необходимо учитывать, что права доступа содержатся в защищаемых объектах, а не в ролях, с которыми они связаны.  
  
#### <a name="to-script-analysis-services-objects"></a>Создание скриптов для объектов служб Analysis Services  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
2.  Выберите объект, для которого требуется разработать скрипт создания, изменения или удаления объектов.  
  
3.  Щелкните объект правой кнопкой мыши, наведите указатель на элемент **Создать скрипт для куба**, затем на пункт **Используя CREATE**, **Используя ALTER**или **Используя DELETE**. Выберите один из следующих вариантов: **Новое окно редактора запросов** — чтобы открыть окно редактора запросов, **Файл** — чтобы сохранить скрипт XMLA в файл или **Буфер обмена** — чтобы сохранить скрипт XMLA в буфер обмена.  
  
    > [!NOTE]  
    >  Если требуется создать несколько различных версий файла, выберите пункт **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Редактор запросов XMLA & #40; Analysis Services — многомерные данные & #41;](http://msdn.microsoft.com/library/14623019-7839-4038-9d12-2f8953d2ec04)  
  
  
