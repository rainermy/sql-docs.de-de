---
title: Verwenden von OPENJSON mit dem Standardschema (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 078f198d81c0fc9de1ce5c0a6221b54c253bfa56
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56033416"
---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>Verwenden von OPENJSON mit dem Standardschema (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Verwenden Sie **OPENJSON** mit dem Standardschema, um eine Tabelle mit einer Zeile für jede Eigenschaft des Objekts oder für jedes Element im Array zurückzugeben.  
  
 Hier ein paar Beispiele, in denen **OPENJSON** mit dem Standardschema verwendet wird. Weitere Informationen und Beispiele finden Sie unter [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md).  
  
## <a name="example---return-each-property-of-an-object"></a>Beispiel: Rückgabe jeder Eigenschaft eines Objekts  
 **Dataseteigenschaften**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **Ergebnisse**  
  
|Key|value|  
|---------|-----------|  
|NAME|John|  
|surname|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>Beispiel: Rückgabe jedes Element eines Arrays  
 **Dataseteigenschaften**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **Ergebnisse**  
  
|Key|value|  
|---------|-----------|  
|0|en-GB|  
|1|en-UK|  
|2|de-AT|  
|3|es-AR|  
|4|sr-Cyrl|  
  
## <a name="example---convert-json-to-a-temporary-table"></a>Beispiel: Konvertieren von JSON in eine temporäre Tabelle  
 Die folgende Abfrage gibt alle Eigenschaften des **info** -Objekts zurück.  
  
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }'

SELECT *
FROM OPENJSON(@json,N'lax $.info')
```  
  
 **Ergebnisse**  
  
|Key|value|Typ|  
|---------|-----------|----------|  
|Typ|1|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|Transponder|[ "Sport", "Water polo" ]|4|  
  
## <a name="example---combine-relational-data-and-json-data"></a>Beispiel: Kombinieren relationale Daten und JSON-Daten  
 Im folgenden Beispiel hat die SalesOrderHeader-Tabelle eine SalesReason-Textspalte, die ein Array von SalesOrderReasons im JSON-Format enthält. Die SalesOrderReasons-Objekte enthalten Eigenschaften, z.B. „Manufacturer“ und „Quality“. Das Beispiel erstellt einen Bericht, der jede Zeile der Bestellung und die zugehörigen Verkaufsgründe verknüpft, indem das JSON-Array von Verkaufsgründe erweitert wird, als wären die Gründe in einer separaten untergeordneten Tabelle gespeichert.  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
 In diesem Beispiel gibt OPENJSON eine Tabelle mit Verkaufsgründen zurück, in denen die Gründe als Wertspalte angezeigt werden. Der CROSS APPLY-Operator verknüpft jede Verkaufszeile der Bestellung mit den von der OPENJSON-Tabellenwertfunktion zurückgegebenen Zeilen.  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Weitere Informationen  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
