---
title: HumanResources.myTeam-Beispieltabelle (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2605b777e4cb7adfbf04ee0ebace0e76868b8a98
ms.sourcegitcommit: ef15fa253d98c62538bf9b6fe191af7f8ef8f6c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49991155"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>HumanResources.myTeam-Beispieltabelle (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Viele der Codebeispiele in [Importieren und Exportieren von Massendaten](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) erfordern eine besondere Testtabelle namens **myTeam**. Bevor Sie die Beispiele ausführen können, müssen Sie die **myTeam** -Tabelle im **HumanResources** -Schema der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank erstellen.  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ist eine der Beispieldatenbanken in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Die Tabelle **myTeam** enthält die folgenden Spalten.  
  
|Spalte|Datentyp|NULL-Zulässigkeit|und Beschreibung|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|**smallint**|Nicht NULL|Primärschlüssel für die Zeilen. Mitarbeiter-ID eines Mitglieds meines Teams.|  
|**Name**|**nvarchar(50)**|Nicht NULL|Name eines Mitglieds meines Teams.|  
|**Title**|**nvarchar(50)**|NULL zulassen|Titel des Mitarbeiters in meinem Team.|  
|**Hintergrund**|**nvarchar(50)**|Nicht NULL|Datum und Uhrzeit des letzten Updates der Zeile. (Standardwert)|  
  
**So erstellen Sie HumanResources.myTeam**  
  
-   Verwenden Sie die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen:  
  
    ```sql
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
**So füllen Sie HumanResources.myTeam auf**  
  
-   Führen Sie die folgenden `INSERT` -Anweisungen zum Auffüllen der Tabelle mit zwei Zeilen aus:  
  
    ```sql
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  Bei diesen Anweisungen wird die vierte Spalte ( `Background`) ausgelassen. Diese besitzt einen Standardwert. Das Auslassen dieser Spalte bewirkt, dass diese Spalte bei der `INSERT` -Anweisung leer bleibt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Massenimport und -export von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
