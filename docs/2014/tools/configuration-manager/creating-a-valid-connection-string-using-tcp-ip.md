---
title: Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine]
- ports [SQL Server], connecting to
- TCP/IP [SQL Server], connection strings
- connection strings [Database Engine], TCP/IP
- aliases [SQL Server], TCP/IP
ms.assetid: ee5dbc2c-1fc6-42bd-bdf5-efa792557934
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6449b073adb406d15f41cfe02d477a05ad8b0b31
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52764252"
---
# <a name="creating-a-valid-connection-string-using-tcp-ip"></a>Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP
  Führen Sie folgende Schritte aus, um eine gültige Verbindungszeichenfolge mithilfe von TCP/IP zu erstellen:  
  
-   Geben Sie einen **Aliasnamen**an.  
  
-   Geben Sie im Feld **Server**entweder den Namen eines Servers an, mit dem Sie eine Verbindung mithilfe des Hilfsprogramms **PING** herstellen können, oder eine IP-Adresse an, mit der Sie eine Verbindung mithilfe des Hilfsprogramms **PING** herstellen können. Bei einer benannten Instanz hängen Sie den Namen der Instanz an.  
  
-   Geben Sie **TCP/IP** für das **Protokoll**an.  
  
-   Optional können Sie auch eine Portnummer für das Feld **Portnummer**eingeben. Der Standard ist 1433. Dies ist die Portnummer der Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf einem Server. Geben Sie die Portnummer an oder starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst, um eine Verbindung zu einer benannten Instanz oder einer Standardinstanz herzustellen, die nicht an Port 1433 lauscht. Weitere Informationen zum Konfigurieren des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdiensts finden Sie unter [SQL Server-Browserdienst](../../../2014/tools/configuration-manager/sql-server-browser-service.md).  
  
 Während der Verbindung werden von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Komponente die Werte für den Server, das Protokoll und den Port aus der Registrierung für den angegebenen Aliasnamen gelesen und eine Verbindungszeichenfolge im Format `tcp:<servername>[\<instancename>],<port>` oder `tcp:<IPAddress>[\<instancename>],<port>`erstellt.  
  
> [!NOTE]  
>  Der Port 1433 wird von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Firewall standardmäßig geschlossen. Da [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über den Port 1433 kommuniziert, müssen Sie diesen Port erneut öffnen, falls [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Überprüfen eingehender Clientverbindungen mithilfe von TCP/IP konfiguriert wurde. Informationen zum Konfigurieren einer Firewall finden Sie unter „Gewusst wie: Konfigurieren einer Firewall für SQL Server-Zugriff“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation oder in Ihrer Firewalldokumentation.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client unterstützen das Internetprotokoll, Version 4 (IPv4), und das Internetprotokoll, Version 6 (IPv6), vollständig. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager akzeptiert sowohl IPv4- als auch IPv6-Formate für IP-Adressen. Informationen zu IPv6 finden Sie unter "Herstellen von Verbindungen über IPv6" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="connecting-to-the-local-server"></a>Herstellen einer Verbindung mit dem lokalen Server  
 Beim Herstellen einer Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , das auf dem gleichen Computer wie der Client ausgeführt wird, können Sie `(local)` als Servernamen verwenden. Aus Gründen der Mehrdeutigkeit wird dies nicht empfohlen, kann aber nützlich sein, wenn vom Client bekannt ist, dass er auf dem vorgesehenen Computer ausgeführt wird. Beim Erstellen einer Anwendung für mobile Benutzer mit getrennter Verbindung (beispielsweise für Verkaufspersonal, wobei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Laptops ausgeführt und zum Speichern von Projektdaten verwendet wird) würde beispielsweise die Verbindung eines Clients zu `(local)` immer zu der auf dem Laptop ausgeführten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt. Anstelle von `localhost` kann das Wort**oder ein Punkt (**. `(local)`) verwendet werden.  
  
## <a name="verifying-your-connection-protocol"></a>Überprüfen des Verbindungsprotokolls  
 Die folgende Abfrage gibt das Protokoll zurück, das für die aktuelle Verbindung verwendet wird.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Beispiele  
 Verbindung über Servername:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Verbindung mit Servernamen zu einer benannten Instanz:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <servername>\<instancename>  
  
```  
  
 Verbindung über Servername zu einem angegebenen Port:  
  
```  
Alias Name         <serveralias>  
Port No            <port>  
Protocol           TCP/IP  
Server             <servername>  
  
```  
  
 Verbindung über IP-Adresse:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Verbindung über IP-Adresse zu einer benannten Instanz:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             <IPAddress>\<instancename>  
  
```  
  
 Verbindung über IP-Adresse zu einem angegebenen Port:  
  
```  
Alias Name         <serveralias>  
Port No            <port number>  
Protocol           TCP/IP  
Server             <IPAddress>  
  
```  
  
 Verbindung zum lokalen Computer mithilfe von `(local)`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             (local)  
  
```  
  
 Verbindung zum lokalen Computer mithilfe von `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost  
  
```  
  
 Verbindung zu einer benannten Instanz auf dem lokalen Computer `localhost`:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             localhost\<instancename>  
  
```  
  
 Verbindung zum lokalen Computer mithilfe eines Punkts:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .  
  
```  
  
 Verbindung zu einer benannten Instanz auf dem lokalen Computer mithilfe eines Punkts:  
  
```  
Alias Name         <serveralias>  
Port No            <blank>  
Protocol           TCP/IP  
Server             .\<instancename>  
  
```  
  
> [!NOTE]  
>  Informationen zum Angeben des Netzwerkprotokolls als einen **Sqlcmd** Parameter finden Sie unter "Vorgehensweise: Herstellen einer Verbindung mit der Datenbank-Engine mithilfe von sqlcmd.exe“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)   
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
