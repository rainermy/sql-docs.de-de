---
title: Starten des Replikationsmonitors | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 389df9d30f4a1d1cace4f3943ba6ea22bcc846c9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124060"
---
# <a name="start-the-replication-monitor"></a>Starten des Replikationsmonitors
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Der Replikationsmonitor kann von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] auf jeder Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]oder von der Eingabeaufforderung aus gestartet werden. Nach dem Starten des Replikationsmonitors können Sie einen oder mehrere Verleger für die Überwachung hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen und Entfernen von Verlegern vom Replikationsmonitor aus](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>So starten Sie den Replikationsmonitor von SQL Server Management Studio aus  
  
1.  Stellen Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]her, und erweitern Sie dann den Serverknoten.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Replikation** oder auf einen der Unterordner dieses Ordners, und klicken Sie dann auf **Replikationsmonitor starten**.  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>So starten Sie den Replikationsmonitor von der Eingabeaufforderung aus  
  
1.  Navigieren Sie von der Eingabeaufforderung zum Installationsverzeichnis für Tools. Der Standardpfad ist [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\.  
  
2.  Führen Sie sqlmonitor.exe aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
