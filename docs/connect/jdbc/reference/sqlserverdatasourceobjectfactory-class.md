---
title: SQLServerDataSourceObjectFactory-Klasse | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19f81b3a458ac0fa2d5e276858fcff45eeb0eb4b
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverdatasourceobjectfactory-class"></a>SQLServerDataSourceObjectFactory-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt ein Objektfactory zum Materialisieren von Datenquellen aus der JNDI (Java Naming and Directory Interface) dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** java.lang.Object  
  
 **Implementiert:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von allen Datenquellenklassen geerbt. Als Teil der Unterstützung der Referenceable-Schnittstelle [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] macht diese Klasse, die eine ObjectFactory implementiert. Java-Anwendungsservern wird für Datenquellenklassen GetReference aufrufen, und dadurch wird ein Verweisobjekt, das der Klassenname intern als Klassenfactory verwendet erstellt.  
  
 Wenn der Java-Anwendungsserver enthält, die Verweis-Objekt zu dereferenzieren, erstellt er eine Instanz der SQLServerDataSourceObjectFactory-Objekt und die Aufrufe der [GetObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) -Methode, die Verweis-Objekt zu übergeben abgerufen Sie die Datenquelleninstanz werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLServerDataSourceObjectFactory-Elemente](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [API-Referenz für JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  