---
title: Befehl SET BLOCKSIZE | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e904d341513047b3940cf5b3fc2ba9538cdb5c8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764228"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE-Befehl
Gibt an, wie der Speicherplatz für die Speicherung der Memo-Felder verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>Argumente  
 *nBytes*  
 Gibt die Blockgröße, die in der Speicherplatz für Memo-Felder verwendet wird. Wenn *nBytes* gleich 0 ist, wird Speicherplatz auf dem Datenträger als einzelbytes (Blöcke von 1 Byte) zugeordnet. Wenn *nBytes* ist, wird eine ganze Zahl zwischen 1 und 32, Speicherplatz auf dem Datenträger zugeordnet, in Blöcken von *nBytes* Bytes multipliziert mit 512. Wenn *nBytes* ist größer als 32, Speicherplatz wird verwendet, in Blöcken von *nBytes* Bytes. Wenn Sie einen Block-Größenwert, der größer als 32 angeben, können Sie erhebliche Speicherplatz sparen.  
  
## <a name="remarks"></a>Hinweise  
 Der Standardwert für BLOCKSIZE festgelegt ist 64. Um die Blockgröße auf einen anderen Wert zurückzusetzen, nachdem die Datei erstellt wurde, legen Sie ihn auf einen neuen Wert aus, und klicken Sie dann verwenden Sie kopieren, um eine neue Tabelle zu erstellen. Die neue Tabelle weist die angegebene Blockgröße.
