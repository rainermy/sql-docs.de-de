---
title: Sp_restoredbreplication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoredbreplication
- sp_restoredbreplication_TSQL
helpviewer_keywords:
- sp_restoredbreplication
ms.assetid: a2c5ee32-e6d9-46e9-8031-8ff13c20acf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 383c37219a0c1e901f58bcee7ccc436c36973d1c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52775272"
---
# <a name="sprestoredbreplication-transact-sql"></a>sp_restoredbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt Replikationseinstellungen, wenn eine Datenbank auf einem Server, in einer Datenbank oder auf einem System wiederhergestellt wird, bei denen es sich nicht um die Ausgangsobjekte handelt oder die aus anderen Gründen nicht in der Lage sind, Replikationsprozesse auszuführen. Wenn eine replizierte Datenbank auf einem Server oder in einer Datenbank wiederhergestellt wird, von dem bzw. der die Sicherung nicht erstellt wurde, dann können die Replikationseinstellungen nicht beibehalten werden. Bei der Wiederherstellung der Server ruft **Sp_restoredbreplication** direkt an die Replikationsmetadaten automatisch aus der wiederhergestellten Datenbank zu entfernen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_restoredbreplication [ @srv_orig = ] 'original_server_name'  
        , [ @db_orig = ] 'original_database_name'  
    [ , [ @keep_replication = ] keep_replication ]  
    [ , [ @perform_upgrade = ] perform_upgrade ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@srv_orig =** ] **"***Original_server_name***"**  
 Der Name des Servers, auf dem die Sicherung erstellt wurde. *Original_server_name* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@db_orig =** ] **"***Original_database_name***"**  
 Name der Datenbank, die gesichert wurde. *Original_database_name* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@keep_replication =** ] *Keep_replication*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@perform_upgrade=** ] *Perform_upgrade*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_restoredbreplication** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** oder **Dbcreator** festen Serverrolle oder die **Dbo** Datenbankschema kann ausführen **Sp_restoredbreplication**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
