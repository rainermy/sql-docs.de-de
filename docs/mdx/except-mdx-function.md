---
title: Mit Ausnahme der (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 03d9b5140eb0cbf9d868e43c65213efe917994a9
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739999"
---
# <a name="except-mdx-function"></a>EXCEPT-Funktion (MDX)


  Wertet zwei Mengen aus und entfernt die Tupel in der ersten Menge, die auch in der zweiten Menge vorhanden sind. Optional werden doppelte Werte beibehalten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Except(Set_Expression1, Set_Expression2 [, ALL ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn **alle** wird angegeben, die die Funktion in der ersten Menge gefundene doppelte Werte beibehalten; in der zweiten Menge gefundene doppelte Werte werden dennoch entfernt. Die Elemente werden entsprechend ihrer Reihenfolge in der ersten Menge zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieser Funktion.  
  
```  
   //This query shows the quantity of orders for all products,  
   //with the exception of Components, which are not  
   //sold.  
SELECT   
   [Date].[Month of Year].Children  ON COLUMNS,  
   Except  
      ([Product].[Product Categories].[All].Children ,  
         {[Product].[Product Categories].[Components]}  
      ) ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   ([Measures].[Order Quantity])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [- &#40;Außer&#41; &#40;MDX&#41;](../mdx/except-mdx-operator.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
