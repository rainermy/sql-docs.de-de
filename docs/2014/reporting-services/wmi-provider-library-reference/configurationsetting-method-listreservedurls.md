---
title: 'ListReservedURLs-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d86fc709f3cc322c17514309906355cc4489876e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012351"
---
# <a name="listreservedurls-method-wmi-msreportserverconfigurationsetting"></a>ListReservedURLs-Methode (WMI: MSReportServer_ConfigurationSetting)
  Listet für alle Anwendungen auf dem Berichtsserver reservierte URLs auf  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *Application[]*  
 [out] Die Anwendungen, die URL-Reservierungen aufweisen  
  
 *UrlString[]*  
 [out] Die URLs, die reserviert sind  
  
 *Account[]*  
 [out] Die mit dem Konto für die URL-Reservierungen verknüpften Kontonamen  
  
 *AccountSID[]*  
 [out] Die mit dem Konto für die URL-Reservierungen verknüpften Konto-SIDs  
  
 *Länge*  
 [out] Die Länge der von der Methode zurückgegebenen Arrays  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Fehlercode gibt an, dass der Aufruf nicht erfolgreich war.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
