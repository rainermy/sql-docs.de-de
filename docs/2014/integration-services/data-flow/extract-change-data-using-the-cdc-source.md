---
title: Extrahieren von Änderungsdaten mithilfe der CDC-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 604fbafb-15fa-4d11-8487-77d7b626eed8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a96c531302c92e61e2a2e0b9feb875d0a1097c43
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805192"
---
# <a name="extract-change-data-using-the-cdc-source"></a>Extrahieren von Änderungsdaten mithilfe der CDC-Quelle
  Das Paket muss bereits mindestens einen Datenflusstask und einen CDC-Steuerungstask enthalten, damit Sie eine CDC-Quelle hinzufügen und konfigurieren können.  
  
 Weitere Informationen zum CDC-Steuerungstask finden Sie unter [CDC Control Task](../control-flow/cdc-control-task.md).  
  
 Weitere Informationen zur CDC-Quelle finden Sie unter [CDC Source](cdc-source.md).  
  
### <a name="to-extract-change-data-using-a-cdc-source"></a>So extrahieren Sie Änderungsdaten mithilfe einer CDC-Quelle  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie die CDC-Quelle dann aus der **Toolbox**auf die Entwurfsoberfläche.  
  
4.  Doppelklicken Sie auf die CDC-Quelle.  
  
5.  Wählen Sie im Dialogfeld **Quellen-Editor für CDC** auf der Seite **Verbindungs-Manager** in der Liste einen vorhandenen ADO.NET-Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um eine neue Verbindung zu erstellen. Die Verbindung sollte zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank hergestellt werden, die die zu lesenden Änderungstabellen enthält.  
  
6.  Wählen Sie die **CDC-Tabelle** aus, in der Sie Änderungen verarbeiten möchten.  
  
7.  Wählen Sie den Namen der **CDC-Aufzeichnungsinstanz** mit der zu lesenden CDC-Tabelle aus, oder geben Sie ihn ein.  
  
     Eine aufgezeichnete Quelltabelle kann über eine oder zwei aufgezeichnete Instanzen zum Behandeln des nahtlosen Übergangs der Tabellendefinition mithilfe von Schemaänderungen verfügen. Wenn mehr als eine Aufzeichnungsinstanz für die aufzuzeichnende Quelltabelle definiert wird, müssen Sie hier die gewünschte Aufzeichnungsinstanz auswählen. Der Standardname einer Aufzeichnungsinstanz für eine Tabelle [Schema].[Tabelle] lautet \<Schema>_\<Tabelle>. Die tatsächlich verwendeten Namen der Aufzeichnungsinstanzen können jedoch abweichen. Die tatsächliche Tabelle, aus der gelesen wird, ist die CDC-Tabelle **cdc.\<Aufzeichnungsinstanz>_CT**.  
  
8.  Wählen Sie den Verarbeitungsmodus aus, der sich für die Behandlung Ihrer Verarbeitungsanforderungen am besten eignet. Folgende Optionen sind möglich:  
  
    -   **alle**: Gibt die Änderungen zurück in den aktuellen CDC-Bereich, ohne die **vor Update** Werte.  
  
    -   **Alle mit den alten Werten**: Gibt die Änderungen im aktuellen CDC-Verarbeitungsbereich Einbeziehung der alten Werte (**vor Update**). Für jeden Updatevorgang gibt es zwei Zeilen, eine mit den Werten vor dem Update und eine mit den Werten nach dem Update.  
  
    -   **NET**: Gibt nur eine Änderungszeile pro Quellzeile, die im aktuellen CDC-Verarbeitungsbereich geändert. Wenn eine Quellzeile mehrmals aktualisiert wurde, wird die kombinierte Änderung erzeugt (Beispiel: Einfügen+Update wird als einzelner Updatevorgang und Update+Löschen als einzelner Löschvorgang erzeugt). Beim Arbeiten im Änderungsverarbeitungsmodus Net ist es möglich, die Änderungen auf Lösch-, Einfüge- und Updatevorgänge aufzuteilen und parallel zu behandeln, da die einzelne Quellzeile in mehr als einer Ausgabe vorhanden ist.  
  
    -   **NET mit updatemaske**: Dieser Modus ähnelt dem normalen Net-Modus, jedoch werden außerdem boolesche Spalten mit dem Namensmuster hinzugefügt **__ $\<Spaltenname >\__Changed** , die auf geänderte Spalten in der aktuellen Änderungszeile.  
  
    -   **NET mit Merge**: Dieser Modus ähnelt dem normalen Net-Modus aber Hierbei sind Einfüge-und Updatevorgänge zu einem einzelnen Mergevorgang (UPSERT) zusammengeführt.  
  
9. Wählen Sie die SSIS-Zeichenfolgenpaketvariable aus, in der der CDC-Status für den aktuellen CDC-Kontext verwaltet wird. Weitere Informationen zur CDC-Statusvariablen finden Sie unter [Definieren einer Statusvariablen](define-a-state-variable.md).  
  
10. Aktivieren Sie das Kontrollkästchen **reprocessing-Indikatorspalte einschließen** , um eine spezielle Ausgabespalte mit dem Namen **__$reprocessing**zu erstellen. Diese Spalte hat den Wert **TRUE** , wenn sich der CDC-Verarbeitungsbereich mit dem ursprünglichen Verarbeitungsbereich überschneidet (der LSN-Bereich, der dem Zeitraum des erstmaligen Ladens entspricht) oder wenn ein CDC-Verarbeitungsbereich nach einem Fehler bei einer vorherigen Ausführung erneut verarbeitet wird. In dieser Indikatorspalte können SSIS-Entwickler Fehler unterschiedlich behandeln, wenn sie Änderungen erneut verarbeiten (z. B. können Aktionen, wie das Löschen einer nicht vorhandenen Zeile und ein fehlgeschlagener Einfügevorgang aufgrund eines doppelten Schlüssels, ignoriert werden).  
  
     Weitere Informationen finden Sie unter [CDC Source Custom Properties](cdc-source-custom-properties.md).  
  
11. Um die Zuordnung zwischen externen Spalten und Ausgabespalten zu aktualisieren, klicken Sie auf **Spalten** und wählen in der Liste **Externe Spalte** verschiedene Spalten aus.  
  
12. Aktualisieren Sie optional die Werte der Ausgabespalten, indem Sie Werte in der Liste **Ausgabespalte** löschen.  
  
13. Klicken Sie auf **Fehlerausgabe**, um die Fehlerausgabe zu konfigurieren.  
  
14. Sie können auf **Vorschau** klicken, um bis zu 200 Datenzeilen anzuzeigen, die von der CDC-Quelle extrahiert werden.  
  
15. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für CDC &#40;Seite „Verbindungs-Manager“&#41;](../cdc-source-editor-connection-manager-page.md)   
 [Quellen-Editor für CDC &#40;Seite „Spalten“&#41;](../cdc-source-editor-columns-page.md)   
 [Quellen-Editor für CDC &#40;Seite „Fehlerausgabe“&#41;](../cdc-source-editor-error-output-page.md)  
  
  
