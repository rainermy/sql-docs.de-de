---
title: Clientseitiger und Serverseitige XML-Formatierung (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cd9f76b11edf684c68658f040b4aa3e0f63727d4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028831"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a>Clientseitiger und Serverseitige XML-Formatierung (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Thema werden die allgemeinen Unterschiede zwischen clientseitiger und serverseitiger XML-Formatierung in SQLXML beschrieben.  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a>Keine Unterstützung von mehreren Rowset-Abfragen bei der clientseitigen Formatierung  
 Abfragen, die mehrere Rowsets generieren, werden bei einer clientseitigen XML-Formatierung nicht unterstützt. Beispiel: Sie haben ein virtuelles Verzeichnis, für das eine clientseitige Formatierung angegeben wurde. Erwägen Sie diese Beispielvorlage mit zwei SELECT-Anweisungen in einem  **\<SQL: Query >** blockieren:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 Sie können diese Vorlage im Anwendungscode ausführen, es wird ein Fehler zurückgegeben, da die clientseitige XML-Formatierung keine Formatierung mehrerer Rowsets unterstützt. Bei Angabe von Abfragen in zwei separate  **\<SQL: Query >** Blöcken, erhalten Sie die gewünschten Ergebnisse.  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a>Unterschiedliche timestamp-Zuordnungen bei der client- und serverseitigen Formatierung  
 In der serverseitigen XML-Formatierung, die Datenbankspalte des **Zeitstempel** Geben Sie mit dem i8 XDR-Datentyp (wenn die XMLDATA-Option in der Abfrage angegeben ist).  
  
 In Client-Side-XML-Formatierung, die Datenbankspalte des **Zeitstempel** geben Zuordnungen, die entweder die **Uri** oder **bin. Base64** XDR-Typ (je nachdem, ob die binary base64 Option ist in der Abfrage angegeben). Die **bin. Base64** XDR-Typ ist nützlich, wenn Sie die updategram- und Bulkload-Funktionen verwenden, da dieser Typ konvertiert wird, auf die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Zeitstempel** Typ. Auf diese Art werden die Einfüge-, Update- oder Löschvorgänge erfolgreich abgeschlossen.  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a>Bei serverseitiger Formatierung werden tiefe VARIANTs verwendet  
 Bei der serverseitigen XML-Formatierung werden tiefe Typen eines VARIANT-Typs verwendet. Bei der clientseitigen XML-Formatierung werden die Varianten in Unicode-Zeichenfolgen konvertiert und die Untertypen von VARIANT werden nicht verwendet.  
  
## <a name="nested-mode-vs-auto-mode"></a>NESTED-Modus im Vergleich zum AUTO-Modus.  
 Der NESTED-Modus des clientseitigen FOR XML ähnelt dem AUTO-Modus des serverseitigen FOR XML. Ausnahmen:  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a>Wenn Sie Sichten mit AUTO-Modus serverseitig abfragen, wird der Sichtname als Elementname in der resultierenden XML zurückgegeben.  
 Nehmen wir beispielsweise an, dass die folgende Ansicht für die Person.Contact-Tabelle in der AdventureWorksdatabase erstellt wird:  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 Die folgende Vorlage gibt eine Abfrage der ContactView-Sicht und die serverseitige XML-Formatierung an:  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Wenn Sie die Vorlage ausführen, wird die folgende XML zurückgegeben. (Es werden nur partielle Ergebnisse angezeigt.) Beachten Sie, dass die Elementnamen die Namen der Sichten sind, für die die Abfrage ausgeführt wird.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 Wenn Sie die clientseitige XML-Formatierung mit dem entsprechenden NESTED-Modus angeben, werden die Basistabellennamen als Elementnamen in der resultierenden XML zurückgegeben. Z. B. die folgende überarbeitete Vorlage führt dieselbe SELECT-Anweisung, aber die XML-Formatierung wird auf der Clientseite ausgeführt (d. h. **Client-Side-XML-** nastaven NA hodnotu in der Vorlage "true"):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Durch die Ausführung der Vorlage wird die folgende XML erstellt. Beachten Sie, dass in diesem Fall der Elementname der Basistabellenname ist.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a>Wenn Sie den AUTO-Modus des serverseitigen FOR XML verwenden, werden die in der Abfrage angegebenen Tabellenaliasse als Elementnamen in der resultierenden XML zurückgegeben.  
 Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Durch die Ausführung der Vorlage wird die folgende XML erstellt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 Wenn Sie den NESTED-Modus des clientseitigen FOR XML verwenden, werden die Tabellennamen als Elementnamen in der resultierenden XML zurückgegeben. (Tabellenaliasse, die in der Abfrage angegeben werden, werden nicht verwendet.) Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Durch die Ausführung der Vorlage wird die folgende XML erstellt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a>Wenn eine Abfrage Spalten als dbobject-Abfragen zurückgibt, können Sie keine Aliasse für diese Spalten verwenden.  
 Die folgende Vorlage führt beispielsweise eine Abfrage aus, die eine Mitarbeiter-ID und ein Foto zurückgibt.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 Wenn Sie diese Vorlage ausführen, wird die Photo-Spalte als eine dbobject-Abfrage zurückgegeben. In dieser dbobject-Abfrage verweist `@P` auf einen Spaltennamen, der nicht existiert.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 Wenn die XML-Formatierung auf dem Server ausgeführt wird (**Client-Side-Xml = "0"**), können Sie den Alias für die Spalten, die Dbobject-Abfragen in der tatsächlichen Tabelle und Spalte Namen zurückgegeben werden (selbst wenn Sie Aliasse angegeben haben) zurückgeben. Z. B. die folgende Vorlage führt eine Abfrage, und die XML-Formatierung auf dem Server erfolgt (der **Client-Side-XML-** Option nicht angegeben und die **ausführen auf Client** ausgewählt ist nicht für die Virtueller Stamm). Die Abfrage gibt auch den AUTO-Modus an (nicht den clientseitigen NESTED-Modus).  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 Wenn diese Vorlage ausgeführt wird, wird das folgende XML-Dokument zurückgegeben (beachten Sie, dass die Aliasse nicht in der dbobject-Abfrage für die LargePhoto-Spalte verwendet werden):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a>Clientseitiger und serverseitiger XPath  
 Clientseitiger XPath und serverseitiger XPath funktionieren gleichermaßen, weisen jedoch die folgenden Unterschiede auf:  
  
-   Die Datenkonvertierungen, die angewendet werden, wenn Sie clientseitige XPath-Abfragen verwenden, unterscheiden sich von jenen, die angewendet werden, wenn Sie serverseitige XPath-Abfragen verwenden. Clientseitiger XPath verwendet CAST anstelle von CONVERT-Modus 126.  
  
-   Beim Angeben von **Client-Side-Xml = "0"** (false) ist in einer Vorlage, fordern Sie eine serverseitige XML-Formatierung. Sie können somit nicht FOR XML NESTED angeben, da der Server die NESTED-Option nicht erkennt. In diesem Fall wird ein Fehler generiert. Sie müssen die Modi AUTO, RAW oder EXPLICIT verwenden, die der Server erkennt.  
  
-   Beim Angeben von **Client-Side-Xml = "1"** (true) in einer Vorlage, fordern Sie eine Client-Side-XML-Formatierung. In diesem Fall können Sie FOR XML NESTED angeben. Wenn Sie FOR XML AUTO angeben, die XML-Formatierung tritt auf, auf dem Server zwar **Client-Side-Xml = "1"** in der Vorlage angegeben ist.  
  
## <a name="see-also"></a>Siehe auch  
 [FOR XML-Sicherheitsüberlegungen &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [Die clientseitige XML-Formatierung &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [Serverseitige XML-Formatierung &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/server-side-xml-formatting-sqlxml-4-0.md)  
  
  
