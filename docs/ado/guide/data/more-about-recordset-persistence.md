---
title: Weitere Informationen zum Recordset-Beibehaltung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e626c924e7b84312877b47f811329e215f47e42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846858"
---
# <a name="more-about-recordset-persistence"></a>Weitere Informationen zur Beibehaltung von Recordsets
Das ADO-Recordset-Objekt unterstützt das Speichern von einem **Recordset** Objekt in einer Datei mithilfe der [speichern](../../../ado/reference/ado-api/save-method.md) Methode. Möglicherweise existiert, die dauerhaft gespeicherte Datei auf einem lokalen Laufwerk, Server oder als URL für eine Web site. Später kann die Datei wiederhergestellt werden, entweder mit der [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode der der **Recordset** Objekt oder die [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) -Methode der der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt.  
  
 Darüber hinaus die [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) Methode konvertiert ein **Recordset** Objekt zu einem Formular, in dem die Spalten und Zeilen mit Zeichen, die Sie angeben, getrennt sind.  
  
 Beibehalten einer **Recordset**, beginnen, indem Sie die Konvertierung in ein Formular, das in einer Datei gespeichert werden kann. **Recordset** Objekte können im proprietären erweiterte Daten TableGram (ADTG) Format oder die offenen Extensible Markup Language (XML)-Format gespeichert werden. ADTG-Beispiele werden im nächsten Abschnitt gezeigt. Weitere Informationen zu XML-Persistenz finden Sie unter [beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Alle ausstehenden Änderungen in der persistenten Datei gespeichert. Auf diese Weise können Sie eine Abfrage ausgeben, die zurückgibt eine **Recordset** -Objekt, Änderungen der **Recordset**, speichert es und die ausstehenden Änderungen, stellt später wieder her die **Recordset**, und klicken Sie dann aktualisiert die Datenquelle mit dem gespeicherten ausstehenden Änderungen.  
  
 Weitere Informationen zum dauerhaft speichern **Stream** Objekten finden Sie [Streams und Persistenz](../../../ado/guide/data/streams-and-persistence.md).  
  
 Ein Beispiel für **Recordset** Persistenz finden Sie unter den Speicherszenario für XML-Recordset.  
  
## <a name="example"></a>Beispiel  
  
### <a name="save-a-recordset"></a>Speichern eines Recordsets:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Öffnen Sie eine permanente Datei mit Recordset.Open an:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 Optional, wenn die **Recordset** verfügt nicht über eine aktive Verbindung, können Sie alle Standardeinstellungen akzeptieren und den folgenden code:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Öffnen Sie eine permanente Datei mit Connection.Execute an:  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Öffnen Sie eine permanente Datei mit RDS. DataControl:  
 In diesem Fall die **Server** Eigenschaft nicht festgelegt.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>Siehe auch  
 [GetString-Methode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)   
 [Microsoft OLE DB-Persistenz-Provider (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Streams und Persistenz](../../../ado/guide/data/streams-and-persistence.md)
