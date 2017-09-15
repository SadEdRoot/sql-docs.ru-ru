---
title: "sqlsrv_configure | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee3da7943b4bba95335de991e38d45b6261f96e3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvconfigure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Изменяет параметры обработки ошибок и ведения журнала.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>Параметры  
*$setting*: имя настраиваемого параметра. Список параметров приведен в таблице ниже.  
  
*$value*: значение, применяемое к настройке, указанной в параметре *$setting* . Возможные значения этого параметра зависят от указанной настройки. В следующей таблице перечислены возможные сочетания.  
  
|Настройка|Возможные значения параметра $value (целочисленный эквивалент в круглых скобках)|Значение по умолчанию|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|Неотрицательное число вплоть до предела памяти PHP.<br /><br />Нуль (0) означает отсутствие предела размера буфера.|10240|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF (0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF (0)|  
|WarningsReturnAsErrors<sup>3</sup>|**значение true,** (1) или **false** (0)|**значение true,** (1)|  
  
## <a name="return-value"></a>Возвращаемое значение  
Если **sqlsrv_configure** вызывается с неподдерживаемым параметром или значением, функция возвращает значение **false**. В противном случае функция возвращает значение **true**.  
  
## <a name="remarks"></a>Замечания  
(1) Дополнительные сведения о клиентских запросах см. в разделе [типы курсоров &#40; Драйвер SQLSRV &#41; ](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
(2) Дополнительные сведения о записи журнала см. в разделе [ведение](../../connect/php/logging-activity.md).  
  
(3) Дополнительные сведения о настройке обработки ошибок и предупреждений см. в разделе [как: Настройка обработки ошибок и предупреждений с помощью драйвера SQLSRV](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md).  
  
## <a name="see-also"></a>См. также:  
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md) 
  
