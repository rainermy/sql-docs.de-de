---
title: Cellset-Objekt (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57b570b93d4e8a6cf10d879659f0886e1c6f0c8e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601668"
---
# <a name="cellset-object-ado-md"></a>Cellset-Objekt (ADO MD)
Stellt die Ergebnisse einer MDX-Abfrage. Es ist eine Auflistung von Zellen, die aus Cubes oder anderen Cellsets ausgewählt.  
  
## <a name="remarks"></a>Hinweise  
 Daten in einem **Cellset** wird mit der direkten, arrayähnlichen Zugriff abgerufen. Sie können auf einen bestimmten Member zum Abrufen von Daten über diesen Member anzeigen. Beispielsweise der folgende Code gibt die Beschriftung des ersten Elements in der ersten Position auf der ersten Achse eines cellSets, die mit dem Namen `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Hinweise  
 Es gibt kein Konzept einer aktuellen Zelle innerhalb eines cellSets dar. Stattdessen die [Element](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) Eigenschaft ruft eine bestimmte [Zelle](../../../ado/reference/ado-md-api/cell-object-ado-md.md) Objekt aus dem Cellset. Die Argumente der **Element** -Eigenschaft fest, welche Zelle abgerufen wird. Sie können den eindeutigen Wert einer Zelle angeben. Sie können auch den Zellen abrufen, mithilfe von ihrer Positionsnummern an jeder Achse, der das Cellset. Weitere Informationen zum Abrufen von Zellen finden Sie unter den [Element](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) Eigenschaft.  
  
 Mit den Auflistungen, Methoden und Eigenschaften einer **Cellset** -Objekts können Sie folgende Möglichkeiten:  
  
-   Ordnen Sie eine offene Verbindung mit einem **Cellset** Objekt durch Festlegen seiner [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) Eigenschaft.  
  
-   Ausführen und zum Abrufen der Ergebnisse einer MDX-Abfrage mit der [öffnen](../../../ado/reference/ado-md-api/open-method-ado-md.md) Methode.  
  
-   Abrufen einer **Zelle** aus der **Cellset** mit der [Element](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) Eigenschaft.  
  
-   Zurückgeben der [Achse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) Objekte, die definieren, die **Cellset** mit der [Achsen](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) Auflistung.  
  
-   Abrufen von Informationen zu den Dimensionen zum Filtern von Daten in die **Cellset** mit der [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben, oder geben Sie die Abfrage, die zum Definieren der **Cellset** mit der [Quelle](../../../ado/reference/ado-md-api/source-property-ado-md.md) Eigenschaft.  
  
-   Zurückgeben des aktuellen Status von der **Cellset** (geöffnet, geschlossen, ausführen oder eine Verbindung herstellen) mit der [Zustand](../../../ado/reference/ado-md-api/state-property-ado-md.md) Eigenschaft.  
  
-   Schließen Sie eine offene **Cellset** mit der [schließen](../../../ado/reference/ado-md-api/close-method-ado-md.md) Methode.  
  
-   Anbieterspezifische Informationen zum Abrufen der **Cellset** mit dem standard-ADO [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Cellset-Beispiel (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Die Achsenauflistung (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Cell-Objekt (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Properties-Collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
