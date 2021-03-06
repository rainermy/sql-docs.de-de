---
title: Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6135c1d2cbf1291465e1346f71010b8befe6f7b5
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100830"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client
  Bei einigen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client APIs werden Verbindungszeichenfolgen zur Angabe von Verbindungsattributen verwendet. Verbindungszeichenfolgen sind Listen von Schlüsselwörtern und zugehörigen Werten. Jedes Schlüsselwort bezeichnet ein spezielles Verbindungsattribut.  
  
 **Bitte beachten Sie!** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lässt aus Gründen der Abwärtskompatibilität Mehrdeutigkeit in Verbindungszeichenfolgen zu (einige Schlüsselwörter können beispielsweise mehrmals angegeben werden, und Konflikt verursachende Schlüsselwörter sind unter Umständen zulässig, wenn Konflikte anhand der Position oder Rangfolge aufgelöst werden). Zukünftige Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lassen möglicherweise keine Mehrdeutigkeit in Verbindungszeichenfolgen zu. Es empfiehlt sich beim Ändern von Anwendungen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu verwenden, um eine Abhängigkeit von der Mehrdeutigkeit von Verbindungszeichenfolgen zu umgehen.  
  
 In den folgenden Abschnitten werden die Schlüsselwörter beschrieben, die mit dem OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, dem ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und ADO (ActiveX Data Objects) verwendet werden können, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client als Datenanbieter verwendet wird.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Verbindungszeichenfolgen-Schlüsselwörter für den ODBC-Treiber  
 ODBC-Anwendungen verwenden die Verbindungszeichenfolgen als Parameter der [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) und [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md) Funktionen.  
  
 Die für ODBC verwendeten Verbindungszeichenfolge haben folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Attributwerte können optional in geschweifte Klammern eingeschlossen werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Attributwerte andere Zeichen als alphanumerische Zeichen enthalten. Da die erste rechte geschweifte Klammer als Endzeichen des Werts interpretiert wird, können Werte keine rechten geschweiften Klammern enthalten.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die in einer ODBC-Verbindungszeichenfolge verwendet werden können.  
  
|Schlüsselwort|Description|  
|-------------|-----------------|  
|`Addr`|Synonym für "Address".|  
|`Address`|Die Netzwerkadresse des Servers, auf dem eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird. `Address` ist normalerweise der Netzwerkname des Servers. Es können jedoch auch andere Namen sein, beispielsweise eine Pipe, eine IP-Adresse oder ein TCP/IP-Port und eine Socketadresse.<br /><br /> Wenn Sie eine IP-Adresse angeben, stellen Sie im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager sicher, dass die Protokolle für TCP/IP oder Named Pipes aktiviert sind.<br /><br /> Bei der Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client hat in ODBC-Verbindungszeichenfolgen der Wert von `Address` Vorrang vor dem Wert, der an `Server` übergeben wird. Zudem ist zu beachten, dass mit der Angabe `Address=;` eine Verbindung mit dem im `Server`-Schlüsselwort angegebenen Server hergestellt wird. Die Angaben `Address= ;, Address=.;`, `Address=localhost;` und `Address=(local);` führen dagegen zu einer Verbindungsherstellung mit dem lokalen Server.<br /><br /> Die vollständige Syntax für das `Address`-Schlüsselwort ist folgendermaßen:<br /><br /> [*Protokoll*`:`]*Adresse*[`,`*Port &#124;\pipe\pipename*]<br /><br /> *Protokoll* kann `tcp` (TCP/IP), `lpc` (shared Memory) oder `np` (named Pipes). Weitere Informationen zu Protokollen finden Sie unter [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Wenn weder *Protokoll* noch die `Network` Schlüsselwort angegeben ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet die Protokollreihenfolge im angegebenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Konfigurations-Manager.<br /><br /> *port* gibt den Port auf dem angegebenen Server an, zu dem eine Verbindung hergestellt werden soll. In der Standardeinstellung verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Port 1433.|  
|`AnsiNPW`|Bei Angabe von "yes" verwendet der Treiber die im ANSI-Standard definierten Verhaltensweisen zum Behandeln von NULL-Vergleichen, Auffüllung mit Zeichendaten, Warnungen und NULL-Verkettungen. Bei Angabe von "no", werden die im ANSI-Standard definierten Verhaltensweisen nicht verwendet. Weitere Informationen zum Ansinpw-Verhalten, finden Sie unter [Effekte von ISO-Optionen](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`APP`|Name der aufrufenden Anwendung [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) (optional). Wenn angegeben, wird dieser Wert gespeichert, der **master.dbo.sysprocesses** Spalte **Program_name** und wird zurückgegeben, indem [Sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) und [APP_NAME](/sql/t-sql/functions/app-name-transact-sql)Funktionen.|  
|`ApplicationIntent`|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind `ReadOnly` und `ReadWrite`. Zum Beispiel: ApplicationIntent=ReadOnly<br /><br /> Der Standardwert ist `ReadWrite`. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [SQL Server Native Client-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|Name der primären Datei einer anfügbaren Datenbank. Geben Sie den vollständigen Pfad an, und versehen Sie sämtliche umgekehrten Schrägstriche (\) mit Escapezeichen, wenn eine C-Zeichenfolgenvariable verwendet wird:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Diese Datenbank wird angefügt und als Standarddatenbank für die Verbindung verwendet. Verwendung von `AttachDBFileName` müssen Sie auch den Datenbanknamen angeben, entweder in der [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) DATABASE-Parameter oder die SQL_COPT_CURRENT_CATALOG-Verbindungsattribut. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an. Die angefügte Datenbank wird standardmäßig für die Verbindung verwendet.|  
|`AutoTranslate`|Bei der Angabe von "yes" werden ANSI-Zeichenfolgen übersetzt, die zwischen Client und Server übermittelt werden, indem sie über Unicode konvertiert werden, um so Probleme bei der Zuordnung von Sonderzeichen zwischen den Codeseiten auf Client und Server zu minimieren.<br /><br /> SQL_C_CHAR-Clientdaten gesendet, um eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Char**, **Varchar**, oder **Text** Variablen,-Parameter oder-Spalten aus Zeichen in Unicode konvertiert mithilfe des-Clients ANSI-Codepage (ACP), klicken Sie dann aus Unicode wieder in Zeichen mithilfe der ACP des Servers konvertiert.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Char**, **Varchar**, oder **Text** Datenübertragungen an eine Clientvariable ist eine Konvertierung von Zeichen in Unicode verwenden die Server-ACP konvertiert und dann aus Unicode wieder in Zeichen, mit dem Client ACP.<br /><br /> Diese Konvertierungen werden vom ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client auf dem Client durchgeführt. Dies erfordert, dass auf dem Client die gleiche ACP verfügbar ist, die auf dem Server verwendet wird.<br /><br /> Diese Einstellungen haben keine Auswirkungen auf die Konvertierungen, die für diese Übertragungen stattfinden:<br /><br /> -Client-Daten Unicode-SQL_C_WCHAR gesendet, um **Char**, **Varchar**, oder **Text** auf dem Server.<br />-   **Char**, **Varchar**, oder **Text** Serverdaten, die an eine Unicode SQL_C_WCHAR-Variable auf dem Client gesendet.<br />-ANSI SQL_C_CHAR-Clientdaten in Unicode gesendet **Nchar**, **Nvarchar**, oder **Ntext** auf dem Server.<br />-Unicode- **Nchar**, **Nvarchar**, oder **Ntext** Serverdaten, die an eine ANSI-SQL_C_CHAR-Variable auf dem Client gesendet.<br /><br /> Bei Angabe von "no" wird keine Zeichenübersetzung durchgeführt.<br /><br /> Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber übersetzt keine Client ANSI-Zeichen des Typs SQL_C_CHAR-Daten gesendet, um **Char**, **Varchar**, oder **Text** Variablen, Parameter oder Spalten, auf dem Server. Keine Übersetzung erfolgt auf **Char**, **Varchar**, oder **Text** SQL_C_CHAR-Variablen, auf dem Client vom Server gesendeten Daten.<br /><br /> Wenn der Client und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterschiedliche ACPs verwenden, können Sonderzeichen falsch interpretiert werden.|  
|`Database`|Der Name der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standarddatenbank, die für die Verbindung verwendet wird. Wenn `Database` nicht angegeben wird, wird die für die Anmeldung definierte Standarddatenbank verwendet. Die Standarddatenbank der ODBC-Datenquelle überschreibt die für die Anmeldung definierte Standarddatenbank. Diese Datenbank muss vorhanden sein, sofern nicht zusätzlich `AttachDBFileName` angegeben wird. Wenn auch `AttachDBFileName` angegeben wird, dann wird die primäre Datei, die hiermit bezeichnet wird, angehängt und mit dem in `Database` angegebenen Datenbanknamen benannt.|  
|`Driver`|Name des Treibers, der vom [SQLDrivers](../../native-client-odbc-api/sqldrivers.md). Der Schlüsselwortwert für den ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client lautet "{SQL Server Native Client 11.0}". Das `Server`-Schlüsselwort ist erforderlich, wenn `Driver` angegeben wird und `DriverCompletion` auf SQL_DRIVER_NOPROMPT festgelegt wurde.<br /><br /> Weitere Informationen zu Treibernamen finden Sie unter [mithilfe der SQL Server Native Client-Header und Bibliotheksdateien](using-the-sql-server-native-client-header-and-library-files.md).|  
|`DSN`|Der Name einer vorhandenen ODBC-Benutzer- oder Systemdatenquelle. Dieses Schlüsselwort überschreibt alle Werte, die möglicherweise in den Schlüsselwörtern `Server`, `Network` und `Address` angegeben werden.|  
|`Encrypt`|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|`Fallback`|Dieses Schlüsselwort ist veraltet, und seine Einstellung wird vom ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ignoriert.|  
|`Failover_Partner`|Name des Failoverpartnerservers, der verwendet werden soll, wenn keine Verbindung mit dem primären Server hergestellt werden kann.|  
|`FailoverPartnerSPN`|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
|`FileDSN`|Der Name einer vorhandenen ODBC-Dateidatenquelle.|  
|`Language`|Name der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprache (optional). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] kann Nachrichten für mehrere Sprachen in speichern **Sysmessages**. Wenn in mehreren Sprachen Verbindungen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hergestellt werden, dann wird mit `Language` festgelegt, welcher Satz an Meldungen für die Verbindung verwendet werden soll.|  
|`MARS_Connection`|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung. Gültige Werte sind "yes" und "no". Der Standardwert ist "no".|  
|`MultiSubnetFailover`|Geben Sie immer `multiSubnetFailover=Yes` an, wenn Sie eine Verbindung mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Verfügbarkeitsgruppenlistener oder einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failovercluster-Verfügbarkeitsgruppenlistener herstellen. `multiSubnetFailover=Yes` konfiguriert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den systemeigenen Client, um eine schnellere Erkennung sowie die Verbindung zum (derzeit) aktiven Server zu gewährleisten. Mögliche Werte sind `Yes` und `No`. Zum Beispiel:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Der Standardwert ist `No`. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [SQL Server Native Client-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Net`|Synonym für "Network".|  
|`Network`|Gültige Werte sind **Dbnmpntw** (named Pipes) und **Dbmssocn** (TCP/IP).<br /><br /> Es führt zu einem Fehler, sowohl einen Wert für das Schlüsselwort `Network` als auch einen Protokollpräfix im Schlüsselwort `Server` anzugeben.|  
|`PWD`|Das Kennwort für das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldekonto, das im UID-Parameter angegeben ist. `PWD` muss nicht angegeben werden, wenn die Anmeldung ein Kennwort vom Typ NULL aufweist oder wenn die Windows-Authentifizierung (`Trusted_Connection = yes`) verwendet wird.|  
|`QueryLog_On`|Bei Angabe von "yes", wird die Protokollierung von langwierigen Abfragen für die Verbindung aktiviert. Bei Angabe von "no" werden keine Daten über langwierige Abfragen protokolliert.|  
|`QueryLogFile`|Vollständiger Pfad- und Dateiname einer Datei, die zur Protokollierung von Daten über Abfragen mit langer Ausführungsdauer verwendet werden soll.|  
|`QueryLogTime`|Ziffernzeichenfolge, die den Schwellenwert (in Millisekunden) zum Protokollieren von langwierigen Abfragen angibt. Jede Abfrage, die nicht innerhalb eines gewissen Zeitraums eine Antwort vom Server erhält, wird in die Protokolldatei für Abfragen langer Ausführungsdauer geschrieben.|  
|`QuotedId`|Bei Angabe von "yes" wird QUOTED_IDENTIFIER für die Verbindung auf ON festgelegt, und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befolgt die ISO-Regeln hinsichtlich der Verwendung von Anführungszeichen in SQL-Anweisungen. Andernfalls wird QUOTED_IDENTIFIERS für die Verbindung auf OFF gesetzt. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] befolgt anschließend die [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Legacyregeln im Hinblick auf die Verwendung von Anführungszeichen in SQL-Anweisungen. Weitere Informationen finden Sie unter [Effekte von ISO-Optionen](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`Regional`|Bei Angabe von "yes" verwendet der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Clienteinstellungen, wenn Währungs-, Datums- oder Zeitdaten in Zeichendaten konvertiert werden. Die Konvertierung ist unidirektional. Der Treiber erkennt nur ODBC-Standardformate in zu konvertierenden Datumszeichenfolgen oder Währungswerten, beispielsweise Parameter in einer INSERT- oder UPDATE-Anweisung. Bei Angabe von "no" verwendet der Treiber ODBC-Standardzeichenfolgen zur Darstellung von Währungs-, Datums- und Zeitdaten, die in Zeichendaten konvertiert werden.|  
|`SaveFile`|Der Name einer ODBC-Datenquellendatei, in der die Attribute der aktuellen Verbindung gespeichert werden, wenn die Verbindung erfolgreich hergestellt wurde.|  
|`Server`|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz. Als Wert muss entweder der Name eines Servers im Netzwerk, eine IP-Adresse oder der Aliasname eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Managers angegeben werden.<br /><br /> Das `Address`-Schlüsselwort überschreibt das `Server`-Schlüsselwort.<br /><br /> Sie können eine Verbindung mit der Standardinstanz auf dem lokalen Server herstellen, indem Sie eine der folgenden Optionen angeben:<br /><br /> -   `Server=;`<br />-   `Server=.;`<br />-   `Server=(local);`<br />-   `Server=(localhost);`<br />-   **Server=(LocalDB)\\**  _Instanzname_ `;`<br /><br /> Weitere Informationen zur Unterstützung von LocalDB finden Sie unter [SQL Server Native Clientunterstützung für LocalDB](../features/sql-server-native-client-support-for-localdb.md).<br /><br /> Angeben eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], fügen Sie **\\** _InstanceName_.<br /><br /> Ohne Angabe eines Servers wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Wenn Sie eine IP-Adresse angeben, stellen Sie im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager sicher, dass die Protokolle für TCP/IP oder Named Pipes aktiviert sind.<br /><br /> Die vollständige Syntax für das `Server`-Schlüsselwort ist folgendermaßen:<br /><br /> `Server=`[*Protokoll*`:`]*Server*[`,`*Port*]<br /><br /> *Protokoll* kann `tcp` (TCP/IP), `lpc` (shared Memory) oder `np` (named Pipes).<br /><br /> Im folgenden Beispiel wird die Angabe einer Named Pipe veranschaulicht:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Diese Zeile gibt das Named Pipe-Protokoll, eine Named Pipe auf dem lokalen Computer (`\\.\pipe`), den Namen der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz (`MSSQL$MYINST01`) und den Standardnamen der Named Pipe (`sql/query`) an.<br /><br /> Wenn weder ein *Protokoll* noch die `Network` Schlüsselwort angegeben ist, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet die Protokollreihenfolge im angegebenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Konfigurations-Manager.<br /><br /> *port* gibt den Port auf dem angegebenen Server an, zu dem eine Verbindung hergestellt werden soll. In der Standardeinstellung verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Port 1433.<br /><br /> Bei der Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client werden Leerzeichen am Anfang des an `Server` übergebenen Werts in ODBC-Verbindungszeichenfolgen ignoriert.|  
|`ServerSPN`|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
|`StatsLog_On`|Durch die Angabe von "yes" wird die Aufzeichnung von Leistungsdaten zum ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native aktiviert. Wenn "no" angegeben wird, sind die Leistungsdaten zum ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client nicht für die Verbindung verfügbar.|  
|`StatsLogFile`|Der vollständige Pfad- und Dateiname einer Datei, die zum Aufzeichnen der statistischen Daten zur Leistung des ODBC-Treibers von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet werden soll.|  
|`Trusted_Connection`|Durch die Angabe von "yes" wird der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, den Windows-Authentifizierungsmodus zur Überprüfung der Anmeldung zu verwenden. Andernfalls wird der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzernamen und ein Kennwort zur Überprüfung der Anmeldung zu verwenden, und in diesem Fall müssen die Schlüsselwörter UID und PWD angegeben werden.|  
|`TrustServerCertificate`|Wenn dieses Schlüsselwort in Verbindung mit `Encrypt` angegeben wird, wird die Verschlüsselung unter Verwendung eines selbstsignierten Serverzertifikats ermöglicht.|  
|`UID`|Ein gültiges [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldekonto. Bei Verwendung der Windows-Authentifizierung muss nicht UID angegeben werden.|  
|`UseProcForPrepare`|Dieses Schlüsselwort ist veraltet, und seine Einstellung wird ignoriert, durch die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber.|  
|`WSID`|Die ID der Arbeitsstation. Normalerweise ist dies der Netzwerkname des Computers, auf dem sich die Anwendung befindet (optional). Wenn angegeben, wird dieser Wert gespeichert, der **master.dbo.sysprocesses** Spalte **Hostname** und wird zurückgegeben, indem [Sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) und [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql)Funktion.|  
  
 **Regionale Konvertierungseinstellungen gelten für währungs-, numerischen, Datums- und Uhrzeitdatentypen. Die konvertierungseinstellung gilt nur für ausgabekonvertierungen und ist nur sichtbar, wenn die Währung, numerischen, Datums- oder Uhrzeitwerte in Zeichenfolgen konvertiert werden**.  
  
 Der ODBC-Treiber von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client verwendet die für den aktuellen Benutzer geltenden Registrierungseinstellungen für das Gebietsschema. Der Treiber berücksichtigt des aktuellen Threads nicht, wenn die Anwendung nach der Verbindung von, z. B. wird aufrufen **SetThreadLocale**.  
  
 Das Verändern des regionalen Verhaltens einer Datenquelle kann Anwendungsfehler verursachen. Eine Anwendung, die Datumszeichenfolgen analysiert und erwartet, dass angezeigt werden, wie die ODBC-Definition kann beeinträchtigt werden, durch die Änderung dieses Werts.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Verbindungszeichenfolgen-Schlüsselwörter für den OLE DB-Anbieter  
 OLE DB-Anwendungen können Datenquellenobjekte auf zweierlei Weise initialisieren:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Im ersten Fall kann die Anbieterzeichenfolge zum Initialisieren der Verbindungseigenschaften verwendet werden, indem die DBPROP_INIT_PROVIDERSTRING-Eigenschaft im DBPROPSET_DBINIT-Eigenschaftensatz festgelegt wird. Im zweiten Fall kann eine Initialisierungszeichenfolge an die **IDataInitialize::GetDataSource**-Methode übergeben werden, um die Verbindungseigenschaften zu initialisieren. Beide Methoden initialisieren die gleichen OLE DB-Verbindungseigenschaften, es werden jedoch andere Sätze von Schlüsselwörtern verwendet. Die von **IDataInitialize::GetDataSource** verwendeten Schlüsselwörter entsprechen mindestens der Beschreibung der in der Gruppe der Initialisierungseigenschaften enthaltenen Eigenschaften.  
  
 Bei jeder Anbieterzeichenfolgeneinstellung, für die eine zugehörige OLE DB-Eigenschaft vorhanden ist, die auf einen bestimmten Standardwert festgelegt ist oder auf einen spezifischen Wert festgelegt wird, überschreibt der OLE DB-Eigenschaftswert die Einstellung in der Anbieterzeichenfolge.  
  
 Für boolesche Eigenschaften, die in Anbieterzeichenfolgen über DBPROP_INIT_PROVIDERSTRING-Werte festgelegt werden, werden die Werte "yes" und "no" angegeben. Für boolesche Eigenschaften, die in Initialisierungszeichenfolgen über **IDataInitialize::GetDataSource** festgelegt werden, werden die Werte TRUE und FALSE angegeben.  
  
 In Anwendungen, in denen **IDataInitialize::GetDataSource** verwendet wird, können auch die Schlüsselwörter für **IDBInitialize::Initialize** verwendet werden, allerdings nur für Eigenschaften, die nicht über einen Standardwert verfügen. Wenn eine Anwendung sowohl das **IDataInitialize::GetDataSource**-Schlüsselwort als auch das **IDBInitialize::Initialize**-Schlüsselwort in der Initialisierungszeichenfolge angibt, dann wird die **IDataInitialize::GetDataSource**-Schlüsselworteinstellung verwendet. Es wird dringend empfohlen, dass Anwendungen keine **IDBInitialize::Initialize**-Schlüsselwörter in **IDataInitialize:GetDataSource**-Verbindungszeichenfolgen verwenden, da dieses Verhalten in künftigen Versionen möglicherweise nicht beibehalten wird.  
  
 **Hinweis**: Eine von **IDataInitialize::GetDataSource** übergebene Verbindungszeichenfolge wird in Eigenschaften konvertiert und mithilfe von **IDBProperties::SetProperties** angewendet. Wenn Komponentendienste die Eigenschaftenbeschreibung in **IDBProperties::GetPropertyInfo** gefunden haben, wird diese Eigenschaft als eigenständige Eigenschaft angewendet. Andernfalls wird sie mithilfe der DBPROP_PROVIDERSTRING-Eigenschaft angewendet. Wenn Sie angeben, dass die Verbindungszeichenfolge z. B. **Data Source = server1; Server = server2**, `Data Source` wird als Eigenschaft festgelegt werden, aber `Server` ein Wechsel in eine Anbieterzeichenfolge übernommen.  
  
 Wenn Sie mehrere Instanzen einer anbieterspezifischen Eigenschaft angeben, wird der erste Wert der ersten Eigenschaft verwendet.  
  
 Für Verbindungszeichenfolgen, die in OLE DB-Anwendungen unter Verwendung von DBPROP_INIT_PROVIDERSTRING mit **IDBInitialize::Initialize** verwendet werden, gilt die folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Attributwerte können optional in geschweifte Klammern eingeschlossen werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Attributwerte andere Zeichen als alphanumerische Zeichen enthalten. Da die erste rechte geschweifte Klammer als Endzeichen des Werts interpretiert wird, können Werte keine rechten geschweiften Klammern enthalten.  
  
 Ein Leerzeichen nach dem Gleichheitszeichen (=) eines Verbindungszeichenfolgen-Schlüsselworts wird als Literal interpretiert. Dies gilt auch, wenn der Wert in Anführungszeichen gesetzt ist.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die mit DBPROP_INIT_PROVIDERSTRING verwendet werden können.  
  
|Schlüsselwort|Initialisierungseigenschaft|Description|  
|-------------|-----------------------------|-----------------|  
|`Addr`|SSPROP_INIT_NETWORKADDRESS|Synonym für "Address".|  
|`Address`|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie weiter unten in diesem Thema in der Beschreibung des ODBC-Schlüsselworts `Address`.|  
|`APP`|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|`ApplicationIntent`|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind `ReadOnly` und `ReadWrite`.<br /><br /> Der Standardwert ist `ReadWrite`. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [SQL Server Native Client-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Um `AttachDBFileName` verwenden zu können, muss auch der Datenbankname mit dem Schlüsselwort Database für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Gültige Werte sind "yes" und "no".|  
|`Database`|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus des Datentyps, die die Verarbeitung verwenden. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für SQL Server 2000-Datentypen.|  
|`Encrypt`|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|`FailoverPartner`|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|`FailoverPartnerSPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|`Language`|SSPROPT_INIT_CURRENTLANGUAGE|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprache.|  
|`MarsConn`|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung, wenn auf dem Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird. Mögliche Werte sind "yes" und "no". Der Standardwert lautet "no".|  
|`Net`|SSPROP_INIT_NETWORKLIBRARY|Synonym für "Network".|  
|`Network`|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Synonym für "Network".|  
|`PacketSize`|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|`PersistSensitive`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "yes" und "no" als Werte. Wenn "no" angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen persistent speichern.|  
|`PWD`|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Server`|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des ODBC-Schlüsselworts `Server`.|  
|`ServerSPN`|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|`Timeout`|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|`Trusted_Connection`|DBPROP_AUTH_INTEGRATED|Durch die Angabe von "yes" wird der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, den Windows-Authentifizierungsmodus zur Überprüfung der Anmeldung zu verwenden. Andernfalls wird der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Native Client angewiesen, einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzernamen und ein Kennwort zur Überprüfung der Anmeldung zu verwenden, und in diesem Fall müssen die Schlüsselwörter UID und PWD angegeben werden.|  
|`TrustServerCertificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "yes" und "no" als Werte. Der Standardwert lautet "no" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|`UID`|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|`UseProcForPrepare`|SSPROP_INIT_USEPROCFORPREP|Dieses Schlüsselwort ist veraltet, und seine Einstellung wird vom OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ignoriert.|  
|`WSID`|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 Verbindungszeichenfolgen, die von OLE DB-Anwendungen verwendet werden, welche **IDataInitialize::GetDataSource** verwenden, haben die folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Die Verwendung von Eigenschaften muss der jeweils dafür zulässigen Syntax entsprechen.  Z. B. `WSID` geschweifte Klammern (`{}`) Anführungszeichen und `Application Name` verwendet einzelne (`'`) oder doppelte (`"`) Anführungszeichen. Es können nur Zeichenfolgeneigenschaften in Anführungszeichen gesetzt werden. Wenn Sie versuchen, eine ganze Zahl oder eine aufgezählte Eigenschaft in Anführungszeichen zu setzen, wird der Fehler angezeigt, dass die Verbindungszeichenfolge keiner OLE DB-Spezifikation entspricht.  
  
 Attributwerte können optional in einfache oder doppelte Anführungszeichen gesetzt werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Werte andere Zeichen als alphanumerische Zeichen enthalten. Das verwendete Anführungszeichen kann auch innerhalb von Werten stehen, vorausgesetzt, dass es doppelt angegeben wird.  
  
 Ein Leerzeichen nach dem Gleichheitszeichen (=) eines Verbindungszeichenfolgen-Schlüsselworts wird als Literal interpretiert. Dies gilt auch, wenn der Wert in Anführungszeichen gesetzt ist.  
  
 Wenn eine Verbindungszeichenfolge mehrere der in der folgenden Tabelle aufgeführten Eigenschaften aufweist, wird der Wert der letzten Eigenschaft verwendet.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die mit **IDataInitialize::GetDataSource** verwendet werden können:  
  
|Schlüsselwort|Initialisierungseigenschaft|Description|  
|-------------|-----------------------------|-----------------|  
|`Application Name`|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind `ReadOnly` und `ReadWrite`.<br /><br /> Der Standardwert ist `ReadWrite`. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [SQL Server Native Client-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Zulässig sind die Werte "true" und "false".|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprachenname.|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie weiter unten in diesem Thema in der Beschreibung des ODBC-Schlüsselworts `Server`.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus des Datentyps, die die Verarbeitung verwenden. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]-Datentypen.|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Um `AttachDBFileName` verwenden zu können, muss auch der Datenbankname mit dem Schlüsselwort DATABASE für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Akzeptiert den Wert "SSPI" für die Windows-Authentifizierung.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung. Zulässig sind die Werte "true" und "false". Der Standardwert lautet "false".|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie weiter unten in diesem Thema in der Beschreibung des ODBC-Schlüsselworts `Address`.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Wenn FALSE angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen dauerhaft speichern.|  
|`Provider`||Bei der Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sollte die Angabe "SQLNCLI11" lauten.|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Der Standardwert lautet "false" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.|  
|`User ID`|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|`Workstation ID`|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 **Hinweis:** In der Verbindungszeichenfolge legt die Eigenschaft „Old Password“ SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Schlüsselwörter für ActiveX Data Objects (ADO)-Verbindungszeichenfolgen  
 ADO-Anwendungen legen die **ConnectionString**-Eigenschaft von **ADODBConnection**-Objekten fest oder stellen eine Verbindungszeichenfolge als Parameter für die **Open**-Methode von **ADODBConnection**-Objekten bereit.  
  
 In ADO-Anwendungen können auch die Schlüsselwörter für die OLE DB-Methode **IDBInitialize::Initialize** verwendet werden, allerdings nur für Eigenschaften, die nicht über Standardwerte verfügen. Wenn eine Anwendung sowohl ADO-Schlüsselwörter als auch die **IDBInitialize::Initialize**-Schlüsselwörter in der Initialisierungszeichenfolge verwendet, dann wird die ADO-Schlüsselworteinstellung verwendet. Es wird dringend empfohlen, dass Anwendungen nur Schlüsselwörter für ADO-Verbindungszeichenfolgen verwenden.  
  
 Die für ADO verwendeten Verbindungszeichenfolge haben folgende Syntax:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Attributwerte können optional in doppelte Anführungszeichen eingeschlossen werden, und es wird empfohlen, dies zu tun. Dadurch werden Probleme vermieden, wenn Werte andere Zeichen als alphanumerische Zeichen enthalten. Attributwerte dürfen keine doppelten Anführungszeichen enthalten.  
  
 In der folgenden Tabelle werden die Schlüsselwörter beschrieben, die in einer ADO-Verbindungszeichenfolge verwendet werden können.  
  
|Schlüsselwort|Initialisierungseigenschaft|Description|  
|-------------|-----------------------------|-----------------|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einem Server. Mögliche Werte sind `ReadOnly` und `ReadWrite`.<br /><br /> Der Standardwert ist `ReadWrite`. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], finden Sie unter [SQL Server Native Client-Support für hohe Verfügbarkeit, Wiederherstellung im Notfall](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Application Name`|SSPROP_INIT_APPNAME|Die Zeichenfolge, die die Anwendung identifiziert.|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Synonym für "AutoTranslate".|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Konfiguriert die OEM-/ANSI-Zeichenübersetzung. Zulässig sind die Werte "true" und "false".|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Der Zeitraum (in Sekunden), der bis zum Abschluss der Datenquelleninitialisierung abgewartet werden soll.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sprachenname.|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Der Name einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz in der Organisation.<br /><br /> Ohne Angabe eines Namens wird eine Verbindung mit der Standardinstanz auf dem lokalen Computer hergestellt.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des ODBC-Schlüsselworts `Server`.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Gibt den Modus der zu verwendenden Datentypbehandlung an. Zulässig sind der Wert "0" für Anbieterdatentypen und der Wert "80" für SQL Server 2000-Datentypen.|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Der Name des für die Datenbankspiegelung zu verwendenden Failoverservers.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Der Datenbankname.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Der Name der Primärdatenbank (einschließlich des vollständigen Pfadnamens) einer anfügbaren Datenbank. Um `AttachDBFileName` verwenden zu können, muss auch der Datenbankname mit dem Schlüsselwort DATABASE für die Anbieterzeichenfolge angegeben werden. Wenn die Datenbank zuvor angefügt worden war, fügt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie nicht erneut an (die angefügte Datenbank wird standardmäßig für die Verbindung verwendet).|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Akzeptiert den Wert "SSPI" für die Windows-Authentifizierung.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Ermöglicht oder unterbindet die Verwendung von mehreren aktiven Resultsets (MARS) bei einer Verbindung, wenn auf dem Server [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] oder höher ausgeführt wird. Zulässig sind die Werte "true" und "false". Der Standardwert lautet "false".|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Die Netzwerkadresse einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation.<br /><br /> Weitere Informationen zur Syntax einer gültigen Adresse finden Sie in diesem Thema in der Beschreibung des ODBC-Schlüsselworts `Address`.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Die Netzwerkbibliothek, die zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Organisation verwendet wird.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Netzwerkpaketgröße. Der Standardwert lautet 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Das Anmeldekennwort für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Wenn "false" angegeben wird, darf das Datenquellenobjekt keine vertraulichen Authentifizierungsinformationen persistent speichern.|  
|`Provider`||Bei der Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sollte die Angabe "SQLNCLI11" lauten.|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge. Die Angabe einer leeren Zeichenfolge bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Anbieter generierten SPN verwendet.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Akzeptiert die Zeichenfolgen "true" und "false" als Werte. Der Standardwert lautet "false" und bedeutet, dass das Serverzertifikat überprüft wird.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Gibt an, ob Daten vor dem Senden über das Netzwerk verschlüsselt werden sollen. Mögliche Werte sind "true" und "false". Der Standardwert ist FALSE.|  
|`User ID`|DBPROP_AUTH_USERID|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename.|  
|`Workstation ID`|SSPROP_INIT_WSID|Der Bezeichner der Arbeitsstation.|  
  
 **Hinweis:** In der Verbindungszeichenfolge legt die Eigenschaft „Old Password“ SSPROP_AUTH_OLD_PASSWORD fest. Dies entspricht dem aktuellen (möglicherweise abgelaufenen) Kennwort, das nicht über eine Anbieterzeichenfolgen-Eigenschaft verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
