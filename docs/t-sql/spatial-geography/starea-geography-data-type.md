---
title: STArea (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb8e33e7f27315871948c5fd7e6915242cc0a339
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643878"
---
# <a name="starea-geography-data-type"></a>STArea (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt die gesamte Oberfläche einer **geography**-Instanz zurück. Ergebnisse für STArea() werden als Quadrat der vom SRID (Spatial Reference Identifier) der **geography**-Instanz verwendeten Maßeinheit zurückgegeben. Wenn der SRID der Instanz beispielsweise 4326 lautet, gibt STAreal() Ergebnisse in Quadratmetern zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **float**  
  
 CLR-Rückgabetyp: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 STArea() gibt 0 (null) zurück, wenn eine **geography**-Instanz nur null- und eindimensionale Abbildungen enthält oder leer ist.  
  
> [!NOTE]  
>  Methoden für den **geography**-Datentyp, die einen metrischen Rückgabewert erzeugen, liefern unterschiedliche Ergebnisse, abhängig vom SRID der in der jeweiligen Methode verwendeten Instanz. Weitere Informationen über SRIDs finden Sie unter [SRIDs &#40;Spatial Reference Identifiers&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mithilfe von `STArea()` eine `Polygon``geography`-Instanz erstellt und dann der Bereich des Polygons berechnet.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
