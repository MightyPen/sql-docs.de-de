---
title: sys. dm_pdw_nodes_exec_query_profiles (Transact-SQL) | Microsoft-Dokumentation
description: Dynamische Verwaltungs Sicht, die zum Überwachen von Echt Zeit Data Warehouse Abfrage Status während der Ausführung der Abfrage verwendet werden kann.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 7237e7f7b49916e09f4a8c5cab0d7d49486cb971
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73145655"
---
# <a name="sysdm_pdw_nodes_exec_query_profiles-transact-sql"></a>sys. dm_pdw_nodes_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Überwacht die Echt Zeit Data Warehouse Abfrage Status während der Ausführung der Abfrage.   
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
Die zurückgegebenen Leistungsindikatoren gelten pro Operator und pro Thread. Die Ergebnisse sind dynamisch und stimmen nicht mit den Ergebnissen vorhandener Optionen, wie `SET STATISTICS XML ON` z. b. der Ausgabe der Ausgabe ab, wenn die Abfrage abgeschlossen ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|
|session_id|**smallint**|Identifiziert die Sitzung, in der die Abfrage ausgeführt wird. Verweist auf dm_exec_sessions.session_id.|  
|request_id|**int**|Identifiziert die Zielanforderung. Verweist auf dm_exec_sessions.request_id.|  
|sql_handle|**varbinary (64)**|Ein Token, das den Batch oder die gespeicherte Prozedur eindeutig identifiziert, zu der die Abfrage gehört. Verweist auf dm_exec_query_stats.sql_handle.|  
|plan_handle|**varbinary (64)**|Ein Token, das einen Abfrage Ausführungsplan für einen Batch eindeutig identifiziert, der ausgeführt wurde und dessen Plan sich im Plancache befindet oder gerade ausgeführt wird. Verweist auf dm_exec_query_stats. plan_handle.|  
|physical_operator_name|**nvarchar(256)**|Der Name des physischen Operators.|  
|node_id|**int**|Identifiziert einen Operatorknoten in der Abfragestruktur.|  
|thread_id|**int**|Unterscheidet die Threads (für eine parallele Abfrage), die zu demselben Abfrageoperatorknoten gehören.|  
|task_address|**varbinary(8)**|Identifiziert den SQLOS-Task, den dieser Thread verwendet. Verweist auf dm_os_tasks.task_address.|  
|row_count|**BIGINT**|Anzahl der bisher vom Operator zurückgegebenen Zeilen.|  
|rewind_count|**BIGINT**|Anzahl der bisherigen Zurückspulvorgänge.|  
|rebind_count|**BIGINT**|Anzahl der bisherigen erneuten Bindungen.|  
|end_of_scan_count|**BIGINT**|Anzahl der bisherigen Scanenden.|  
|estimate_row_count|**BIGINT**|Geschätzte Anzahl von Zeilen. Es kann nützlich sein, "estimated_row_count" mit dem tatsächlichen "row_count" zu vergleichen.|  
|first_active_time|**BIGINT**|Die Zeit in Millisekunden, zu der der Operator zuerst aufgerufen wurde.|  
|last_active_time|**BIGINT**|Die Zeit in Millisekunden, zu der der Operator zuletzt aufgerufen wurde.|  
|open_time|**BIGINT**|Zeitstempel beim Öffnen (in Millisekunden).|  
|first_row_time|**BIGINT**|Zeitstempel beim Öffnen der ersten Zeile (in Millisekunden).|  
|last_row_time|**BIGINT**|Zeitstempel beim Öffnen der letzten Zeile (in Millisekunden).|  
|close_time|**BIGINT**|Zeitstempel beim Schließen (in Millisekunden).|  
|elapsed_time_ms|**BIGINT**|Die gesamte verstrichene Zeit (in Millisekunden), die bisher durch die Vorgänge des Ziel Knotens verwendet wurde.|  
|cpu_time_ms|**BIGINT**|Die CPU-Gesamtzeit (in Millisekunden), die bisher durch die Vorgänge des Ziel Knotens verwendet wurde.|  
|database_id|**smallint**|ID der Datenbank, die das Objekt enthält, für das die Lese- und Schreibvorgänge ausgeführt werden.|  
|object_id|**int**|Der Bezeichner für das Objekt, für das die Lese- und Schreibvorgänge ausgeführt werden. Verweist auf "sys.objects.object_id".|  
|index_id|**int**|Der Index (sofern vorhanden), für den das Rowset geöffnet wird.|  
|scan_count|**BIGINT**|Anzahl der bisherigen Tabellen-/Indexscans.|  
|logical_read_count|**BIGINT**|Anzahl der bisherigen logischen Lesevorgänge.|  
|physical_read_count|**BIGINT**|Anzahl der bisherigen physischen Lesevorgänge.|  
|read_ahead_count|**BIGINT**|Anzahl der bisherigen Read-Ahead-Lesevorgänge.|  
|write_page_count|**BIGINT**|Anzahl der bisherigen page-writes-Schreibvorgänge aufgrund eines Überlaufs.|  
|lob_logical_read_count|**BIGINT**|Anzahl der bisherigen logischen LOB-Lesevorgänge.|  
|lob_physical_read_count|**BIGINT**|Anzahl der bisherigen physischen LOB-Lesevorgänge.|  
|lob_read_ahead_count|**BIGINT**|Anzahl der bisherigen Read-Ahead-LOB-Lesevorgänge.|  
|segment_read_count|**int**|Anzahl der bisherigen Segment-Read-Ahead-Lesevorgänge.|  
|segment_skip_count|**int**|Anzahl der bisher übersprungenen Segmente.| 
|actual_read_row_count|**BIGINT**|Anzahl der von einem Operator gelesenen Zeilen, bevor das Rest-Prädikat angewendet wurde.| 
|estimated_read_row_count|**BIGINT**|**Gilt für:** Ab [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] SP1. <br/>Anzahl der Zeilen, die von einem Operator vor dem Anwenden des Rest-Prädikats gelesen werden sollen.|  
  
## <a name="remarks"></a>Bemerkungen  
Die gleichen Hinweise in [sys. dm_exec_query_profiles](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql?view=sql-server-ver15) werden angewendet.  

## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW SERVER STATE`-Berechtigung auf dem Server.  

## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
   

 ## <a name="next-steps"></a>Nächste Schritte
 Weitere Hinweise zur Entwicklung finden Sie in der [Entwicklungsübersicht für SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).
