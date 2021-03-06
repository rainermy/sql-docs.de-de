---
title: Sys. dm_exec_query_memory_grants (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_memory_grants_TSQL
- sys.dm_exec_query_memory_grants
- sys.dm_exec_query_memory_grants_TSQL
- dm_exec_query_memory_grants
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_memory_grants dynamic management view
ms.assetid: 2c417747-2edd-4e0d-8a9c-e5f445985c1a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2332e4f80e0dded930b22d9f0faf76d80ec09141
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52413411"
---
# <a name="sysdmexecquerymemorygrants-transact-sql"></a>sys.dm_exec_query_memory_grants (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu allen Abfragen, die angefordert haben und auf eine arbeitsspeicherzuweisung warten oder eine arbeitsspeicherzuweisung erhalten haben. Abfragen, die nicht auf eine arbeitsspeicherzuweisung erforderlich ist, werden in dieser Ansicht nicht angezeigt. Z. B. sortieren und Hash Join-Vorgänge haben arbeitsspeicherzuweisungen für die abfrageausführung, während Abfragen ohne eine **ORDER BY** Klausel keinen Speicher zu gewähren.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, diese Informationen bereitstellen, wird jede Zeile, die Daten enthält, die zum verbundenen Mandanten gehören nicht herausgefiltert. Darüber hinaus werden die Werte in den Spalten **Scheduler_id**, **Wait_order**, **Pool_id**, **Group_id** gefiltert; der Spaltenwert wird festgelegt auf NULL.  
  
> [!NOTE]  
> Aufrufen von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], verwenden Sie den Namen **sys.dm_pdw_nodes_exec_query_memory_grants**.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|ID (SPID) der Sitzung, in der die Abfrage ausgeführt wird.|  
|**request_id**|**int**|ID der Anforderung. Ist im Kontext der Sitzung eindeutig.|  
|**scheduler_id**|**int**|ID des Zeitplanungsmoduls, der diese Abfrage plant.|  
|**Grad an Parallelität**|**smallint**|Grad an Parallelität für diese Abfrage.|  
|**request_time**|**datetime**|Datum und Uhrzeit, zu der die Abfrage die Arbeitsspeicherzuweisung angefordert hat.|  
|**grant_time**|**datetime**|Datum und Uhrzeit, zu der die Arbeitsspeicherzuweisung für die Abfrage erfolgt ist. NULL, wenn noch kein Arbeitsspeicher zugewiesen wurde.|  
|**requested_memory_kb**|**bigint**|Insgesamt angeforderter Arbeitsspeicher in Kilobytes.|  
|**granted_memory_kb**|**bigint**|Insgesamt tatsächlich zugewiesener Arbeitsspeicher in Kilobytes. Kann NULL sein, wenn noch kein Arbeitsspeicher zugewiesen wurde. Für eine typische Situation, dieser Wert sollte identisch sein **Requested_memory_kb**. Für die Indexerstellung wird möglicherweise vom Server bei Bedarf weiterer Arbeitsspeicher über den ursprünglich zugewiesenen hinaus zugelassen.|  
|**required_memory_kb**|**bigint**|Minimaler Arbeitsspeicher in Kilobyte, der erforderlich ist, um diese Abfrage auszuführen. **Requested_memory_kb** ist gleich oder größer sein als diese.|  
|**used_memory_kb**|**bigint**|Der zu diesem Zeitpunkt verwendete physische Arbeitsspeicher in Kilobytes.|  
|**max_used_memory_kb**|**bigint**|Der bis zu diesem Zeitpunkt verwendete maximale physische Arbeitsspeicher in Kilobytes.|  
|**query_cost**|**float**|Die geschätzten Abfragekosten.|  
|**timeout_sec**|**int**|Timeout in Sekunden, nach dem die Abfrage die Anforderung der Arbeitsspeicherzuweisung aufgibt.|  
|**resource_semaphore_id**|**smallint**|Nicht eindeutige ID des Ressourcensemaphors, auf das die Abfrage wartet.<br /><br /> **Hinweis**: Diese ID ist in Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor Version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] eindeutig. Diese Änderung kann die Abfrageausführung bei der Problembehandlung beeinflussen. Weitere Informationen finden Sie im Abschnitt "Hinweise" weiter unten in diesem Thema.|  
|**queue_id**|**smallint**|ID der Warteschlange, in der die Abfrage auf Arbeitsspeicherzuweisungen wartet. NULL, wenn der Arbeitsspeicher bereits zugewiesen wurde.|  
|**wait_order**|**int**|Sequenzielle Position wartender Abfragen innerhalb des angegebenen **Queue_id**. Der Wert kann sich für eine Abfrage ändern, wenn andere Abfragen Arbeitsspeicherzuweisungen erhalten oder für diese ein Timeout eintritt. NULL, wenn bereits Arbeitsspeicher zugewiesen wurde.|  
|**is_next_candidate**|**bit**|Kandidat für die nächste Arbeitsspeicherzuweisung.<br /><br /> 1 = Ja<br /><br /> 0 = Nein<br /><br /> NULL = Arbeitsspeicher wurde bereits zugewiesen|  
|**wait_time_ms**|**bigint**|Wartezeit in Millisekunden. NULL, wenn der Arbeitsspeicher bereits zugewiesen wurde.|  
|**plan_handle**|**varbinary(64)**|Bezeichner für diesen Abfrageplan. Verwendung **Sys. dm_exec_query_plan** um die tatsächlichen XML-Plan zu extrahieren.|  
|**sql_handle**|**varbinary(64)**|Bezeichner für den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Text dieser Abfrage. Verwendung **Sys. dm_exec_sql_text** abzurufenden den tatsächlichen [!INCLUDE[tsql](../../includes/tsql-md.md)] Text.|  
|**group_id**|**int**|ID für die Arbeitsauslastungsgruppe, in der diese Abfrage ausgeführt wird.|  
|**pool_id**|**int**|ID des Ressourcenpools, zu dem die Arbeitsauslastungsgruppe gehört.|  
|**is_small**|**tinyint**|Der Wert 1 gibt an, dass diese Zuweisung das kleine Ressourcensemaphor verwendet. Der Wert 0 gibt an, dass ein normales Semaphor verwendet wird.|  
|**ideal_memory_kb**|**bigint**|Größe der Arbeitsspeicherzuweisung in Kilobyte (KB), um alles in den physischen Speicher aufzunehmen. Dieser Wert basiert auf der Kardinalitätsschätzung.|  
|**pdw_node_id**|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, dem auf diesem Verteilungspunkt befindet.|  
  
## <a name="permissions"></a>Berechtigungen  

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.   
   
## <a name="remarks"></a>Hinweise  
 Ein typisches Debugszenario für ein Abfragetimeout sieht folgendermaßen aus:  
  
-   Überprüfen Sie die gesamte Arbeitsspeicherstatus im Gesamtsystem mithilfe [Sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md), [Sys. dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md), und verschiedenen Leistungsindikatoren.  
  
-   Überprüfen Sie für die abfrageausführung arbeitsspeicherreservierungen in **Sys. dm_os_memory_clerks** , in denen `type = 'MEMORYCLERK_SQLQERESERVATIONS'`.  
  
-   Überprüfen Sie für Abfragen, die darauf warten<sup>1</sup> für gewährt, die mit **Sys. dm_exec_query_memory_grants**.  
  
    ```sql  
    --Find all queries waiting in the memory queue  
    SELECT * FROM sys.dm_exec_query_memory_grants where grant_time is null  
    ```  
    
    <sup>1</sup> In diesem Szenario ist der Wartetyp in der Regel RESOURCE_SEMAPHORE. Weitere Informationen finden Sie unter [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). 
  
-   Suchen Sie nach Cache für Abfragen arbeitsspeicherzuweisungen, die mit [dm_exec_cached_plans &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md) und [Sys. dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
  
    ```sql  
    -- retrieve every query plan from the plan cache  
    USE master;  
    GO  
    SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
    GO  
    ```  
  
-   Untersuchen Sie arbeitsspeicherintensive Abfragen mithilfe von [Sys. dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).  
  
    ```sql  
    --Find top 5 queries by average CPU time  
    SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
      plan_handle, query_plan   
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
    ORDER BY total_worker_time/execution_count DESC;  
    GO  
    ```  
  
-   Wenn eine endlosabfrage vermutet wird, überprüfen Sie den Showplan in [Sys. dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md) und den Batchtext aus [Sys. dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md).  
  
 Abfragen, die dynamischen Verwaltungssichten zu verwenden, die enthalten `ORDER BY` oder Aggregate arbeitsspeichernutzung erhöhen und somit zu dem Problem beitragen ihnen behandelt werden können.  
  
 Mit der Ressourcenkontrollen-Funktion kann ein Datenbankadministrator Serverressourcen auf Ressourcenpools verteilen, bis zu maximal 64 Pools. Beginnend mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], jeden Pool verhält sich wie eine kleine unabhängige Serverinstanz und erfordert 2 Semaphore. Die Anzahl der Zeilen, die von zurückgegeben werden **Sys. dm_exec_query_resource_semaphores** können nicht mit bis zu 20-Mal länger als die Zeilen, die in zurückgegebenen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. dm_exec_query_resource_semaphores &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md)     
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)     
 [Execution Related Dynamic Management Views and Functions &#40;Transact-SQL&#41; (Dynamische Verwaltungssichten und Funktionen im Zusammenhang mit der Ausführung (Transact-SQL))](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
