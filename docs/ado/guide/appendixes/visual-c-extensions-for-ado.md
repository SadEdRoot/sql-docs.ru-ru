---
title: Расширения Visual C++ для ADO | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO], VC++ extensions for ADO
ms.assetid: 2952ece0-7217-4448-bb09-f6b64f43b7e2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d27cc7776c59364ebc0b69c4872dc8b78ee51116
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="visual-c-extensions"></a>Расширения Visual C++
Предпочтительным способом программирования ADO в Visual C++ использует **#import** директивы, как описано в [Microsoft Visual C++ ADO программирования](../../../ado/guide/appendixes/visual-c-ado-programming.md). Тем не менее, более ранних версиях ADO, поставляемых с альтернативным способом программирования, с помощью Visual C++: расширения Visual C++. В данном разделе описываются эту функцию для тех, кто должен поддерживать код расширения Visual C++, но новый код ADO должны быть написаны с помощью #**импорта**.

 Одно из наиболее трудоемкой заданий Visual C++ программисты лицевой стороны при извлечении данных с помощью ADO выполняет преобразование данных возвращаются как тип данных VARIANT к типу данных, C++ и последующее сохранение преобразованные данные в классе или структуре. Помимо громоздким, получение данных C++ с помощью типа данных VARIANT снижает производительность.

 ADO предоставляет интерфейс, который поддерживает получение данных в собственные типы данных C/C++, минуя типа VARIANT, а также макросы препроцессора, которые упрощают использование интерфейса. Результатом является гибкий инструмент, который проще в использовании и имеет высокую производительность.

 Типичный сценарий клиента C/C++ является привязка записи в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) C/C++ структура или класс, содержащий собственные типы C/C++. При работе через вариантов, это требует написания кода преобразования из типа VARIANT для собственных типов C/C++. Поэтому данную ситуацию намного проще для программистов Visual C++ предназначены для ADO расширения Visual C++.

 Дополнительные сведения о расширениях Visual C++ для ADO с в следующих разделах.

-   [С помощью расширений Visual C++ для ADO](../../../ado/guide/appendixes/using-visual-c-extensions.md)

-   [Заголовок расширений Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)

-   [ADO с примером расширения Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md)

## <a name="see-also"></a>См. также
 [ADO для индекса синтаксис Visual C++ для модели COM](../../../ado/reference/ado-api/ado-for-visual-c-syntax-index-for-com.md) [пример расширения Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [использование расширений Visual C++](../../../ado/guide/appendixes/using-visual-c-extensions.md) [заголовок расширений Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)
