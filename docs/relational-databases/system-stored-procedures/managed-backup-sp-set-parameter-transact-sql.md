---
title: managed_backup.sp_set_parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 578997f57c4092689e49cb0e3102c8bdf7b4f8d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843891"
---
# <a name="managedbackupspsetparameter-transact-sql"></a>managed_backup.sp_set_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Legt den Wert des angegebenen Smart Admin-Systemparameters fest.  
  
 Die verfügbaren Parameter beziehen sich auf [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Mit diesen Parametern werden die E-Mail-Benachrichtigungen festgelegt, bestimmte erweiterte Ereignisse aktiviert und auf benutzerdefinierten Richtlinien basierende Verwaltungsrichtlinien aktiviert. Sie müssen die Paare aus Parametername und Parameterwert angeben.  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="Arguments"></a> Argumente  
 @parameter_name  
 Der Name des Parameters, dessen Wert festgelegt werden soll. @parameter_name ist vom Datentyp NVARCHAR(128). Die verfügbaren Parameternamen lauten **SSMBackup2WANotificationEmailIds**, **SSMBackup2WADebugXevent**, **SSMBackup2WAEnableUserDefinedPolicy**, **FileRetentionDebugXevent**, und **StorageOperationDebugXevent**.  
  
 @parameter_value  
 Der Wert des Parameters, der festgelegt werden soll. @parameter der Wert ist vom Datentyp NVARCHAR(128).  Im Folgenden sind die zulässigen Parametername/Parameterwert-Paare aufgeführt:  
  
-   @parameter_name = 'SSMBackup2WANotificationEmailIds': @parameter_value = "Email"  
  
-   @parameter_name = 'SSMBackup2WAEnableUserDefinedPolicy': @parameter_value = {'true' | 'false'}  
  
-   @parameter_name = 'SSMBackup2WADebugXevent': @parameter_value = {'true' | 'false'}  
  
-   @parameter_name = 'FileRetentionDebugXevent': @parameter_value = {'true' | 'false'}  
  
-   @parameter_name = "StorageOperationDebugXevent" = {'true' | 'false'}  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Optionaler Abschnitt, der bewährte Methoden beschreibt, die der Benutzer beim Ausführen der Anweisung oder Routine befolgen sollte.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert **EXECUTE** Berechtigungen für **managed_backup.sp_set_parameter** gespeicherte Prozedur.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen werden erweiterte operationale und Debugereignisse aktiviert.  
  
```  
-- to enable operational events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionOperationalXevent', 'True'  
--  to enable debug events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
```  
  
 Im folgenden Beispiel werden E-Mail-Benachrichtigungen über Fehler sowie Warnungen aktiviert; zudem wird die emailID festgelegt, an die die Benachrichtigungen gesendet werden sollen:  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
