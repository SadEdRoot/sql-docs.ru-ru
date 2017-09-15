---
title: "Занятие 4: Добавление перенаправления потока ошибок с помощью служб SSIS | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cfe3634566a7ede28e3c1f5640cfe6e4caa1c351
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>Занятие 4. Добавление перенаправления потока ошибок с помощью служб SSIS
Для обработки ошибок, которые могут возникать в процессе преобразования, в службах [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] можно указать, как должны обрабатываться данные отдельных компонентов и столбцов, недоступные для преобразования. Можно проигнорировать ошибки в определенных столбцах, перенаправить всю строку с ошибкой или просто завершить работу компонента с ошибкой. По умолчанию для всех компонентов в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] указано завершение работы при возникновении ошибки. Завершение работы компонента с ошибкой, в свою очередь, приводит к сбою в работе пакета и остановке дальнейшей обработки.  
  
Рекомендуется вместо прекращения выполнения пакетов при возникновении ошибок обрабатывать потенциальные ошибки обработки при их возникновении в ходе преобразования. Хотя ошибки можно игнорировать, чтобы не прекращать выполнение пакета, зачастую лучше перенаправить строку с ошибкой по другому пути обработки, где данные вместе с ошибкой могут быть сохранены, а впоследствии проверены и повторно обработаны.  
  
На этом занятии предстоит создать копию пакета, разработанного на [занятии 3: добавление журнала](../integration-services/lesson-3-add-logging-with-ssis.md). При работе с этим новым пакетом будет создана поврежденная версия одного из файлов образцов данных. Повреждение файла приведет к возникновению ошибки обработки при выполнении пакета.  
  
Чтобы обработать данные об ошибке, будет добавлено и настроено назначение «Неструктурированный файл», которое будет записывать все строки, которым не удалось расположить в файле искомое значение преобразование «Уточняющий запрос ключа валюты».  
  
Прежде чем данные об ошибке будут записаны в файл, следует включить компонент скрипта, который использует скрипт для получения описания ошибки. Затем следует перенастроить преобразование «Уточняющий запрос ключа валюты» таким образом, чтобы перенаправлять все данные, обработка которых невозможна, в преобразование «Скрипт».  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**, [Образцы продуктов службы Reporting Services на сайте CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="tasks-in-lesson"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1: Копирование пакета занятия 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Шаг 2: Создание поврежденного файла](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Шаг 3: Добавление перенаправления потока ошибок](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Шаг 4: Добавление назначения «неструктурированный файл»](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Шаг 5: Проверка учебного пакета занятия 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1: Копирование пакета занятия 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
