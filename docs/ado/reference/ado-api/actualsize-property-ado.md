---
title: ActualSize-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4676f1d0a9d96779303898631164101bbdc4201d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752908"
---
# <a name="actualsize-property-ado"></a>ActualSize-Eigenschaft (ADO)
Gibt die tatsächliche Länge der der Wert eines Felds in Bytes an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Gibt eine **lange** Wert.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **ActualSize** zurückzugebende die tatsächliche Länge der Eigenschaft ein [Feld](../../../ado/reference/ado-api/field-object.md) Wert des Objekts. Für alle Felder der **ActualSize** Eigenschaft ist schreibgeschützt. Wenn die Länge des ADO ermittelt werden kann die **Feld** Wert des Objekts, das **ActualSize** -Eigenschaft gibt **ActualSize**.  
  
 Die **ActualSize** und [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) Eigenschaften unterschiedlich sind, wie im folgenden Beispiel gezeigt. Ein **Feld** Objekt mit dem deklarierten Typ **AdVarChar** und eine maximale Länge von 50 Zeichen gibt eine **DefinedSize** Eigenschaftswert von 50 jedoch  **ActualSize** Eigenschaftswert zurückgegeben wird, die Länge der Daten in das Feld für den aktuellen Datensatz gespeichert. **Felder** mit einem **DefinedSize** größer als 255 Byte als Spalten variabler Länge behandelt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ActualSize und DefinedSize – Beispiel (VB)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [ActualSize und DefinedSize – Beispiel (VC++)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [DefinedSize-Eigenschaft](../../../ado/reference/ado-api/definedsize-property.md)
