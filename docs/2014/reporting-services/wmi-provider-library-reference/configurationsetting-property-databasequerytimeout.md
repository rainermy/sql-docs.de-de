---
title: 'DatabaseQueryTimeout-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: cf21ba6211a016676ea7d1f2547bf4d96b1e6fb4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023762"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>DatabaseQueryTimeout-Eigenschaft (WMI: MSReportServer_ConfigurationSetting)
  Gibt die Anzahl von Sekunden an, die verstreichen müssen, ehe der Berichtsserver annimmt, dass der Befehl fehlgeschlagen ist oder die Ausführungszeit zu lang war. Der Berichtsserver nimmt die zeitliche Steuerung der Abfrage anhand des SQL-Katalogs und nicht anhand einer Datenquelle für den Bericht vor. Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein 32-Bit-`integer`-Objekt ohne Vorzeichen, das die Anzahl der Sekunden darstellt, die für die Ausführung der Abfrage erlaubt sind  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting-Klasse](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
