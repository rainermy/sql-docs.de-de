---
title: 'Analysis Services Tutorial ergänzende Lektion: unregelmäßige Hierarchien | Microsoft-Dokumentation'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1aa9b8b0e456bb4f4aeff0a2a8e03d4938a46399
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074830"
---
# <a name="supplemental-lesson---ragged-hierarchies"></a>Ergänzende Lektion: unregelmäßige Hierarchien

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser ergänzenden Lektion beheben Sie ein häufiges Problem beim Pivotieren von Hierarchien, die leere Werte (Member) auf verschiedenen Ebenen enthalten. Beispielsweise muss eine Organisation, in dem eine hochrangigen Führungskraft sowohl Abteilungsleiter als auch ohne Führungskompetenzen unterstellt ist. Oder geografische Hierarchien bestehen Country-Region-Stadt, in denen einige Städte ein Bundesland / Kanton untergeordnet, z. B. Washington d. c., Vatikanstadt fehlt. Wenn eine Hierarchie leere Member aufweist, verzweigt es häufig zu anderen oder unregelmäßigen Ebenen.

![As-Lesson-Detail-ragged-hierarchies-Table](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-table.png)

Tabellarische Modelle mit Kompatibilitätsgrad 1400 verfügen über eine zusätzliche **Member ausblenden** -Eigenschaft für Hierarchien. Die **Standard** Einstellung wird vorausgesetzt, es sind keine leeren Mitglieder auf jeder Ebene. Die **leere Member ausblenden** Einstellung schließt leere Member aus der Hierarchie, wenn eine PivotTable oder ein Bericht hinzugefügt.  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **20 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In diesem Artikel ergänzende Lektion ist Teil einer Tutorials zur tabellenmodellierung. Vor dem Ausführen der Aufgaben in dieser ergänzenden Lektion an, Sie sollten abgeschlossen haben alle vorherige Lektionen oder über einen abgeschlossenen Adventure Works Internet Sales-Beispiel-Modellprojekt. 

Wenn Sie das AW Internet Sales-Projekt als Teil des Tutorials erstellt haben, Ihr Modell noch keine Daten oder Hierarchien, die unregelmäßig sind. Um diese ergänzende Lektion durchführen zu können, müssen Sie zuerst erstellen das Problem, indem einige weiteren Tabellen hinzufügen, Beziehungen, berechnete Spalten, ein Measure und eine neue Organisationshierarchie zu erstellen. Dies nimmt etwa 15 Minuten. Anschließend können Sie es in wenigen Minuten zu lösen.  

## <a name="add-tables-and-objects"></a>Hinzufügen von Tabellen und Objekte
  
### <a name="to-add-new-tables-to-your-model"></a>Auf dem Modell neue Tabellen hinzufügen
  
1.  Erweitern Sie im tabellarischen Modell-Explorer **Datenquellen**, die Verbindung per Rechtsklick > **neue Tabelle importieren**.
  
2.  Wählen Sie im Navigator **DimEmployee** und **FactResellerSales**, und klicken Sie dann auf **OK**.

3.  Klicken Sie im Abfrage-Editor **importieren**

4.  Erstellen Sie die folgende [Beziehungen](../tutorial-tabular-1400/as-lesson-4-create-relationships.md):

    | Tabelle 1           | Spalte       | Filterrichtung   | Tabelle 2     | Spalte      | Active |
    |-------------------|--------------|--------------------|-------------|-------------|--------|
    | FactResellerSales | OrderDateKey | Default            | DimDate     | date        | Benutzerkontensteuerung    |
    | FactResellerSales | DueDate      | Default            | DimDate     | date        | nein     |
    | FactResellerSales | ShipDateKey  | Default            | DimDate     | date        | nein     |
    | FactResellerSales | ProductKey   | Default            | DimProduct  | ProductKey  | Benutzerkontensteuerung    |
    | FactResellerSales | EmployeeKey  | Für beide Tabellen | "Dimemployee" | EmployeeKey | Benutzerkontensteuerung    |

5. In der **DimEmployee** Tabelle, erstellen Sie die folgende [berechnete Spalten](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md): 

    **Pfad** 
    ```
    =PATH([EmployeeKey],[ParentEmployeeKey])
    ```

    **"FullName"** 
    ```
    =[FirstName] & " " & [MiddleName] & " " & [LastName]
    ```

    **Level1** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],1,1)) 
    ```

    **Level2** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],2,1)) 
    ```

    **Level3** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],3,1)) 
    ```

    **"Level4"** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],4,1)) 
    ```

    **Ebene5** 
    ```
    =LOOKUPVALUE(DimEmployee[FullName],DimEmployee[EmployeeKey],PATHITEM([Path],5,1)) 
    ```

6.  In der **DimEmployee** Tabelle, erstellen Sie eine [Hierarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md) mit dem Namen **Organisation**. Fügen Sie die folgenden Spalten in dieser Reihenfolge hinzu: **Level1**, **Level2**, **Level3**, **"Level4"**, **ebene5**.

7.  In der **FactResellerSales** Tabelle, erstellen Sie die folgende [Measure](../tutorial-tabular-1400/as-lesson-6-create-measures.md):

    ```
    ResellerTotalSales:=SUM([SalesAmount])
    ```

8.  Verwendung [in Excel analysieren](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md) öffnen Sie Excel und erstellen Sie automatisch eine PivotTable.

9.  In **PivotTable Fields**, Hinzufügen der **Organisation** -Hierarchie aus der **DimEmployee** Tabelle **Zeilen**, und die  **ResellerTotalSales** measure aus der **FactResellerSales** Tabelle **Werte**.

    ![As-Lesson-Detail-ragged-hierarchies-PivotTable](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable.png)

    Wie Sie in der PivotTable sehen, zeigt die Hierarchie unregelmäßige Zeilen an. Es gibt viele Zeilen, in denen leere Member angezeigt werden.

## <a name="to-fix-the-ragged-hierarchy-by-setting-the-hide-members-property"></a>Unregelmäßige Hierarchien zu beheben, indem Sie Member ausblenden Eigenschaft festlegen.

1.  In **tabellarischer Modell-Explorer**, erweitern Sie **Tabellen** > **DimEmployee** > **Hierarchien**  >  **Organisation**.

2.  In **Eigenschaften** > **Member ausblenden**Option **leere Member ausblenden**. 

    ![As-Lesson-Detail-ragged-hierarchies-hidemembers](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-hidemembers.png)

3.  Aktualisieren Sie die PivotTable in Excel. 

    ![As-Lesson-Detail-ragged-hierarchies-PivotTable-Refresh](../tutorial-tabular-1400/media/as-lesson-detail-ragged-hierarchies-pivottable-refresh.png)

    Das sieht doch sehr viel besser!

## <a name="see-also"></a>Siehe auch   
[Lesson 9: Create hierarchies (Lektion 9: Erstellen von Hierarchien)](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)  
[Ergänzende Lektion – dynamische Sicherheit](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)  
[Ergänzende Lektion – Detailzeilen](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)  
