---
title: Eigenschaften von Analysis-Servern (Registerkarte „Dienst“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4f083aafd2dc8718bb79798d43483c66b3520b0d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795872"
---
# <a name="analysis-server-properties-service-tab"></a>Analysis-Server-Eigenschaften (Registerkarte Dienst)
  Hierbei handelt es sich um den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Dienst. Dieser Dienst ist für die ordnungsgemäße Ausführung von [!INCLUDE[ssAS](../../includes/ssas-md.md)] zwingend erforderlich. Die ausgegrauten Eigenschaftswerte können nicht mithilfe dieser Anwendung geändert werden.  
  
## <a name="options"></a>Optionen  
 **Binärpfad**  
 Zeigt den Speicherort der Programmdateien an, die von diesem Dienst verwendet werden.  
  
 **Fehlersteuerung**  
 1 steht für `SERVICE_ERROR_NORMAL`. Wenn der Dienst nicht zusammen mit dem Computer gestartet werden kann, wird der Fehler vom Startprogramm protokolliert und eine Popupmeldung angezeigt, der Startvorgang aber fortgesetzt. Dieser Wert kann nicht geändert werden.  
  
 **Exitcode**  
 Bei einem Fehler wird die dazu gehörende Nummer in diesem Feld angezeigt. Verwenden Sie diese Nummer für die Problembehandlung. Stellen Sie die Fehlernummer dem technischen Support zur Verfügung, oder durchsuchen Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base.  
  
 **HostName**  
 Zeigt den Namen des Computers oder Clusters an, auf dem [!INCLUDE[ssAS](../../includes/ssas-md.md)]ausgeführt wird.  
  
 **Name**  
 Zeigt den Anzeigenamen des Dienstes an.  
  
 **Prozess-ID**  
 Zeigt die Nummer an, die von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows zum Nachverfolgen der Prozesse dieses Programms verwendet wird.  
  
 **SQL-Diensttyp**  
 Zeigt den für aufrufende Prozesse bereitgestellten Diensttyp an. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden mehrere Dienste installiert.  
  
 **Startmodus**  
 Richten Sie den Dienst mit den folgenden Auswahlmöglichkeiten ein:  
  
-   Manuell: Dieser Dienst wird nicht automatisch zusammen mit dem Computer gestartet. Zum Starten des Dienstes verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager oder ein anderes Tool.  
  
-   Automatisch: Dieser Dienst wird zusammen mit dem Computer gestartet.  
  
-   Deaktiviert: Der Dienst kann nicht gestartet werden.  
  
 **Zustand**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist.  
  
  
