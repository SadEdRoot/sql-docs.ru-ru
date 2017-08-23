---
title: "С помощью репозиториев теста (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c3d2c6665c6d1852b291e69d2494343b5000ac06
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="using-test-repositories-oracletosql"></a>С помощью репозиториев теста (OracleToSQL)
Хранилище тестов SSMA хранилищ инженер-испытатель SSMA тестовые случаи и результаты теста для последующего использования. Репозиторий данных сохраняются в таблицах SQL Server **TestCaseRepository** и **RunTestCaseResultRepository** в схеме **ssma_oracle_utilities** из **ssmatesterdb** базы данных.  
  
В диалоговом окне репозитория тестовых случаев доступны следующие кнопки:  
  
-   Нажмите кнопку **обновление** кнопку, чтобы обновить список тестовых случаев или результатов тестов.  
  
-   Нажмите кнопку **закрыть** кнопку, чтобы закрыть диалоговое окно репозитория тестовых случаев.  
  
## <a name="test-cases-repository"></a>Репозиторий тестовых случаев  
Репозиторий тестовые случаи можно просмотреть, щелкнув **тестовые случаи...** из **тест-инженер** меню. Затем отображает SSMA **репозитория тестовых случаев** диалоговое окно со списком сохраненные тестовые случаи в **тестовых случаев** страницы.  
  
В сетке показаны следующие сведения о каждого тестового случая:  
  
-   Имя: Имя тестового случая.  
  
-   Создан: Тестовый случай Дата создания.  
  
-   Изменен: Тестовый случай Дата последнего изменения.  
  
-   Описание: Тестовый случай описания.  
  
На странице тестовых случаев доступны следующие кнопки:  
  
-   Нажмите кнопку **добавить** кнопку, чтобы запустить мастер тестовый случай и создать новый тест.  
  
-   Нажмите кнопку **удалить** кнопку, чтобы удалить выбранный тест из репозитория. При удалении тестового случая, также удаляются все связанные результаты тестов.  
  
-   Нажмите кнопку **изменить** кнопку, чтобы запустить мастер тестовый случай и изменить выбранного теста.  
  
-   Нажмите кнопку **запуска** кнопку, чтобы открыть [выполнение тестовых случаев (OracleToSQL)](http://msdn.microsoft.com/en-us/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02) диалоговое окно и выполнение выбранного теста.  
  
## <a name="test-results-repository"></a>Репозиторий результатов теста  
Репозиторий результатов теста можно просмотреть на **результаты теста** страница **репозитория тестовых случаев** окна. Открыть, щелкнув **результаты теста...** из **тест-инженер** меню.  
  
Можно использовать два фильтра на **результаты теста** страницы:  
  
-   Фильтр имя тестового случая: позволяет выбирать результаты тестов по имени тестового случая. Этот фильтр **всех тестовых случаев** значение позволяет отображение результатов теста для всех тестовых случаев.  
  
-   Фильтр даты выполнения тестового случая: фильтры результаты тестов по дате сохранения. Этот фильтр **все период** значение дает возможность отображения для любой даты для сохранения результатов теста.  
  
Следующие сведения о результатах теста отображается в сетке.  
  
-   Имя: имя тестового случая.  
  
-   Сохранен: Проверка даты вариантов для сохранения.  
  
-   Результаты: Краткое описание выполнения теста (эта ячейка всплывающая подсказка Сводка полного выполнения теста).  
  
На странице результатов тестирования доступны следующие кнопки:  
  
-   Нажмите кнопку **представление** кнопку, чтобы открыть [просмотра отчетов тестовый случай &#40; OracleToSQL &#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) текущего результата тестового случая.  
  
-   Нажмите кнопку **удалить** кнопку, чтобы удалить выбранный результат теста  
  
## <a name="see-also"></a>См. также:  
[Выполнение тестовых случаев &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Тестирование миграции объектов базы данных &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
