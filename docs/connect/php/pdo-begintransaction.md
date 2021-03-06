---
title: 'PDO:: BeginTransaction | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c3e4fc0dce4b712d1a7bea39f0b69f605d68fcb9
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606620"
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Schaltet den Autocommit-Modus aus und beginnt eine Transaktion.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>Rückgabewert  
„true“, bei erfolgreichem Aufruf der Methode; andernfalls „false“.  
  
## <a name="remarks"></a>Remarks  
Die Transaktion, die mit PDO::beginTransaction gestartet wurde, endet, wenn [PDO::commit](../../connect/php/pdo-commit.md) oder [PDO::rollback](../../connect/php/pdo-rollback.md) aufgerufen wird.  
  
PDO::beginTransaction ist nicht betroffen von dem (und hat keinen Einfluss auf den) Wert von PDO::ATTR_AUTOCOMMIT.  
  
Sie dürfen PDO::beginTransaction nicht aufrufen, solange die vorherige PDO::beginTransaction noch nicht mit PDO::rollback oder PDO::commit beendet wurde.  
  
Die Verbindung kehrt zum Autocommit-Modus zurück, falls diese Methode fehlschlägt.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel wird eine Datenbank namens „Test“ und eine Tabelle namens „Tabelle1“ verwendet. Es startet eine Transaktion und gibt die Befehle aus, um zwei Zeilen hinzuzufügen und dann eine Zeile zu löschen. Diese Befehle werden an die Datenbank geschickt und die Transaktion wird explizit mit `PDO::commit`beendet.  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
