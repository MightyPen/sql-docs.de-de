---
title: sys. dm_db_index_usage_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_index_usage_stats_TSQL
- sys.dm_db_index_usage_stats
- sys.dm_db_index_usage_stats_TSQL
- dm_db_index_usage_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_usage_stats dynamic management view
ms.assetid: d06a001f-0f72-4679-bc2f-66fff7958b86
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 491ec37d96cf6bdb2b074efb42a54406beb1fd20
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264404"
---
# <a name="sysdm_db_index_usage_stats-transact-sql"></a>sys.dm_db_index_usage_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt die Anzahl verschiedener Arten von Indexvorgängen und den Zeitpunkt zurück, wann die einzelnen Vorgänge zuletzt ausgeführt wurden.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]können dynamische Verwaltungssichten keine Informationen verfügbar machen, die sich auf die Datenbankkapselung auswirken würden oder die sich auf andere Datenbanken beziehen, auf die der Benutzer Zugriff hat. Um zu vermeiden, dass diese Informationen verfügbar gemacht werden, wird jede Zeile, die Daten enthält, die nicht zum verbundenen Mandanten gehören, herausgefiltert.  
  
> [!NOTE]  
>  **sys. dm_db_index_usage_stats** gibt keine Informationen zu Speicher optimierten Indizes zurück. Weitere Informationen zur Speicher optimierten Index Verwendung finden Sie unter [sys. dm_db_xtp_index_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).  
  
> [!NOTE]  
>  Um diese Sicht von [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oder [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]aufzurufen, verwenden Sie **sys. dm_pdw_nodes_db_index_usage_stats**.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**database_id**|**smallint**|ID der Datenbank, für die die Tabelle oder Sicht definiert ist.|  
|**object_id**|**int**|ID der Tabelle oder Sicht, für die der Index definiert ist.|  
|**index_id**|**int**|Die ID des Index.|  
|**user_seeks**|**BIGINT**|Anzahl von Suchvorgängen durch Benutzerabfragen.|  
|**user_scans**|**BIGINT**|Anzahl der Scans durch Benutzer Abfragen, für die kein Seek-Prädikat verwendet wurde.|  
|**user_lookups**|**BIGINT**|Anzahl von Lesezeichen-Nachschlagevorgängen durch Benutzerabfragen.|  
|**user_updates**|**BIGINT**|Anzahl von Updates durch Benutzerabfragen. Dies schließt Einfüge-, Lösch-und Update Vorgänge ein, die die Anzahl der Vorgänge darstellen, die nicht den betroffenen Zeilen entspricht. Wenn Sie z. b. 1000 Zeilen in einer Anweisung löschen, wird dieser Zähler um 1 erhöht.|  
|**last_user_seek**|**datetime**|Zeitpunkt des letzten Suchvorgangs durch den Benutzer|  
|**last_user_scan**|**datetime**|Zeitpunkt des letzten Scanvorgangs durch den Benutzer|  
|**last_user_lookup**|**datetime**|Zeitpunkt des letzten Nachschlagevorgangs durch den Benutzer.|  
|**last_user_update**|**datetime**|Zeitpunkt des letzten Updates durch den Benutzer.|  
|**system_seeks**|**BIGINT**|Anzahl von Suchvorgängen durch Systemabfragen.|  
|**system_scans**|**BIGINT**|Anzahl von Scanvorgängen durch Systemabfragen.|  
|**system_lookups**|**BIGINT**|Anzahl von Nachschlagevorgängen durch Systemabfragen.|  
|**system_updates**|**BIGINT**|Anzahl von Updates durch Systemabfragen.|  
|**last_system_seek**|**datetime**|Zeitpunkt des letzten Systemsuchvorgangs.|  
|**last_system_scan**|**datetime**|Zeitpunkt des letzten Systemscanvorgangs.|  
|**last_system_lookup**|**datetime**|Zeitpunkt des letzten Systemnachschlagevorgangs.|  
|**last_system_update**|**datetime**|Zeitpunkt des letzten Systemupdates.|  
|pdw_node_id|**int**|**Gilt für**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Der Bezeichner für den Knoten, auf dem sich diese Distribution befindet.|  
  
## <a name="remarks"></a>Bemerkungen  
 Jeder einzelne Such-, Scan-, Nachschlage- oder Updatevorgang für den angegebenen Index durch eine Abfrageausführung zählt als Verwendung dieses Indexes, und der entsprechende Zähler in dieser Sicht wird inkrementiert. Informationen werden für Vorgänge angezeigt, die durch Benutzerabfragen verursacht werden, und für Vorgänge, die durch intern generierte Abfragen verursacht werden, wie z. B. Scans zum Sammeln von Statistikdaten.  
  
 Der **user_updates**-Leistungsindikator gibt die Wartungsebene für den Index an, die durch Einfüge-, Update- oder Löschvorgänge an der zugrunde liegenden Tabelle oder Sicht verursacht wird. Mithilfe dieser Sicht können Sie ermitteln, welche Indizes selten von den Anwendungen verwendet werden. Außerdem können Sie mithilfe dieser Sicht bestimmen, welche Indizes einen hohen Wartungsaufwand erzeugen. Sie können Indizes löschen, die einen hohen Wartungsaufwand erzeugen, aber nicht oder nur selten für Abfragen verwendet werden.  
  
 Die Zähler werden auf 'leer' gesetzt, sobald ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst (MSSQLSERVER) gestartet wird. Außerdem werden jedes Mal, wenn eine Datenbank getrennt oder beendet wird (beispielsweise, weil AUTO_CLOSE auf ON festgelegt ist), alle dieser Datenbank zugehörigen Zeilen entfernt.  
  
 Falls ein Index verwendet wird, wird **sys.dm_db_index_usage_stats** eine Zeile hinzugefügt, wenn nicht bereits eine Zeile für diesen Index vorhanden ist. Beim Hinzufügen der Zeile sind deren Zähler anfänglich auf 0 festgelegt.  
  
 Während des Upgrades [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], oder [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]werden Einträge in sys. dm_db_index_usage_stats entfernt. [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]Ab werden Einträge wie vor gespeichert [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].  
  
## <a name="permissions"></a>Berechtigungen  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]ist die `VIEW SERVER STATE` -Berechtigung erforderlich.   
Bei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarifen ist die `VIEW DATABASE STATE` -Berechtigung in der Datenbank erforderlich. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] den Tarifen "Standard" und "Basic" ist der **Server Administrator** oder ein **Azure Active Directory Administrator** Konto erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  

 [Index bezogene dynamische Verwaltungs Sichten und Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)   
 [sys. dm_db_index_operational_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  
  


