---
title: Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2267ff0af67682417b118e9fa01b2dceeb1454a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634748"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Ausgeben von Befehlen an den zugrunde liegenden Datenanbieter
Jeder Befehl, der nicht mit der Form beginnt wird an den Datenanbieter übergeben. Dies ist gleichbedeutend mit dem ein Shape-Befehl in der Form "Form {Anbieterbefehl}". Diese Befehle werden *nicht* erzeugen eine **Recordset**. Z. B. "ist die Form {DROP TABLE MyTable} eine absolut gültige Shape-Befehl, vorausgesetzt, dass der Datenanbieter unterstützt die DROP TABLE.  
  
 Diese Funktion ermöglicht sowohl die normalen Anbieterbefehlen als auch die Shape-Befehlen auf derselben Verbindung und Transaktion.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die datenstrukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
