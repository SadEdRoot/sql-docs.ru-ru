---
title: Занятие 3. Добавление журналов с помощью служб SSIS | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: acea495a2496b6ee70d85b691fd8742cd6e16b56
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-3-add-logging-with-ssis"></a>Занятие 3. Добавление журналов с помощью служб SSIS
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] возможно ведение журналов, что позволяет отслеживать и устранять неполадки при выполнении пакетов, обеспечивая трассировку задач и событий контейнеров. Эти возможности очень гибки. Они могут активироваться как на уровне пакетов, так и на уровне отдельных задач или контейнеров в пакете. Можно выбрать события, которые будут заноситься в журнал, а также создать несколько журналов для одного пакета.  
  
Ведение журнала обеспечивается регистратором. Каждый регистратор может сохранять данные журналов в разных форматах и на разных типах носителей. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предоставляют следующие регистраторы:  
  
-   текстовый файл  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Журнал событий Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   XML-файл  
  
На этом занятии будет создана копия пакета, созданного на [занятии 2: добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md). При работе с новым пакетом будет добавлено и настроено ведение журнала, позволяющее отслеживать отдельные события при выполнении пакета. Если вы не выполняли ни одно из предыдущих занятий, можно воспользоваться копией пакета из занятия 2, которая включена в учебник.  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**, [Образцы продуктов службы Reporting Services на сайте CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
-   [Шаг 2. Добавление и настройка ведения журнала](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
-   [Шаг 3. Проверка учебного пакета, созданного на занятии 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 2](../integration-services/lesson-3-1-copying-the-lesson-2-package.md)  
  
  
  
