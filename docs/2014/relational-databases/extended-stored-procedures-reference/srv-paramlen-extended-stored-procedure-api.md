---
title: srv_paramlen (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2c858d0fa8579aff288efd7026ab4b65035bad8d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53364706"
---
# <a name="srvparamlen-extended-stored-procedure-api"></a>srv_paramlen (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt die Datenlänge des Aufrufparameters für eine remote gespeicherte Prozedur zurück. Diese Funktion wurde durch die **srv_paraminfo**-Funktion ersetzt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*   
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das den Aufruf der remote gespeicherten Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *n*  
 Gibt die Anzahl der Parameter an. Der erste Parameter ist 1.  
  
## <a name="returns"></a>Rückgabewert  
 Die tatsächliche Länge der Parameterdaten in Byte. Wenn es keinen *n*-ten Parameter gibt, oder wenn es keine remote gespeicherte Prozedur gibt, wird –1 zurückgegeben. Wenn der *n*-te Parameter NULL ist, wird 0 zurückgegeben.  
  
 Diese Funktion gibt die folgenden Werte zurück, wenn der Parameter einem der folgenden Systemdatentypen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] entspricht.  
  
|Neue Datentypen|Länge der Eingabedaten|  
|--------------------|-----------------------|  
|`BITN`|**NULL:** 1<br /><br /> **0 (NULL):** 1<br /><br /> **> = 255:** Nicht zutreffend<br /><br /> **< 255:** Nicht zutreffend|  
|`BIGVARCHAR`|**NULL:** 0<br /><br /> **0 (NULL):** 1<br /><br /> **> = 255:** 255<br /><br /> **<255:** tatsächlicher *len*-Wert|  
|`BIGCHAR`|**NULL:** 0<br /><br /> **0 (NULL):** 255<br /><br /> **> = 255:** 255<br /><br /> **< 255:** 255|  
|`BIGBINARY`|**NULL:** 0<br /><br /> **0 (NULL):** 255<br /><br /> **> = 255:** 255<br /><br /> **< 255:** 255|  
|`BIGVARBINARY`|**NULL:** 0<br /><br /> **0 (NULL):** 1<br /><br /> **> = 255:** 255<br /><br /> **<255:** tatsächlicher *len*-Wert|  
|`NCHAR`|**NULL:** 0<br /><br /> **0 (NULL):** 255<br /><br /> **> = 255:** 255<br /><br /> **< 255:** 255|  
|`NVARCHAR`|**NULL:** 0<br /><br /> **0 (NULL):** 1<br /><br /> **> = 255:** 255<br /><br /> **<255:** tatsächlicher *len*-Wert|  
|`NTEXT`|**NULL:** –1<br /><br /> **ZERO:** –1<br /><br /> **>=255:** –1<br /><br /> **< 255:** -1|  
  
 \* tatsächlicher *len*-Wert = Länge von Mehrbyte-Zeichenfolgen (cch)  
  
## <a name="remarks"></a>Hinweise  
 Parameter einer remote gespeicherten Prozedur haben eine tatsächliche und eine maximale Datenlänge. Bei Standarddatentypen fester Länge, die keine Nullwerte zulassen, ist die tatsächliche Länge mit der maximalen Länge identisch. Bei Datentypen variabler Länge können die Längen unterschiedlich sein. Ein als `varchar(30)` deklarierter Parameter kann beispielsweise über Daten verfügen, die nur 10 Byte lang sind. Die tatsächliche Länge des Parameters ist 10, die maximale Länge jedoch 30. Die **srv_paramlen**-Funktion ruft die tatsächliche Datenlänge einer remote gespeicherten Prozedur in Byte ab. Zum Abrufen der maximalen Datenlänge eines Parameters verwenden Sie **srv_parammaxlen**.  
  
 Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherten Prozedur einige Parameter über ihren Namen und andere über ihre Position übergeben, so tritt ein Fehler auf. Der SRV_RPC-Handler wird trotzdem aufgerufen, doch es sind scheinbar keine Parameter vorhanden, und **srv_rpcparams** gibt 0 zurück.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Siehe auch  
 [srv_paraminfo (API für erweiterte gespeicherte Prozeduren)](srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams (API für erweiterte gespeicherte Prozeduren)](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
