---
title: Verwenden von gespeicherten Prozeduren (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0d4d455ed7bd804f4c2d4ce036c00f85fd94629f
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148180"
---
# <a name="using-stored-procedures-mdx"></a>Verwenden von gespeicherten Prozeduren (MDX)


  Sie können die Funktionalität von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und Multidimensional Expressions (MDX) erweitern, indem sie mit .NET gespeicherte Prozeduren oder benutzerdefinierte Funktionen erstellen. Weitere Informationen finden Sie unter [ADOMD.NET Server-Programmierung](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
 Wenn Sie auf eine gespeicherte Prozedur verweisen bzw. eine gespeicherte Prozedur aufrufen, geben Sie den Namen der Prozedur und dahinter Klammern an. In den Klammern können Sie Ausdrücke angeben. Diese Ausdrücke werden als Argumente bezeichnet und stellen die Daten bereit, die an die Parameter zu übergeben sind. Wenn Sie eine Funktion aufrufen, müssen Sie Argumentwerte für alle Parameter bereitstellen und die Argumentwerte in derselben Reihenfolge angeben, in der die Parameter in der benutzerdefinierten Funktion definiert sind.  
  
 Die folgende Beispielabfrage geht davon aus, dass Sie über eine auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server registrierte Assembly mit dem Namen SampleAssembly verfügen:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *Gespeicherte Prozedur* -Terminologie ist [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] für diese Arten von Funktionen. Frühere Versionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] wird aufgerufen, diese Arten von Funktionen als *benutzerdefinierte Funktionen*.  
  
## <a name="types-of-stored-procedures"></a>Arten von gespeicherten Prozeduren  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt sowohl COM- als auch CLR-Assemblys. CLR-Assemblys empfehlen sich wegen der für sie verfügbaren verbesserten Sicherheit. Wenn Microsoft Office Excel auf dem Server installiert ist, sind auch die Excel-Funktionen verfügbar.  
  
> [!NOTE]  
>  COM-Assemblys von Microsoft Visual Basic für Applikationen (VBA) werden automatisch registriert.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)  
  
  
