---
title: sp_cdc_start_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_start_job
- sp_cdc_start_job_TSQL
- sys.sp_cdc_start_job_TSQL
- sys.sp_cdc_start_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_start_job
ms.assetid: cf443a67-7705-4799-9f39-0e3a6a8a0708
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 842f7a9f677312501a92a42301017eedaee0f5d4
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589144"
---
# <a name="sysspcdcstartjob-transact-sql"></a>sys.sp_cdc_start_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Startet einen Cleanup- oder Aufzeichnungsauftrag für Change Data Capture in der aktuellen Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_start_job [ [ @job_type = ] 'job_type' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [[  **@job_type=** ] **"**_Job_type_**"** ]  
 Der Typ des hinzuzufügenden Auftrags. *Der Standardwert ist* ist **nvarchar(20)** hat den Standardwert **erfassen**. Gültige Eingaben sind **erfassen** und **Bereinigung**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 sys.sp_cdc_start_job kann von einem Administrator zum expliziten Start des Aufzeichnungsauftrags oder Cleanupauftrags verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-starting-a-capture-job"></a>A. Starten eines Aufzeichnungsauftrags  
 Im folgenden Beispiel wird der Aufzeichnungsauftrag für die `AdventureWorks2012`-Datenbank gestartet. Angeben eines Werts für *Job_type* ist nicht erforderlich, da der Standardauftragstyp **erfassen**.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_start_job;  
GO  
```  
  
### <a name="b-starting-a-cleanup-job"></a>B. Starten eines Cleanupauftrags  
 Im folgenden Beispiel wird ein Cleanupauftrag für die `AdventureWorks2012`-Datenbank gestartet.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_start_job @job_type = N'cleanup';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sp_cdc_stop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md)  
  
  
