---
title: 'Erstellen von R-Modelle RevoScaleR-Tutorial: SQL Server-Machine Learning'
description: Exemplarische Vorgehensweise im Lernprogramm zum Erstellen ein Modells mit der Sprache R auf SQL Server bereit.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 88e2dd9e50ca79136e4082cab30bba4a0e961531
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645069"
---
# <a name="create-r-models-sql-server-and-revoscaler-tutorial"></a>Erstellen von R-Modellen (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Nun, da Sie die Trainingsdaten erweitert haben, ist es Zeit für die regressionsmodellierung mit Daten zu analysieren. Lineare Modelle sind ein wichtiges Tool in der Welt von Vorhersageanalysen und **RevoScaleR** Paket enthält die regressionsalgorithmen, die die arbeitsauslastung zu unterteilen und parallel ausführen können.

> [!div class="checklist"]
> * Erstellen eines linearen Regressionsmodells
> * Erstellen eines logistischen Regressionsmodells

## <a name="create-a-linear-regression-model"></a>Erstellen eines linearen Regressionsmodells

In diesem Schritt erstellen Sie ein einfaches Lineares Modell, das die Kunden, die mithilfe der unabhängigen Variablen die Werte in die Kreditkartenschulden schätzt die *Geschlecht* und *CreditLine* Spalten.
  
Verwenden Sie hierzu die [RxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) -Funktion, die remotecomputekontexte unterstützt.
  
1. Erstellen Sie eine R-Variable zum Speichern von das abgeschlossene Modell, und rufen **RxLinMod**, eine geeignete Formel zu übergeben.
  
    ```R
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)
    ```
  
2. Um eine Zusammenfassung der Ergebnisse anzuzeigen, rufen Sie die R-Standardfunktion **Zusammenfassung** für das Modellobjekt.
  
     ```R
     summary(linModObj)
     ```

Es mag Ihnen seltsam erscheinen, dass eine einfache R-Funktion wie **summary** hier funktioniert, da Sie im vorherigen Schritt den Server als Computekontext festgelegt haben. Auch wenn die Funktion **rxLinMod** den Remotecomputekontext zum Erstellen des Modells verwendet, gibt sie auch ein Objekt zurück, das das Modell für Ihre lokale Arbeitsstation enthält und es im freigegebenen Verzeichnis speichert.

Daher können Sie R-Standardbefehle für das Modell ausführen, als ob es mithilfe des „lokalen“ Kontexts erstellt wurde.

**Ergebnisse**

```R
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
Signif. codes: 0  0.001  0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 3812 on 9997 degrees of freedom
Multiple R-squared: 0.05765
Adjusted R-squared: 0.05746
F-statistic: 305.8 on 2 and 9997 DF, p-value: < 2.2e-16
Condition number: 1.0184
```

## <a name="create-a-logistic-regression-model"></a>Erstellen eines logistischen Regressionsmodells

Als Nächstes erstellen Sie ein Logistisches Regressionsmodell, das angibt, ob ein bestimmter Kunde ein Betrugs-Risiko ist. Verwenden Sie die **RevoScaleR** [RxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) -Funktion, die Anpassung der logistischen regressionsmodelle in remotecomputekontexten unterstützt.

Lassen Sie den Computekontext wie er ist. Sie werden auch weiterhin auch die gleiche Datenquelle verwenden.

1. Rufen Sie die Funktion **rxLogit** auf, und übergeben Sie die Formel, die zum Definieren des Modells erforderlich ist.

    ```R
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS, dropFirst = TRUE)
    ```
  
    Da es ein großes Modell mit 60 unabhängigen Variablen ist, einschließlich der drei Dummy-Variablen, die gelöscht werden, müssen Sie möglicherweise ein paar Minuten warten, bis der Computekontext das Objekt zurückgibt.
    
    Der Grund für die Größe des Modells ist, dass in R und im **RevoScaleR** -Paket alle Ebenen einer kategorischen Faktor-Variable automatisch als separate Dummyvariablen behandelt werden.
  
2. Rufen Sie die **summary** -Funktion von R auf, um eine Zusammenfassung des zurückgegebenen Modells anzuzeigen.
  
    ```R
    summary(logitObj)
    ```
  
**Teilergebnisse**

```R
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

Signif. codes:  0 '\*\*\*' 0.001 '\*\*' 0.01 '\*' 0.05 '.' 0.1 ' ' 1
Condition number of final variance-covariance matrix: 3997.308
Number of iterations: 15
```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Auswertung neuer Daten](../../advanced-analytics/tutorials/deepdive-score-new-data.md)