---
title: Создание моделей R (SQL и R глубокое погружение) | Документы Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a2f6e9b23e1592073c1b21bc41e4975ffaf17075
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-r-models-sql-and-r-deep-dive"></a>Создание моделей R (SQL и R глубокое погружение)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье является частью учебника по глубокое погружение обработки и анализа данных, о том, как использовать [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) с SQL Server.

Теперь, когда вы расширили данные обучения, пора проанализировать их с помощью линейной регрессии. Линейные модели — важный инструмент в области прогнозирующего анализа, и пакет **RevoScaleR** в службах [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] содержит масштабируемый алгоритм с высокой производительностью.

## <a name="create-a-linear-regression-model"></a>создание модели линейной регрессии;

На этом шаге создания простой линейной модели, которая оценивает баланс кредитной карты для клиентов, используя как независимые переменные значения в *Пол* и *creditLine* столбцы.
  
Чтобы сделать это, используйте [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) функции, которая поддерживает контекстах удаленных вычислений.
  
1. Создайте переменную R для хранения завершенный модель и вызвать метод **rxLinMod**, передавая соответствующие формулы.
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. Чтобы просмотреть сводку результатов, вызовите стандартный R `summary` функции объекта модели.
  
     ```R
     summary(linModObj)
     ```

Может показаться необычные plain функцию R, такие как `summary` будет работать, поскольку на предыдущем шаге был переключен контекст вычислений на сервер. Однако даже если функция **rxLinMod** использует контекст удаленных вычислений для создания модели, она также возвращает объект, который содержит модель для локальной рабочей станции, и сохраняет его в общем каталоге.

Таким образом, для модели можно выполнять стандартные команды R, как если бы она была создана с помощью контекста local.

**Результаты**

```
Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): balance
Total independent variables: 4 (Including number dropped: 1)
Number of valid observations: 10000
Number of missing observations: 0
Coefficients: (1 not defined because of singularities)

Estimate Std. Error t value Pr(>|t|) (Intercept)
3253.575 71.194 45.700 2.22e-16
gender=Male -88.813 78.360 -1.133 0.257
gender=Female Dropped Dropped Dropped Dropped
creditLine 95.379 3.862 24.694 2.22e-16
Signif. codes: 0  0.001  0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>создание модели логистической регрессии;

Создайте модель логистической регрессии, который указывает, является ли конкретный заказчик риск мошенничества. Вы воспользуетесь **RevoScaleR** [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) функции, какие подгонки поддерживает моделей логистической регрессии в удаленных контекстов вычислений.

1.  Не меняйте контекст вычисления. Кроме того, по-прежнему будет использоваться тот же источник данных.

2.  Вызовите функцию **rxLogit** и передайте формулу, необходимую для определения модели.

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    Так как это большая модель, содержащая 60 независимых переменных, в том числе три фиктивные переменные, которые удаляются, возможно, придется подождать некоторое время, пока контекст вычислений вернет объект.
    
    Причина такого большого размера модели в том, что в языке R (и в пакете **RevoScaleR** ) каждый уровень категориальной факторной переменной автоматически обрабатывается как отдельная фиктивная переменная.
  
3.  Чтобы просмотреть сводные данные, возвращенные модели, вызовите R `summary` функции.
  
    ```R
    summary(logitObj)
    ```
  
**Частичные результаты**

```
Logistic Regression Results for: fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Dependent variable(s): fraudRisk
Total independent variables: 60 (Including number dropped: 3)
Number of valid observations: 10000 -2

LogLikelihood: 2032.8699 (Residual deviance on 9943 degrees of freedom)

Coefficients:
Estimate Std. Error z value Pr(>|z|)     (Intercept)
-8.627e+00  1.319e+00  -6.538 6.22e-11
state=AK                Dropped    Dropped Dropped  Dropped
state=AL             -1.043e+00  1.383e+00  -0.754   0.4511

(other states omitted)

gender=Male             Dropped    Dropped Dropped  Dropped
gender=Female         7.226e-01  1.217e-01   5.936 2.92e-09
cardholder=Principal    Dropped    Dropped Dropped  Dropped
cardholder=Secondary  5.635e-01  3.403e-01   1.656   0.0977
balance               3.962e-04  1.564e-05  25.335 2.22e-16
numTrans              4.950e-02  2.202e-03  22.477 2.22e-16
numIntlTrans          3.414e-02  5.318e-03   6.420 1.36e-10
creditLine            1.042e-01  4.705e-03  22.153 2.22e-16

Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-step"></a>Следующий шаг

[Оценка новых данных](../../advanced-analytics/tutorials/deepdive-score-new-data.md)

## <a name="previous-step"></a>Предыдущий шаг

[Визуализация данных SQL Server с помощью языка R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)
