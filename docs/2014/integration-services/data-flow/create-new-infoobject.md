---
title: Neues InfoObject erstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3587a633-1c0b-4d63-a22a-6b2b93923c3a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17e9b7508317abc2ceb3b6e273c46fdea5a5abb3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52781253"
---
# <a name="create-new-infoobject"></a>Neues InfoObject erstellen
  Verwenden Sie das Dialogfeld **Neues InfoObject erstellen** , um ein neues InfoObject im SAP NetWeaver BW-System zu erstellen.  
  
 Sie können das Dialogfeld **InfoObject erstellen** über die Seite **Verbindungs-Manager** im **Ziel-Editor für SAP BW**öffnen. Weitere Informationen zum SAP BW-Ziel finden Sie unter [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie das Dialogfeld "Neues InfoObject erstellen"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Verbindungs-Manager** , um die Seite **Verbindungs-Manager** des Editors zu öffnen.  
  
4.  Führen Sie auf der Seite **Verbindungs-Manager** im Gruppenfeld **SAP BW-Objekte erstellen** einen der folgenden Schritte aus, um ein InfoObject zu erstellen:  
  
    1.  Um ein InfoObject direkt zu erstellen, wählen Sie **InfoObject**aus, und klicken Sie dann auf **Erstellen** , um das Dialogfeld **Neues InfoObject erstellen** zu öffnen.  
  
    2.  Um ein InfoObject beim Erstellen eines InfoCube anzulegen, wählen Sie **InfoCube**aus und klicken dann auf **Erstellen**. Wählen Sie im Dialogfeld **InfoCube für Transaktionsdaten erstellen** in der Spalte **IObject** für eine der Zeilen in der Liste **Erstellen** aus, um das Dialogfeld **Neues InfoObject erstellen** zu öffnen.  
  
        > [!NOTE]  
        >  Jede Zeile in der Tabelle stellt eine Spalte im Datenfluss des Pakets dar.  
  
    3.  Um ein InfoObject zu erstellen, während eine InfoSouce für Transaktionsdaten erstellt wird, wählen Sie **InfoSource**aus und klicken dann auf **Erstellen**. Wählen Sie im Dialogfeld **InfoSource erstellen** die Option **Transaktionsdaten**aus, und klicken Sie dann auf **OK**. Wählen Sie im Dialogfeld **InfoSource für Transaktionsdaten erstellen** in der Spalte **IObject** für eine der Zeilen in der Liste **Erstellen** aus, um das Dialogfeld **Neues InfoObject erstellen** zu öffnen.  
  
        > [!NOTE]  
        >  Jede Zeile in der Tabelle stellt eine Spalte im Datenfluss des Pakets dar.  
  
    4.  Um ein InfoObject zu erstellen, während eine InfoSouce für Masterdaten erstellt wird, wählen Sie **InfoSource**aus und klicken dann auf **Erstellen**. Wählen Sie im Dialogfeld **InfoSource erstellen** die Option **Masterdaten**aus, und klicken Sie dann auf **OK**. Klicken Sie im Dialogfeld **InfoSource für Masterdaten erstellen** auf **Neu** , um das Dialogfeld **Neues InfoObject erstellen** zu öffnen.  
  
 Sie können das Dialogfeld **Neues InfoObject erstellen** auch öffnen, indem Sie im Abschnitt **Attribute** des Dialogfelds **Neues InfoObject erstellen** auf **Neu** klicken.  
  
## <a name="general-options"></a>Allgemeine Optionen  
 **Merkmal**  
 Erstellen Sie ein InfoObject, das die Dimensionsdaten darstellt.  
  
 **Kennzahl**  
 Erstellen Sie ein InfoObject, das die Faktendaten darstellt.  
  
 **InfoObject-Name**  
 Geben Sie einen Namen für das InfoObject ein.  
  
 **Kurze Beschreibung**  
 Geben Sie eine kurze Beschreibung für das InfoObject ein.  
  
 **Lange Beschreibung**  
 Geben Sie eine lange Beschreibung für das InfoObject ein.  
  
 **Verfügt über Masterdaten**  
 Geben Sie an, dass das InfoObject Masterdaten in Form von Attributen, Texten oder Hierarchien enthält.  
  
> [!NOTE]  
>  Wählen Sie diese Option aus, wenn das InfoObject Dimensionsdaten darstellt und Sie die Option **Merkmal** ausgewählt haben.  
  
 **Kleinbuchstaben zulassen**  
 Lassen Sie Kleinbuchstaben in den InfoObject-Daten zu.  
  
 **Speichern und aktivieren**  
 Speichern und aktivieren Sie das neue InfoObject.  
  
## <a name="data-type-options"></a>Optionen für "Datentyp"  
 **CHAR - Zeichenfolge**  
 Gibt an, dass das InfoObject Zeichendaten enthält.  
  
 **NUMC - Numerische Zeichenfolge**  
 Gibt an, dass das InfoObject numerische Daten enthält.  
  
 **DATS - Datum (JJJJMMTT)**  
 Gibt an, dass das InfoObject Datumsangaben enthält.  
  
 **TIMS - Zeit (HHMMSS)**  
 Gibt an, dass das InfoObject Uhrzeitdaten enthält.  
  
 **Länge**  
 Geben Sie die Länge der Daten ein.  
  
## <a name="text-options"></a>Optionen für "Text"  
 **Mit Texten**  
 Gibt an, dass das InfoObject Texte enthält.  
  
 **Kurzer Text**  
 Gibt an, dass das InfoObject kurze Texte enthält.  
  
 **Mittellanger Text**  
 Gibt an, dass das InfoObject mittellange Texte enthält.  
  
 **Langer Text**  
 Gibt an, dass das InfoObject lange Texte enthält.  
  
 **Sprachenabhängiger Text**  
 Gibt an, dass die Texte sprachabhängig sind.  
  
 **Zeitabhängiger Text**  
 Gibt an, dass die Texte zeitabhängig sind.  
  
## <a name="attributes-section"></a>Abschnitt "Attribute"  
 Der Abschnitt **Attribute** enthält eine Liste der Attribute für das InfoObject sowie die Optionen, mit denen Sie Listenattribute hinzufügen und entfernen können.  
  
### <a name="attributes-list"></a>Liste "Attribute"  
 Die Liste **Attribute** zeigt die Attribute des erstellten InfoObject an. Die Liste **Attribute** verfügt über die folgenden Spaltenüberschriften:  
  
 **InfoObject**  
 Zeigt den InfoObject-Namen an.  
  
 **Beschreibung**  
 Zeigt die InfoObject-Beschreibung an.  
  
 **InfoObject-Typ**  
 Zeigt den InfoObject-Typ an. In der folgenden Tabelle sind die möglichen Werte für den Typ aufgelistet.  
  
|Wert|Description|  
|-----------|-----------------|  
|CHA|Merkmale|  
|KYF|Kennzahlen|  
|UNI|Einheiten|  
|TIM|Zeitmerkmale|  
  
### <a name="attributes-options"></a>Optionen für "Attribute"  
 Verwenden Sie die folgenden Optionen, um Attribute für ein erstelltes InfoObject hinzuzufügen und zu entfernen:  
  
 **Hinzufügen**  
 Fügen Sie ein bestehendes InfoObject als Attribut hinzu.  
  
 Um ein vorhandenes InfoObject hinzuzufügen, klicken Sie auf Hinzufügen und verwenden dann das Dialogfeld **InfoObject suchen** für die Suche nach dem InfoObject. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up InfoObject](look-up-infoobject.md).  
  
 **Neu**  
 Fügt ein neues InfoObject als Attribut hinzu.  
  
 Um ein neues InfoObject zu erstellen und hinzuzufügen, klicken Sie auf Neu und verwenden dann eine neue Instanz des Dialogfelds **Neues InfoObject erstellen** , um das neue InfoObject zu erstellen.  
  
 **Entfernen**  
 Entfernt das ausgewählte InfoObject aus der Liste **Attribute** .  
  
## <a name="see-also"></a>Siehe auch  
 [InfoCube für Transaktionsdaten erstellen](create-infocube-for-transaction-data.md)   
 [InfoSource erstellen](create-infosource.md)   
 [InfoSource für Transaktionsdaten erstellen](create-infosource-for-transaction-data.md)   
 [InfoSource für Masterdaten erstellen](create-infosource-for-master-data.md)   
 [F1-Hilfe zu Microsoft Connector 1.1 für SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
