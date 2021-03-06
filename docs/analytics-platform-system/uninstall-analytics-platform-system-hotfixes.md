---
title: Deinstallieren von Analytics Platform System-Hotfixes auf | Microsoft-Dokumentation
description: Deinstallieren Sie die Hotfixes für Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5507eae7bb2f8a5ce138223a031ac4946d9f0030
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54255066"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Deinstallieren von Hotfixes für Analytics Platform System 
Die folgenden Schritte beschreiben, wie Sie einen zuvor installierten Hotfix für Analytics Platform System zu deinstallieren.  
  
## <a name="before-you-begin"></a>Vorbereitungen  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Diese Schritte ausführen zu können, benötigen Sie:  
  
-   Eine Analytics Platform System Anmeldenamen mit Berechtigungen zum Zugriff auf die Admin-Konsole zum Überwachen der Appliance.  
  
-   Das Konto des Domänenadministrators Anmelden die <em>< Appliance_domain ></em>**-HST01** Knoten.  
  
-   Nummer des Knowledge Base-Artikel für das Hotfix deinstallieren.  
  
## <a name="HowToUninstallPDW"></a>So deinstallieren Sie einen SQL Server-PDW-hotfix  
  
1.  Melden Sie sich an den <em>< Appliance_domain ></em>**-HST01** als Domänenadministrator Fabric-Knoten.  
  
2.  Verwenden Sie die Ausführung als Administrator aus, um eine Eingabeaufforderung zu öffnen.  
  
3.  Wechseln Sie zum `C:\PDWINST\Patches\<kbarticle>\media` , in denen *<kbarticle>* ist die Nummer des Knowledge Base-Artikel für das Hotfix deinstallieren.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Führen Sie den folgenden Befehl, um den Hotfix zu entfernen.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>Siehe auch  
[Microsoft-Updates herunterzuladen und anzuwenden &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Deinstallieren von Microsoft-Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Anwenden von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Softwarewartung &#40;Analytics Platform System&#41;](software-servicing.md)  
  
