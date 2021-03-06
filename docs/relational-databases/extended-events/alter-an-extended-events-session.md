---
title: Изменение сеанса расширенных событий | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: xevents
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 614b322beaf2c8e9e7c818341983f58a6228debf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="alter-an-extended-events-session"></a>Изменение сеанса расширенных событий
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  После того как создан сеанс расширенных событий, его можно изменить необходимым образом с помощью **Мастера расширенных событий SQL Server**.  
  
## <a name="before-you-begin"></a>Перед началом работы  
 Нельзя изменять целевой объект для активных или неактивных сеансов, нельзя изменять настройки расширенных свойств для активного сеанса.  
  
 Можно вносить следующие изменения как в активные, так и в неактивные сеансы событий.  
  
-   Добавлять или удалять события, изменять настройки событий, например поля событий, фильтры и действия.  
  
-   Добавьте или удалите целевой объект из сеанса событий.  
  
-   Включите параметр **Запускать сеанс событий при запуске сервера** .  
  
 Можно вносить в неактивный сеанс событий следующие изменения.  
  
-   Включать параметр **Отслеживать связь между событиями** .  
  
-   Изменять конфигурацию расширенных свойств.  
  
> [!NOTE]  
>  В **мастере расширенных событий SQL Server** не поддерживается изменение сеансов событий.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Как изменить сеанс расширенных событий с помощью мастера расширенных событий SQL Server  
  
-   В обозревателе объектов откройте сервер, разверните **Управление**, **Планы обслуживания**и затем **Сеансы**.  
  
-   Щелкните правой кнопкой мыши сеанс, который нужно изменить, и выберите **Свойства**.  
  
-   В диалоговом окне **Свойства** внесите соответствующие изменения и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [ALTER EVENT SESSION (Transact-SQL)](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Создание сеанса расширенных событий с помощью редактора запросов](http://msdn.microsoft.com/library/cba0e02b-b201-4863-bf1b-9164e68e5fa8)  
  
  
