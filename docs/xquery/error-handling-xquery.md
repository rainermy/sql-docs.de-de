---
title: Fehlerbehandlung (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- static errors
- errors [XQuery]
- XQuery, error handling
- dynamic errors [XQuery]
ms.assetid: 7dee3c11-aea0-4d10-9126-d54db19448f2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 78a89ddcb27111396ec279af0b418e8490780e6a
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291336"
---
# <a name="error-handling-xquery"></a>Fehlerbehandlung (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gemäß der W3C-Spezifikation können Typfehler statisch oder dynamisch ausgelöst werden; die Spezifikation definiert statische, dynamische und Typfehler.  
  
## <a name="compilation-and-error-handling"></a>Kompilierung und Fehlerbehandlung  
 Von syntaktisch fehlerhaften XQuery-Ausdrücken und XML DML-Anweisungen werden Kompilierungsfehler zurückgegeben. In der Kompilierungsphase wird die Richtigkeit des statischen Typs von XQuery-Ausdrücken und von DML-Anweisungen überprüft, und es werden XML-Schemas für Typrückschlüsse für typisiertes XML verwendet. Es werden statische Typfehler ausgelöst, wenn ein Ausdruck aufgrund eines Verstoßes gegen die Typsicherheit zur Laufzeit fehlschlagen könnte. Beispiele für statische Fehler sind das Hinzufügen einer Zeichenfolge zu einer ganzen Zahl und das Abfragen eines nicht vorhandenen Knotens für typisierte Daten.  
  
 In Abweichung vom W3C-Standard werden XQuery-Laufzeitfehler in leere Sequenzen umgewandelt. Diese Sequenzen können je nach Aufrufkontext als leere XML-Daten oder als NULL-Wert an das Abfrageergebnis übergeben werden.  
  
 Die explizite Umwandlung in den richtigen Typ ermöglicht Benutzern das Umgehen von statischen Fehlern, obwohl dabei Laufzeitumwandlungsfehler in leere Sequenzen transformiert werden.  
  
## <a name="static-errors"></a>Statische Fehler  
 Statische Fehler werden mithilfe des [!INCLUDE[tsql](../includes/tsql-md.md)]-Fehlermechanismus zurückgegeben. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] werden XQuery-Typfehler statisch zurückgegeben. Weitere Informationen finden Sie unter [XQuery and statische Typisierung](../xquery/xquery-and-static-typing.md).  
  
## <a name="dynamic-errors"></a>Dynamische Fehler  
 In XQuery werden die meisten dynamischen Fehler einer leeren Sequenz ("()") zugeordnet. Dabei gelten die folgenden beiden Ausnahmen: Überlaufbedingungen in XQuery-Aggregatfunktionen und XML-DML-Überprüfungsfehler. Beachten Sie, dass die meisten dynamischen Fehler einer leeren Sequenz zugeordnet werden. Anderenfalls kann eine Abfrageausführung, die XML-Indizes nutzt, unerwartete Fehler auslösen. Um eine effiziente Ausführung zu ermöglichen, ohne dass unerwartete Fehler generiert werden, ordnet deshalb [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] dynamische Fehler () zu.  
  
 Wenn ein dynamischer Fehler in einem Prädikat auftritt, bedeutet das Nichtauslösen des Fehlers, dass die Semantik nicht geändert wird, weil () False zugeordnet wird. In einigen Fällen kann die Rückgabe von () statt eines dynamischen Fehlers jedoch zu unerwarteten Ergebnissen führen. Die folgenden Beispiele veranschaulichen dies.  
  
### <a name="example-using-the-avg-function-with-a-string"></a>Beispiel: Verwenden der avg()-Funktion mit einer Zeichenfolge  
 Im folgenden Beispiel die ["Avg"-Funktion](../xquery/aggregate-functions-avg.md) wird aufgerufen, um den Durchschnitt der drei Werte zu berechnen. Einer dieser Werte ist eine Zeichenfolge. Da die XML-Instanz in diesem Fall nicht typisiert ist, sind alle darin enthaltenen Daten nicht typisierte atomare Typen. Die **avg()** Funktion wandelt diese Werte zu zuerst **xs: double** bevor der Mittelwert berechnet. Allerdings den Wert `"Hello"`, kann nicht umgewandelt werden, um **xs: double** und erstellt einen dynamischen Fehler. In diesem Fall anstatt einen dynamischen Fehler, die Umwandlung von `"Hello"` zu **xs: double** bewirkt, dass eine leere Sequenz. Die **avg()** Funktion ignoriert diesen Wert, berechnet den Durchschnitt der beiden anderen Werte und gibt 150 zurück.  
  
```  
DECLARE @x xml  
SET @x=N'<root xmlns:myNS="test">  
 <a>100</a>  
 <b>200</b>  
 <c>Hello</c>  
</root>'  
SELECT @x.query('avg(//*)')  
```  
  
### <a name="example-using-the-not-function"></a>Beispiel: Verwenden der not-Funktion  
 Bei Verwendung der [funktionieren nicht](../xquery/functions-on-boolean-values-not-function.md) in einem Prädikat, z. B. `/SomeNode[not(Expression)]`, und der Ausdruck bewirkt einen dynamischen Fehler, eine leere Sequenz zurückgegeben statt eines Fehlers. Anwenden von **"NOT()" "** in die leere Sequenz gibt True zurück, statt eines Fehlers.  
  
### <a name="example-casting-a-string"></a>Beispiel: Umwandeln einer Zeichenfolge  
 Im folgenden Beispiel wird die Literalzeichenfolge "NaN" zuerst in xs:string und dann in xs:double umgewandelt. Das Ergebnis ist ein leeres Rowset. Die Zeichenfolge "NaN" kann nicht erfolgreich in xs:double umgewandelt werden; dies wird jedoch erst zur Laufzeit bestimmt, weil die Zeichenfolge zuerst in xs:string umgewandelt wird.  
  
```  
DECLARE @x XML  
SET @x = ''  
SELECT @x.query(' xs:double(xs:string("NaN")) ')  
GO  
```  
  
 In diesem Beispiel tritt jedoch ein statischer Typfehler auf.  
  
```  
DECLARE @x XML  
SET @x = ''  
SELECT @x.query(' xs:double("NaN") ')  
GO  
```  
  
#### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die **Fn:error()** Funktion wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [XQuery Basics (XQuery-Grundlagen)](../xquery/xquery-basics.md)  
  
  
