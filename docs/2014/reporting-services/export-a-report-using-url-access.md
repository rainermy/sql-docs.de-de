---
title: Exportieren eines Berichts über URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 589f1d42936d243bff9aa77740cefce14ab8856e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014601"
---
# <a name="export-a-report-using-url-access"></a>Exportieren von Berichten über URL-Zugriff
  Optional können Sie angeben, das Format, in dem zum Rendern eines Berichts mithilfe der *Rs: Format* Parameter. Um beispielsweise von einem im einheitlichen Modus ausgeführten Berichtsserver direkt eine PDF-Kopie eines Berichts abzurufen, geben Sie Folgendes an:  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 Zum Abrufen von einem Berichtsserver im integrierten SharePoint-Modus geben Sie Folgendes an:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 Gültige Werte für diesen Parameter sind von den Berichtrenderingerweiterungen abhängig, die auf dem Berichtsserver installiert sind, auf den zugegriffen wird. Häufig verwendete Erweiterungen sind HTML4.0, MHTML, IMAGE, EXCEL, WORD, CSV, PDF, XML und NULL. Wenn eine bestimmte Renderingerweiterung nicht auf dem Berichtsserver installiert ist, wird der Bericht nicht gerendert. Es wird ein Fehler generiert und im Browser angezeigt.  
  
 Wenn Sie den *Format* -Parameter nicht als Teil der URL aufnehmen, erkennt der Berichtsserver den Browser und rendert den Bericht im entsprechenden HTML-Format.  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL-Zugriffsparameterverweis](url-access-parameter-reference.md)  
  
  
