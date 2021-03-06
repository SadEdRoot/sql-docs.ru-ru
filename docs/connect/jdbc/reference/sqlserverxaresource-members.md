---
title: Элементы SQLServerXAResource | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a069bf2c-1b70-4817-b084-a508445de799
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36b5bc655f0ad54a8c326030aa123ef043920a13
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverxaresource-members"></a>Элементы SQLServerXAResource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Название|Описание|  
|----------|-----------------|  
|[SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)|Используется для разрешения тесно связанных транзакций XA, имеющих различные идентификаторы ветвей транзакции (XID), но одинаковые глобальные идентификаторы транзакции (GTRID).|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|javax.transaction.xa.XAResource|TMENDRSCAN, TMFAIL, TMJOIN, TMNOFLAGS, TMONEPHASE, TMRESUME, TMSTARTRSCAN, TMSUCCESS, TMSUSPEND, XA_OK, XA_RDONLY|  
  
## <a name="methods"></a>Методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Фиксация](../../../connect/jdbc/reference/commit-method-sqlserverxaresource.md)|Фиксирует глобальную транзакцию, указанный в заданном объекте Xid.|  
|[Конец](../../../connect/jdbc/reference/end-method-sqlserverxaresource.md)|Завершает работу, выполняемую от имени ветви транзакции.|  
|[Забыли](../../../connect/jdbc/reference/forget-method-sqlserverxaresource.md)|Удаляет в диспетчере ресурсов данные об эвристически выполненной ветви транзакции.|  
|[getTransactionTimeout](../../../connect/jdbc/reference/gettransactiontimeout-method-sqlserverxaresource.md)|Получает текущее значение времени ожидания транзакции задать для данного [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) объекта.|  
|[isSameRM](../../../connect/jdbc/reference/issamerm-method-sqlserverxaresource.md)|Определяет, является ли экземпляр диспетчера ресурсов, представленный целевой объект таким же, как экземпляр диспетчера ресурсов, представленных в заданном объекте XAResource.|  
|[Подготовка](../../../connect/jdbc/reference/prepare-method-sqlserverxaresource.md)|Запросы, в диспетчере ресурсов подготовку к фиксации транзакции, заданное в заданном объекте Xid.|  
|[восстановить](../../../connect/jdbc/reference/recover-method-sqlserverxaresource.md)|Получает список ветвей подготовленной транзакции от диспетчера ресурсов.|  
|[Откат](../../../connect/jdbc/reference/rollback-method-sqlserverxaresource.md)|Запрашивает в диспетчере ресурсов откат работы, выполненной от имени ветви транзакции.|  
|[setTransactionTimeout](../../../connect/jdbc/reference/settransactiontimeout-method-sqlserverxaresource.md)|Задает текущее значение времени ожидания транзакции для данного [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) объекта.|  
|[start](../../../connect/jdbc/reference/start-method-sqlserverxaresource.md)|Начинает работу от имени ветви транзакции, указанной в объекте Xid.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>См. также  
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
