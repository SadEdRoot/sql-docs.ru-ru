---
title: С помощью функций R с данными SQL Server (R в быстрый запуск SQL Server) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 52b03b16c55b4ae8a772c2c12861fcc4b184d1f4
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585746"
---
# <a name="using-r-functions-with-sql-server-data-r-in-sql-quickstart"></a>С помощью функций R с данными SQL Server (R в быстрый запуск SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Теперь, когда вы знакомы с базовыми операциями, пришло время поработать с расширенными функциями R. Например, многие дополнительные статистические функции сложно реализовать с помощью T-SQL, а при использовании R для них требуется только одна строка кода.  Службы R упрощают внедрение служебных скриптов R в хранимую процедуру.

Используя приведенные здесь примеры, вы научитесь внедрять служебные и математические функции R в хранимую процедуру SQL Server.

## <a name="create-a-stored-procedure-to-generate-random-numbers"></a>Создание хранимой процедуры для формирования случайных чисел

Для простоты используем R `stats` пакет, который установлен и загружен по умолчанию со службами R Services. Он содержит сотню функций для общих статистических задач, в том числе функцию `rnorm`, которая формирует указанное количество случайных чисел с нормальным распределением при заданном среднем значении и стандартном отклонении.

Например, код R возвращает 100 чисел со средним значением 50 и стандартным отклонением 3.

```R
as.data.frame(rnorm(100, mean = 50, sd = 3));
```

Чтобы вызвать строку кода R из T-SQL, выполните процедуру sp_execute_external_script и добавьте функцию R в параметр скрипта R, как показано ниже.

```sql
EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(100, mean = 50, sd =3));'
    , @input_data_1 = N'   ;'
      WITH RESULT SETS (([Density] float NOT NULL));
```

Как упростить формирование другого набора случайных чисел?

Это просто в сочетании с SQL Server: определение хранимой процедуры, которая возвращает аргументы от пользователя. Затем передайте эти аргументы в скрипт R в виде переменных.

```sql
CREATE PROCEDURE MyRNorm (@param1 int, @param2 int, @param3 int)
AS
    EXEC sp_execute_external_script
      @language = N'R'
    , @script = N'
         OutputDataSet <- as.data.frame(rnorm(mynumbers, mymean, mysd));'
    , @input_data_1 = N'   ;'
    , @params = N' @mynumbers int, @mymean int, @mysd int'
    , @mynumbers = @param1
    , @mymean = @param2
    , @mysd = @param3
    WITH RESULT SETS (([Density] float NOT NULL));
```

+ В первой строке определяется каждый из входных параметров SQL, необходимых при выполнении хранимой процедуры.

+ Строка, начинающаяся с `@params`, определяет все переменные, используемые в коде R, и соответствующие типы данных SQL.

+ Следующие строки сопоставляют имена параметров SQL с соответствующими именами переменных R.

Теперь, когда функция R упакована в хранимой процедуре, вы можете легко вызвать функцию и передать различные значения, как показано ниже.

```sql
EXEC MyRNorm @param1 = 100,@param2 = 50, @param3 = 3
```

## <a name="use-r-utility-functions-for-troubleshooting"></a>Использование служебных функций R для устранения неполадок

По умолчанию включает установленного экземпляра R `utils` пакет, который предоставляет широкий набор служебных функций для изучения текущей среде R. Они могут оказаться полезными, если вы нашли несоответствия в выполнении кода R в SQL Server и внешних средах.

Например, можно использовать функцию R `memory.limit()`, чтобы получить память для текущей среды R. По умолчанию пакет `utils` устанавливается, но не загружается, поэтому сначала необходимо использовать функцию `library()`, чтобы его загрузить.

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N'
        library(utils);
        mymemory <- memory.limit();
        OutputDataSet <- as.data.frame(mymemory);'
    , @input_data_1 = N' ;'
WITH RESULT SETS (([Col1] int not null));
```

Многие пользователи предпочитают использовать системные функции синхронизации в R, например `system.time` и `proc.time`, для отслеживания времени, используемая процессами R и анализировать проблемы производительности.

Пример см. в руководстве [Занятие 3. Создание характеристик данных (пошаговое руководство по обработке и анализу данных)](../tutorials/walkthrough-create-data-features.md). В этом пошаговом руководстве функции времени R внедряются в решение, чтобы сравнить производительность двух методов для формирования признаков на основе данных: с помощью функций R и функций T-SQL.

## <a name="next-lesson"></a>Следующее занятие

Далее вы создадите модель прогнозирования с помощью R в SQL Server.

[Создание модели прогнозирования](../tutorials/rtsql-create-a-predictive-model-r.md)
