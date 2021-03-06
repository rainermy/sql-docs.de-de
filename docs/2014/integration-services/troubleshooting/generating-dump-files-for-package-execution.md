---
title: Generieren von Sicherungsdateien für die Paketausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 61ef1731-cb3a-4afb-b4a4-059b04aeade0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00b75a698a372466dfe46d8997c730bb77ac2d1b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52799182"
---
# <a name="generating-dump-files-for-package-execution"></a>Generieren von Dumpdateien für die Paketausführung
  In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]können Sie Debugdumpdateien erstellen, die Informationen über die Ausführung eines Pakets enthalten. Die Informationen in diesen Dateien können Ihnen bei der Behebung von Problemen bei der Paketausführung helfen.  
  
> [!NOTE]  
>  Debugdumpdateien können vertrauliche Informationen enthalten. Zum Schutz vertraulicher Informationen können Sie eine Zugriffssteuerungsliste verwenden, um den Zugriff auf die Dateien einzuschränken oder die Dateien in einen Ordner mit eingeschränktem Zugriff zu kopieren. Bevor Sie Ihre Debugdateien beispielsweise an [!INCLUDE[msCoName](../../includes/msconame-md.md)] Support Services senden, empfehlen wir, sensible oder vertrauliche Informationen zu entfernen.  
  
 Wenn Sie auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server ein Projekt bereitstellen, können Sie Dumpdateien erstellen, die Informationen über die Ausführung der im Projekt enthaltenen Pakete bereitstellen. Wenn der Prozess "ISServerExec.exe" beendet wird, werden die Dumpdateien erstellt. Sie können angeben, dass eine Dumpdatei erstellt wird, wenn Fehler während der Paketausführung auftreten, indem Sie im Dialogfeld **Paket ausführen** die Option für die Speicherung von **Dumps bei Fehlern** auswählen. Außerdem können Sie Folgendes als gespeicherte Prozeduren verwenden.  
  
-   [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
     Rufen Sie diese gespeicherte Prozedur auf, um zu konfigurieren, dass eine Dumpdatei erstellt wird, wenn ein Fehler oder ein Ereignis auftritt, und wenn spezifische Ereignisse während einer Paketausführung auftreten.  
  
-   [catalog.create_execution_dump](/sql/integration-services/system-stored-procedures/catalog-create-execution-dump)  
  
     Rufen Sie diese gespeicherte Prozedur auf, um ein ausgeführtes Paket zu veranlassen, eine Dumpdatei anzuhalten und zu erstellen.  
  
 Wenn Sie Pakete mithilfe des Paketbereitstellungsmodells bereitstellen, erstellen Sie die Debugdumpdateien, indem Sie entweder mit dem Hilfsprogramm **dtexec** oder dem Hilfsprogramm **dtutil** in der Befehlszeile eine Debugdumpoption angeben. Weitere Informationen finden Sie unter [dtexec Utility](../packages/dtexec-utility.md) und [dtutil Utility](../dtutil-utility.md). Weitere Informationen zu paketbereitstellungsmodellen finden Sie unter [Bereitstellung von Projekten und Paketen](../packages/deploy-integration-services-ssis-projects-and-packages.md) und [Paketbereitstellung &#40;SSIS&#41;](../packages/legacy-package-deployment-ssis.md).  
  
## <a name="debug-dump-file-format"></a>Format der Debugdumpdateien  
 Wenn Sie eine Debugdumpoption angeben, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] die folgenden Debugdumpdateien:  
  
-   Eine .mdmp-Debugdumpdatei. Hierbei handelt es sich um eine Binärdatei.  
  
-   Eine .tmp-Debugdumpdatei. Hierbei handelt es sich um eine textformatierte Datei.  
  
 In der Standardeinstellung speichert [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] diese Dateien im Ordner *\<Laufwerk>:* \Programme\Microsoft SQL Server\110\Shared\ErrorDumps.  
  
 In der folgenden Tabelle werden nur bestimmte Abschnitte der TMP-Datei beschrieben. Die TMP-Datei schließt weitere Daten ein, die nicht in der Tabelle aufgeführt werden.  
  
|Art der Informationen|Description|Beispiel|  
|-------------------------|-----------------|-------------|  
|Umgebung|Betriebssystemversion, Speicherauslastungsdaten, Prozess-ID und Name des Prozessimages. Die Umgebungsinformationen befinden sich am Anfang der TMP-Datei.|# SSIS Textual Dump taken at 9/13/2007 1:50:34 PM<br /><br /> #PID 4120<br /><br /> #Image Name [C:\Programme\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]<br /><br /> # OS major=6 minor=0 build=6000<br /><br /> # Running on 2 amd64 processors under WOW64<br /><br /> -Arbeitsspeicher: 58 % verwendet. Physische: 845M/2044 Min. Paging: 2404M/4095 Min. (Verfügbare/gesamt)|  
|Pfad und Version der Dynamic Link Library (DLL)|Pfad und Versionsnummer jeder DLL, die das System während der Verarbeitung eines Pakets lädt.|# Loaded Module: c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)<br /><br /> Anzahl geladene Modul: C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)<br /><br /> Anzahl geladene Modul: C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)|  
|Letzte Meldungen|Letzte Meldungen, die vom System ausgegeben wurden. Schließt die Zeit, Typ, Beschreibung und Thread-ID jeder Meldung ein.|[M:1]   Ring buffer entry:              (*pRecord)<br /><br /> [D:2]      <<\<CRingBufferLogging::RingBufferLoggingRecord>>> ( \@ 0282F1A8 )<br /><br /> [E:3]         Zeitstempel: 2007-09-13 13:50:32.786 (SzTimeStamp)<br /><br /> [E:3]         Thread-ID: 2368 (ThreadID)<br /><br /> [E:3]         Ereignisname: OnError (EventName)<br /><br /> [E:3]         Quellname:                (SourceName)<br /><br /> [E:3]         Datenquellen-ID:                        (SourceID)<br /><br /> [E:3]         Ausführungs-ID:                 (ExecutionGUID)<br /><br /> [E:3]         Data Code: -1073446879              (DataCode)<br /><br /> [E:3]         Beschreibung: Die Komponente fehlt, ist nicht registriert, nicht aktualisierbar, oder es fehlen erforderliche Schnittstellen. Die Kontaktinformationen für diese Komponente lauten "".|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Paket ausführen (Dialogfeld)](../execute-package-dialog-box.md)  
  
  
