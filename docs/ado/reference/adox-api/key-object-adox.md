---
title: Key-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7365b3ac33f215840a112089523f23e88697a433
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626728"
---
# <a name="key-object-adox"></a>Key-Objekt (ADOX)
Stellt ein primärer, Fremdschlüssel oder eindeutiger Schlüsselfeld aus einer Datenbanktabelle dar.  
  
## <a name="remarks"></a>Hinweise  
 Der folgende Code erstellt ein neues **Schlüssel**:  
  
```  
Dim obj As New Key  
```  
  
 Mit den Eigenschaften und Auflistungen von einem **Schlüssel** Objekt ist, können Sie:  
  
-   Den Schlüssel mit dem Identifizieren der [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Bestimmt, ob die primäre, Fremdschlüssel oder eindeutig ist die [Typ](../../../ado/reference/adox-api/type-property-key-adox.md) Eigenschaft.  
  
-   Zugreifen auf die Datenbankspalten des Schlüssels mit dem [Spalten](../../../ado/reference/adox-api/columns-collection-adox.md) Auflistung.  
  
-   Geben Sie den Namen der verknüpften Tabelle mit den [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) Eigenschaft.  
  
-   Bestimmen Sie die Aktion ausgeführt, die beim Löschen oder Aktualisieren eines primären Schlüssels mit dem [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) und [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) Eigenschaften.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Key-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Keys Append-Methode, Typ des Schlüssels, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Keys Collection (ADOX) (Keys-Auflistung (ADOX))](../../../ado/reference/adox-api/keys-collection-adox.md)
