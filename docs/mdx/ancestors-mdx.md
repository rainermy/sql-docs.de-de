---
title: Vorgänger (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0c108ea102e03000481d18bfc69f657e6bd8a0ce
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740049"
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)


  Eine Funktion, die die Menge aller Vorgänger eines angegebenen Elements in einer angegebenen Ebene oder in einem angegebenen Abstand vom Element zurückgibt. Mit [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], die zurückgegebene Menge stets ein einzelnes Element – [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt nicht mehrere übergeordnete Elemente für ein einzelnes Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Abstand*  
 Ein gültiger numerischer Ausdruck, der den Abstand vom angegebenen Element angibt.  
  
## <a name="remarks"></a>Hinweise  
 Mit der **Vorgänger** -Funktion, Sie stellen die Funktion einen MDX-Elementausdruck bereit und anschließend entweder einen MDX-Ausdruck einer Ebene, die sich um einen Vorgänger dieses Elements oder eines numerischen Ausdrucks, der die Anzahl der Ebenen oberhalb dieses Elements darstellt. Anhand dieser Informationen die **Vorgänger** Funktion gibt die Menge der Elemente (die einen Satz bestehend aus einem Element) auf dieser Ebene zurück.  
  
> [!NOTE]  
>  Um zurückzugeben, verwenden Sie ein Vorgängerelement, anstatt einen Satz Vorgänger der [Vorgänger](../mdx/ancestor-mdx.md) Funktion.  
  
 Wenn ein Ebenenausdruck angegeben wird, die **Vorgänger** -Funktion die Menge aller Vorgänger eines angegebenen Elements auf der angegebenen Ebene zurück. Wenn das angegebene Element nicht in derselben Hierarchie wie der angegebenen Ebene ist, gibt die Funktion einen Fehler aus.  
  
 Wenn ein Abstand angegeben ist, die **Vorgänger** -Funktion die Menge aller Elemente, die die Anzahl der Schritte, die gemäß der von der im Elementausdruck angegebenen Hierarchie zurück. Ein Element kann als ein Element einer Attributhierarchie, eine benutzerdefinierte Hierarchie oder in einigen Fällen eine über-/ unterordnungshierarchie angegeben werden. 1 gibt die Menge der Elemente auf der übergeordneten Ebene und 2 die Menge der Elemente auf der dieser Ebene übergeordneten Ebene (sofern vorhanden) zurück. 0 gibt die Menge zurück, die nur das Element selbst enthält.  
  
> [!NOTE]  
>  Verwenden Sie dieses Formular von der **Vorgänger** -Funktion in Fällen, in dem die Ebene des übergeordneten Elements ist unbekannt oder nicht benannt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die **Vorgänger** Funktion, um die Internet Sales Amount-Measure für ein Element, die das übergeordnete Element und das diesem übergeordnete Element zurückzugeben. In diesem Beispiel werden Ebenenausdrücke zum Angeben der zurückzugebenden Ebene verwendet. Die Ebenen befinden sich in der gleichen Hierarchie wie das im Elementausdruck angegebene Element.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Vorgänger** Funktion, um die Internet Sales Amount-Measure für ein Element, die das übergeordnete Element und das diesem übergeordnete Element zurückzugeben. In diesem Beispiel werden numerische Ausdrücke zum Angeben der zurückzugebenden Ebene verwendet. Die Ebenen befinden sich in der gleichen Hierarchie wie das im Elementausdruck angegebene Element.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 Im folgenden Beispiel wird die **Vorgänger** Funktion, um das Internet Sales Amount-Measure für das übergeordnete Element eines Elements der Attributhierarchie zurückzugeben. In diesem Beispiel wird ein numerischer Ausdruck zum Angeben der zurückzugebenden Ebene verwendet. Da das Element im Elementausdruck ein Element einer Attributhierarchie darstellt, ist das ihm übergeordnete Element die [All]-Ebene.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
