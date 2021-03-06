---
title: Sys. database_firewall_rules (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 59c59150136910e2d0818fe93ff4811ed3262d8d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012321"
---
# <a name="sysdatabasefirewallrules-azure-sql-database"></a>sys.database_firewall_rules (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt Informationen über die Firewalleinstellungen auf Datenbankebene zurück, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]zugeordnet sind. Firewalleinstellungen auf Datenbankebene sind besonders nützlich, wenn eigenständige Datenbankbenutzer verwendet werden. Weitere Informationen finden Sie unter [Contained Database Users - Making Your Database Portable](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 Die `sys.database_firewall_rules` -Sicht enthält die folgenden Spalten:  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|id|**INTEGER**|Der Bezeichner der Firewalleinstellung auf Datenbankebene.|  
|NAME|**NVARCHAR(128)**|Der ausgewählte Name, um die Firewalleinstellung auf Datenbankebene zu beschreiben und von anderen zu unterscheiden.|  
|start_ip_address|**VARCHAR(50)**|Die niedrigste IP-Adresse im Bereich der Firewalleinstellung auf Datenbankebene. IP-Adressen, die gleich oder größer dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die niedrigste mögliche IP-Adresse ist `0.0.0.0`.|  
|end_ip_address|**VARCHAR(50)**|Die höchste IP-Adresse im Bereich der Firewalleinstellung. IP-Adressen, die kleiner oder gleich dieser IP-Adresse sind, können versuchen, eine Verbindung mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Instanz herzustellen. Die höchste mögliche IP-Adresse ist `255.255.255.255`.<br /><br /> Hinweis: Windows Azure-Verbindungsversuche sind zulässig, wenn sowohl dieses Feld und die **Start_ip_address** Feld `0.0.0.0`.|  
|create_date|**DATETIME**|UTC-Datum und -Uhrzeit der Erstellung der Firewalleinstellung auf Datenbankebene.|  
|modify_date|**DATETIME**|UTC-Datum und -Uhrzeit der letzten Änderung der Firewalleinstellung auf Datenbankebene.|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie zum Entfernen einer Datenbank-Firewallregel [Sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md). Zum Festlegen einer Firewallregel für alle [!INCLUDE[ssSDS](../../includes/sssds-md.md)], finden Sie unter [Sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md). Um Informationen zu vorhandenen Datenbank-Firewallregeln zurückzugeben, fragen Sie [sys.database_firewall_rules (Azure SQL Database)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)ab.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht ist in der **master** -Datenbank und in jeder Benutzerdatenbank verfügbar. Alle Benutzer, die berechtigt sind, eine Verbindung mit der Datenbank herzustellen, haben schreibgeschützten Zugriff auf diese Sicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_set_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Sys. database_firewall_rules (Azure SQL-Datenbank)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [Sp_delete_database_firewall_rule &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Konfigurieren einer Firewall für FILESTREAM-Zugriff](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  
