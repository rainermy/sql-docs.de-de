---
title: Hinzufügen vorhandener Elemente zu einem Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 084b3879-e96b-45a7-b421-6a4b0db2b92b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: db4a09177a9af1afa73fadfbf585f5b9e0f0b8ab
ms.sourcegitcommit: e3f5b70bbb4c66294df8c7b2c70186bdf2365af9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397519"
---
# <a name="add-existing-items-to-a-project"></a>Hinzufügen vorhandener Elemente zu einem Projekt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sie können neue Elemente zu einem Projekt hinzufügen, um die Funktionalität der Anwendung zu erweitern. Bei einem vorhandenen Element kann es sich um eine Abfrage oder eine beliebige Datei handeln. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] hat zwei Projekttypen: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Skriptprojekt und Analysis Services-Skriptprojekt. Der Projekttyp bestimmt die Abfragedateien, die Sie zu einem Projekt hinzufügen können. So können Sie beispielsweise eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage (eine Datei mit einer SQL-Erweiterung) zu einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Skriptprojekt hinzufügen, nicht jedoch zu einem Analysis Services-Skriptprojekt. Informationen zum Zuordnen weiterer Dateierweiterungen zu einem Projekttyp finden Sie unter [ Zuordnen von Dateierweiterungen zu einem Code-Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
### <a name="to-add-an-existing-query-or-a-miscellaneous-file-to-a-project"></a>So fügen Sie eine vorhandene Abfrage oder eine beliebige Datei zu einem Projekt hinzu  
  
1.  Wählen Sie im Projektmappen-Explorer ein Zielprojekt aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**.  
  
    **Look in**  
    Suchen Sie in der Liste nach den Dateien oder Ordnern, die dem Projekt hinzugefügt werden sollen. Die Dateien von XML-Webdiensten und ASP.NET-Webanwendungen sind auf dem Webserver gespeichert.  
  
    **Desktop**  
    Zeigt die Dateien und Ordner auf dem Desktop an.  
  
    **Eigene Projekte**  
    Zeigt die Dateien und Ordner im Standardverzeichnis **Eigene Projekte** an.  
  
    **Arbeitsplatz**  
    Zeigt den Inhalt des Ordners **Arbeitsplatz** an.  
  
    **Dateiname**  
    Mithilfe dieser Option können Sie die anzuzeigenden Dateien oder Ordner filtern. Geben Sie den Dateinamen, nach dem gefiltert werden soll, vollständig oder teilweise ein. Als Platzhalter können Sie das Sternchen (`*`) verwenden.  
  
    > [!NOTE]  
    > Navigieren Sie zu dem gewünschten Speicherort im Web oder Netzwerk, indem Sie die URL oder Netzwerkpfad in das Feld **Dateiname** eingeben. Beispielsweise werden mit **`https://mywebsite`** alle Dateien angezeigt, die unter der Webadresse „mywebsite“ verfügbar sind, während mit **\\\myserver\myshare** alle Dateien aufgeführt werden, die im Ordner „myshare“ des Servers „myserver“ gespeichert sind.  
  
    **Dateityp**  
    Mithilfe dieser Option können Sie Dateien nach der Dateierweiterung filtern. Jedes Produkt listet Standardfilter für die am häufigsten verwendeten Dateitypen auf.  
  
    **Hinzufügen**  
    Mithilfe dieser Dropdown-Schaltfläche können Sie dem Projekt das Objekt hinzufügen und das Objekt mit dem entsprechenden Standard-Editor öffnen.  
  
    -   **Hinzufügen**  
  
        Kopiert ein vorhandenes Objekt in den Projektordner auf dem Datenträger und fügt das Objekt dem ausgewählten Projekt im Projektmappen-Explorer hinzu. Die an diesem Objekt vorgenommenen Änderungen haben keine Auswirkungen auf das Objekt am ursprünglichen Speicherort. Dies ist der Standardeditor für diesen Dateityp.  
  
    -   **Als Link hinzufügen**  
  
        Fügt dem Projekt die ausgewählte Datei hinzu und öffnet sie mit dem Standard-Editor für den Dateityp. Mit dieser Option wird die ursprünglich ausgewählte Datei geöffnet. Die Datei wird nicht in den Projektordner kopiert.  
  
3.  Beim Hinzufügen von Abfragedateien werden Sie im Verbindungsdialogfeld aufgefordert, eine Verbindung für die Abfrage anzugeben. Wenn Sie der Abfrage keine Verbindung zuordnen möchten, klicken Sie im Verbindungsdialogfeld auf **Abbrechen** .  
  
4.  Die Datei wird dem Ordner **Abfragen** oder **Sonstige Dateien** des Projekts hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Projektmappen-Explorer](../../ssms/solution/solution-explorer.md)  
[Hinzufügen neuer Elemente zu einem Projekt](../../ssms/solution/add-new-items-to-a-project.md)  
[Entfernen oder Löschen eines Elements oder Projekts](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
