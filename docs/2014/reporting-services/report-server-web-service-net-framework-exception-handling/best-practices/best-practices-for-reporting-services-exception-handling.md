---
title: Bewährte Methoden für die Ausnahmebehandlung in Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 10bf93cbaa510b9cff0cf373ada287e1aa2aea6c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034811"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Bewährte Methoden für die Ausnahmebehandlung in Reporting Services
  Wenn Sie [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Anwendungen entwickeln, können Sie verschiedene Methoden verwenden, um das Auftreten von Ausnahmezuständen zu verhindern oder zu reduzieren. Wenn Ausnahmen auftreten, sorgen Sie für klare und prägnante Fehlermeldungen, und fügen Sie eine adäquate Behandlung der Ausnahme hinzu, um unerwartete Abbrüche Ihrer Anwendungen zu verhindern.  
  
 Eine Anwendung, die Anforderungen an den Berichtsserver-Webdienst sendet, sollte wie folgt vorgehen:  
  
-   Keine Ausnahmen verursachen, indem möglichst viele ungültige Anforderungen verhindert werden.  
  
-   Abfangen von Ausnahmen und Angabe eines spezifischen Fehlerbehandlungscodes, wenn möglich.  
  
-   Behandlung von Fehlerfällen, die keine Ausnahmen auslösen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Preventing Invalid Requests (Verhindern von ungültigen Anforderungen)](preventing-invalid-requests.md)|Beschreibt Techniken, mit denen verhindert wird, dass ungültige Anforderungen zum Berichtsserver gesendet werden.|  
|[Using Try and Catch Blocks (Verwenden von Try- und Catch-Blöcken)](using-try-and-catch-blocks.md)|Beschreibt, wie die Zuverlässigkeit Ihrer Anwendung mithilfe von try/catch-Blöcken weiter verbessert wird.|  
|[Handling Warnings and Cases That Do Not Cause Exceptions (Behandeln von Warnungen und Fällen, die keine Ausnahmen verursachen)](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Erklärt, wie Fehler behandelt werden, die nicht zu einer Ausnahme führen, die von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ausgelöst wird.|  
|[Using the Detail Property to Handle Specific Errors (Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler)](using-the-detail-property-to-handle-specific-errors.md)|Erklärt, wie bestimmte Fehler programmgesteuert mit der **Detail**-Eigenschaft des **SoapException**-Objekts behandelt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Detail-Eigenschaft](../soapexception-class/detail-property.md)   
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException Class (Reporting Services-SoapException-Klasse)](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
