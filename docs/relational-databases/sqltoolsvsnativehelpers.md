---
title: "SqlToolsVSNativeHelpers | Документация Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ea1f35f69b035b35ef789a4f61d02d8721c716c7
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sqltoolsvsnativehelpers"></a>SqlToolsVSNativeHelpers
  Библиотека, поддерживающая функциональность SQL Server в Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Логическое значение **True** , если точка входа библиотеки DLL инициализирована правильно; в противном случае — **False**.  
  
## <a name="see-also"></a>См. также:  
 [FrameWindowVisible](../relational-databases/sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  