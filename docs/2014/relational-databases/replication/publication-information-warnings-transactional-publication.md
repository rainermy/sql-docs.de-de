---
title: Veröffentlichungsinformationen, Warnungen (Transaktionsveröffentlichung, SqlServer 2005 und höher) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.tran.f1
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2ab1c4be29b87e1051daa702ce40905a95e34ab
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132700"
---
# <a name="publication-information-warnings-transactional-publication-sql-server-2005-and-later"></a>Veröffentlichungsinformationen, Warnungen (Transaktionsveröffentlichung, SQL Server 2005 und höher)
  Die Registerkarte **Warnungen** ist für Verteiler verfügbar, auf denen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen ausgeführt werden. Auf der Registerkarte **Warnungen** können Sie folgende Tasks für die ausgewählte Veröffentlichung ausführen:  
  
-   Aktivieren von Warnungen, die im Replikationsmonitor angezeigt werden.  
  
-   Angeben von Schwellenwerten, die den Warnungen zugeordnet werden.  
  
-   Festlegen von Hinweisen, die den Warnungen zugeordnet werden.  
  
## <a name="warnings-thresholds-and-alerts"></a>Warnungen, Schwellenwerte und Warnhinweise  
 Standardmäßig werden vom Replikationsmonitor Warnungen zu nicht initialisierten Abonnements angezeigt: auf den Seiten mit den Abonnementinformationen wird in der Spalte **Status** - der Status **Nicht initialisiertes Abonnement** als Warnung angezeigt. Sie können angeben, ob durch folgende zusätzlichen Bedingungen bei Transaktionsveröffentlichungen eine Warnung ausgelöst wird:  
  
-   Bevorstehender Abonnementablauf.  
  
     Diese Bedingung entspricht der Option **Warnung, wenn ein Abonnement innerhalb des Schwellenwerts abläuft**. Wenn der angegebene Schwellenwert erreicht oder überschritten wird, wird als Abonnementstatus **Läuft demnächst ab/Abgelaufen** angezeigt (wenn kein Problem mit einer höheren Priorität angezeigt werden muss).  
  
-   Überschreiten der angegebenen Latenzzeit. Dabei handelt es sich um die Zeit zwischen dem Ausführen eines Commits für eine Transaktion beim Verleger und der entsprechenden Ausführung des Commits für die Transaktion beim Abonnenten.  
  
     Diese Bedingung entspricht der Option **Warnung, wenn die Latenzzeit den Schwellenwert überschreitet**. Wenn der angegebene Schwellenwert erreicht oder überschritten wird, wird als Abonnementstatus **Leistungskritisch** angezeigt (falls kein Problem mit einer höheren Priorität angezeigt werden muss). Mit den Schwellenwerten wird gleichzeitig eine Leistungsbewertung bereitgestellt, die in der **Leistung** -Spalte auf den Seiten mit den Abonnementinformationen angezeigt wird. Die folgenden Werte sind für die Leistungsbewertung möglich:  
  
    -   Hervorragend  
  
    -   Gut  
  
    -   Durchschnittlich  
  
    -   Schlecht  
  
    -   Kritisch  
  
 Wenn Sie eine Warnung aktivieren, müssen Sie auch einen Schwellenwert festlegen. Wenn Sie z. B. die Warnung **Warnung, wenn die Latenzzeit den Schwellenwert überschreitet**aktivieren, müssen Sie die Zeitspanne auswählen, die zwischen dem Ausführen eines Commits für eine Transaktion beim Verleger und der entsprechenden Ausführung des Commits für die Transaktion beim Abonnenten liegt.  
  
 Neben der Warnung im Replikationsmonitor kann bei Erreichen eines Schwellenwerts auch ein Warnhinweis ausgelöst werden. Zum Definieren eines Warnhinweises klicken Sie auf **Warnungen konfigurieren** , und stellen Sie im Dialogfeld **Replikationswarnungen konfigurieren** die entsprechenden Informationen bereit.  
  
## <a name="options"></a>Optionen  
 **Aktiviert**  
 Wählen Sie diese Option aus, um eine Warnung zu aktivieren und einen Schwellenwert anzugeben.  
  
 **Warnung**  
 Eine Beschreibung der Warnung, die einem Schwellenwert zugeordnet ist.  
  
 **Schwellenwert**  
 Geben Sie einen Wert für den Schwellenwert an.  
  
 **Warnungen konfigurieren**  
 Wählen Sie im Raster **Warnungen** die gewünschte Zeile aus, und klicken Sie auf **Warnungen konfigurieren** , um das Dialogfeld **Replikationswarnungen konfigurieren** zu öffnen. In dem Dialogfeld können Sie einen Warnhinweis definieren, der dem ausgewählten Schwellenwert und der Warnung zugeordnet wird.  
  
 **Änderungen verwerfen**  
 Klicken Sie hier, um die Änderungen an Warnungen und Schwellenwerten zu verwerfen.  
  
> [!NOTE]  
>  Die Schaltfläche **Änderungen verwerfen** hat keine Auswirkungen auf die im Dialogfeld **Replikationswarnungen konfigurieren** definierten Warnungen.  
  
 **Änderungen speichern**  
 Klicken Sie hier, um die Änderungen an Warnungen und Schwellenwerten zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [Anzeigen von Informationen und Ausführen von Aufgaben mithilfe des Replikationsmonitors](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Leistung mit dem Replikationsmonitor](monitor/monitor-performance-with-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)   
 [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
