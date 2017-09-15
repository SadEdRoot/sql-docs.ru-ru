---
title: "Уровень совместимости для табличных моделей в службах Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 07/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 58710676e09a49ecc1b49ad37c656e3589ee1257
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="compatibility-level-for-analysis-services-tabular-models"></a>Уровень совместимости для табличных моделей служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  *Уровень совместимости* ссылается на поведения конкретного выпуска в ядро служб Analysis Services. Например DirectQuery и метаданные табличных объектов имеют разные реализации в зависимости от уровня совместимости. В целом, следует выбирать последний уровень совместимости, поддерживаемых вашими серверами.

  **Последний уровень совместимости равно 1400** 
  
Уровень совместимости 1400 функциональные возможности включают:

*  Новая инфраструктура для импорта в табличной модели и подключение к данным с поддержкой TOM API-интерфейсы и скрипты TMSL. Это обеспечивает поддержку дополнительных данных источников, таких как хранилище больших двоичных объектов Azure. Дополнительные источники данных будут указывать включены в будущих обновлений.
*  Преобразование данных и данных возможности гибридного веб-приложения с помощью выражений получение данных и M.
*  Меры теперь поддерживает свойство строки подробностей выражение DAX, включение средств бизнес-Аналитики, таких как Microsoft Excel перехода на подробные данные из статистических отчета. Например при конечным пользователям просматривать общий объем продаж по региону и месяц, режиме связанного заказе. 
*  Безопасность на уровне объекта для имена таблиц и столбцов в дополнение к данным в них.
*  Расширенная поддержка для неоднородных иерархий.
*  Мониторинг производительности и улучшения.

  
## <a name="supported-compatibility-levels-by-version"></a>Поддерживаемые уровни совместимости версии
  
|||  
|-|-|- 
|**Уровень совместимости**|**Версия сервера**| 
|1400|Azure Analysis Services (Предварительная версия), SQL Server 2017 г. |  
|1200|Azure Analysis Services, SQL Server 2017 г., SQL Server 2016| 
|1103|SQL Server 2017 г *, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1|  
|1100|SQL Server 2017 г *, SQL Server 2016, SQL Server 2014, SQL Server 2012 SP1, SQL Server 2012| 

\*уровни совместимости 1100 и 1103 являются устаревшими в 2017 г. SQL Server.
  
## <a name="set-compatibility-level"></a>Уровень совместимости набор 
 При создании нового проекта табличной модели в SQL Server Data Tools (SSDT), можно указать уровень совместимости на **конструктор табличных моделей** диалогового окна. 
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.png)  
  
 При выборе **больше не показывать это сообщение** , во всех последующих проектах будет воспользоваться задан по умолчанию уровень совместимости. Уровень совместимости, используемый в SSDT по умолчанию, вы можете изменить в меню **Инструменты** > **Параметры**.  
  
 Чтобы обновить проект табличной модели в SSDT, задайте **уровень совместимости** свойства в модели **свойства** окна. Имейте в виду, обновление уровня совместимости является необратимым.
  
## <a name="check-compatibility-level-for-a-database-in-ssms"></a>Проверка уровня совместимости для базы данных в среде SSMS  
 В среде SSMS щелкните правой кнопкой мыши имя базы данных > **свойства** > **уровень совместимости**.  
  
## <a name="check-supported-compatibility-level-for-a-server-in-ssms"></a>Проверка поддерживаемого уровня совместимости для сервера в среде SSMS  
 В среде SSMS щелкните правой кнопкой мыши имя сервера и в контекстном меню выберите **Свойства** > **Поддерживаемый уровень совместимости**.  
  
 Это свойство указывает наивысший уровень совместимости базы данных, которая будет выполняться на сервере. Поддерживаемый уровень совместимости доступен только для чтения. Его нельзя изменить.  
  
## <a name="see-also"></a>См. также:  
 [Уровень совместимости многомерной базы данных](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Новые возможности служб Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Создание нового проекта табличной модели](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  
