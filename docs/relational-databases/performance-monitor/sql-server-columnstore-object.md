---
title: SQL Server, Columnstore-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: dc21bd2fa9d3c35d436679cf256bec81654f5747
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380511"
---
# <a name="sql-server-columnstore-object"></a>SQL Server, Columnstore-Objekt
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Das **SQLServer:Columnstore**-Objekt bietet Leistungsindikatoren zum Überwachen der Ausführung des Columnstore-Index in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Die folgende Tabelle beschreibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Columnstore** counters.  
  
|Columnstore-Leistungsindikatoren|und Beschreibung|  
|--------------------------|-----------------|  
|**Geschlossene Delta-Zeilengruppen**|Die Anzahl von geschlossenen Delta-Zeilengruppen.|  
|**Komprimierte Delta-Zeilengruppen**|Die Anzahl von komprimierten Delta-Zeilengruppen.|  
|**Erstellte Delta-Zeilengruppen**|Die Anzahl von erstellten Delta-Zeilengruppen.|  
|**Segmentcache-Trefferquote**|Der Prozentsatz der Spaltensegmente, die im Columnstore-Pool gefunden wurden, ohne dass ein Lesevorgang vom Datenträger erforderlich war.|  
|**Basis für Segmentcache-Trefferquote**|Nur zur internen Verwendung.|
|**Segmentlesevorgänge/Sek.**|Die Anzahl von ausgegebenen physischen Segmentlesevorgängen.|  
|**Migrierte Löschpuffer gesamt**|Die Anzahl von Bereinigungen des Löschpuffers durch den Tupelverschiebungsvorgang.|  
|**Auswertungen der Zusammenführungsrichtlinie gesamt**|Die Anzahl von Auswertungen der Zusammenführungsrichtlinie für den Columnstore.|  
|**Komprimierte Zeilengruppen gesamt**|Die Gesamtzahl von komprimierten Zeilengruppen.|  
|**Zeilengruppen bereit für Zusammenführung gesamt**|Die Anzahl von Quellzeilengruppen, die seit dem Start von SQL Server für MERGE bereit sind.|  
|**Komprimierte zusammengeführte Zeilengruppen gesamt**|Die Anzahl von komprimierten Zielzeilengruppen, die seit dem Start von SQL Server mit MERGE erstellt wurden.|  
|**Zusammengeführte Quellzeilengruppen gesamt**|Die Anzahl von Quellzeilengruppen, die seit dem Start von SQL Server zusammengeführt wurden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
