---
title: Sys. service_message_types (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.service_message_types
- service_message_types
- sys.service_message_types_TSQL
- service_message_types_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.service_message_types catalog view
ms.assetid: 6a38709a-60fe-46f6-89da-718f74f15600
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 866424b72b284479e2f9e1771ff62c5099cb7f71
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="sysservicemessagetypes-transact-sql"></a>sys.service_message_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Katalogsicht enthält eine Zeile pro Nachrichtentyp, der im Service Broker registriert ist.
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Nachrichtentypes, der innerhalb der Datenbank eindeutig ist. Lässt keine NULL-Werte zu.|  
|**message_type_id**|**int**|Die ID des Nachrichtentypes, die innerhalb der Datenbank eindeutig ist. Lässt keine NULL-Werte zu.|  
|**principal_id**|**int**|Die ID des Datenbankprinzipals, der diesen Nachrichtentyp besitzt. Lässt NULL-Werte zu.|  
|**Überprüfung**|**char(2)**|Vom Broker vor dem Senden von Nachrichten dieses Types ausgeführte Überprüfung. Lässt keine NULL-Werte zu. Folgende Angaben sind möglich:<br /><br /> N = Keiner<br /><br /> X = XML<br /><br /> E = Leer|  
|**validation_desc**|**nvarchar(60)**|Beschreibung der vom Broker vor dem Senden von Nachrichten dieses Types ausgeführten Überprüfung. Lässt NULL-Werte zu. Folgende Angaben sind möglich:<br /><br /> NONE<br /><br /> XML<br /><br /> EMPTY|  
|**xml_collection_id**|**int**|Für eine Überprüfung, die ein XML-Schema verwendet, wird die ID der Schemaauflistung verwendet.<br /><br /> Andernfalls wird NULL verwendet.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  