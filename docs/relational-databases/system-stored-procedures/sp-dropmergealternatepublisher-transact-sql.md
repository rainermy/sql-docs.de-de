---
title: Sp_dropmergealternatepublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergealternatepublisher
- sp_dropmergealternatepublisher_TSQL
helpviewer_keywords:
- sp_dropmergealternatepublisher
ms.assetid: a7dee4e2-2a60-41da-9d1d-6f991d7e2c5e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 722a8092a799695be0ab5e4f6925cd7416b7c1b9
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54134720"
---
# <a name="spdropmergealternatepublisher-transact-sql"></a>sp_dropmergealternatepublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen alternativen Verleger aus einer Mergeveröffentlichung. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropmergealaternatepublisher [ @publisher = ] 'publisher'    , [ @publisher_db = ] 'publisher_db'    , [ @publication = ] 'publication'    , [ @alternate_publisher = ] 'alternate_publisher'    , [ @alternate_publisher_db = ] 'alternate_publisher_db'    , [ @alternate_publication = ] 'alternate_publication'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publisher=**] **"**_Verleger_**"**  
 Der Name des aktuellen Verlegers. *Publisher*ist **Sysname**, hat keinen Standardwert.  
  
 [  **@publisher_db=**] **"**_Publisher_db_**"**  
 Der Name der aktuellen Veröffentlichungsdatenbank. *Publisher_db*ist **Sysname**, hat keinen Standardwert.  
  
 [  **@publication =**] **"**_Veröffentlichung_**"**  
 Der Name der aktuellen Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@alternate_publisher=**] **"**_Alternate_publisher_**"**  
 Der Name des alternativen Verlegers, der als alternativer Synchronisierungspartner gelöscht werden soll. *Alternate_publisher*ist **Sysname**, hat keinen Standardwert.  
  
 [  **@alternate_publisher_db=**] **"**_Alternate_publisher_db_**"**  
 Der Name der Veröffentlichungsdatenbank, die als Veröffentlichungsdatenbank des alternativen Synchronisierungspartners gelöscht werden soll. *Alternate_publisher_db*ist **Sysname**, hat keinen Standardwert.  
  
 [  **@alternate_publication=**] **"**_Alternate_publication_**"**  
 Der Name der Veröffentlichung, die als Veröffentlichung des alternativen Synchronisierungspartners gelöscht werden soll. *Alternate_publication*ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropmergealternatepublisher** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_dropmergelternatepublisher**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_addmergealternatepublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergealternatepublisher-transact-sql.md)  
  
  
