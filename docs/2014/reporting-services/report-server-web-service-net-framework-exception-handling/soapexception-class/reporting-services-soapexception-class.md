---
title: SoapException-Klasse von Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ac8b0b7a36cc3ecff37ba0d74167b99458eb5e77
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027200"
---
# <a name="reporting-services-soapexception-class"></a>Reporting Services-SoapException-Klasse
  Sie sollten bestimmte [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Fehler angeben, die erfahrungsgemäß auftreten können. In einer Anwendung, in der Sie den Benutzer auffordern, einen Ordner zu erstellen, kann es beispielsweise passieren, dass der Benutzer einen Ordner erstellen möchte, der bereits vorhanden ist. Als Entwickler können Sie nicht steuern, welchen Ordnernamen und welches Verzeichnis der Benutzer in der Anwendung angibt. Allerdings können Sie steuern, was passieren soll, wenn jemand ein Element erstellen möchte, das bereits vorhanden ist.  
  
 Um bestimmte Fehlerbedingungen leichter zu erfassen, klassifiziert [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] einen Fehlercode für die Ausnahme und gibt die Fehlerklassifizierung mithilfe der Eigenschaften aus der **SoapException**-Klasse zurück. Weitere Informationen finden Sie unter „SoapException-Klasse“ in der Dokumentation zum [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
 In der folgenden Tabelle sind die öffentlichen Eigenschaften der **SoapException**-Klasse aufgeführt.  
  
|Öffentliche Eigenschaft|Description|  
|---------------------|-----------------|  
|**Actor**|Der Code, der die Ausnahme verursacht hat. Der Wert ist die URL der Webdienstmethode.|  
|**Detail**|Anwendungsspezifische Fehlerinformationen. Der Wert wird vom Berichtsserver festgelegt und ist im XML-Format. Weitere Informationen finden Sie unter [Detail-Eigenschaft](detail-property.md) und [Verwenden der Detail-Eigenschaft zur Handhabung bestimmter Fehler](../best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|Eine URL oder eine URN zu einer zum Fehler gehörigen Hilfedatei. Der Wert wird normalerweise durch einen Webdienst festgelegt, und er richtet eine URL zu [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Hilfe und Support ein. Da [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] mehrere HelpLinks für auftretende Fehler unterstützt, richtet der Berichtsserver die HelpLink-Informationen als Teil der **Detail**-Eigenschaft ein. Weitere Informationen finden Sie unter [HelpLink-Element](helplink-element.md).|  
|**MessageBox**|Eine informative, lokalisierte Meldung, die den Fehler beschreibt. Dieser Text kann in der Benutzeroberfläche der Anwendung angezeigt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException Errors Table (Tabelle für SoapException-Fehler)](soapexception-errors-table.md)  
  
  
