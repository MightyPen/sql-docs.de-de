---
title: sys. sysdatenbanken (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b0dab1ca5f21ced6a54192a4b0173ead68fd6f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089171"
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jede Datenbank in einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstmalig installiert wird, enthält **sysdatabases** Einträge für die Datenbanken **master**, **model**, **msdb**und **tempdb** .  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Datenbankname|  
|**DBID**|**smallint**|Datenbank-ID|  
|**sid**|**varbinary(85)**|Die System-ID des Datenbankerstellers.|  
|**Spar**|**smallint**|Wird intern verwendet, um eine Datenbank beim Erstellen zu sperren.|  
|**Stands**|**int**|Statusbits, die teilweise mithilfe von [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) festgelegt werden können, wie im Folgenden beschrieben:<br /><br /> 1 = **autoclose** (ALTER DATABASE)<br /><br /> 4 = **select into/bulkcopy** (ALTER DATABASE mithilfe von SET RECOVERY)<br /><br /> 8 = **trunc. log on chkpt** (ALTER DATABASE mithilfe von SET RECOVERY)<br /><br /> 16 = **torn page detection** (ALTER DATABASE)<br /><br /> 32 = **loading**<br /><br /> 64 = **pre recovery**<br /><br /> 128 = **recovering**<br /><br /> 256 = **not recovered**<br /><br /> 512 = **offline** (ALTER DATABASE)<br /><br /> 1024 = **read only** (ALTER DATABASE)<br /><br /> 2048 = **dbo use only** (ALTER DATABASE mithilfe von SET RESTRICTED_USER)<br /><br /> 4096 = **single user** (ALTER DATABASE)<br /><br /> 32768 = **emergency mode**<br /><br /> 65536 = **CHECKSUM** (ALTER DATABASE)<br /><br /> 4194304 = **autoshrink** (ALTER DATABASE)<br /><br /> 1073741824 = **cleanly shutdown**<br /><br /> Es können mehrere Bits gleichzeitig aktiviert (ON) sein.|  
|**status2**|**int**|16384 = **ANSI null default** (ALTER DATABASE)<br /><br /> 65536 = **concat null yields null** (ALTER DATABASE)<br /><br /> 131072 = **recursive triggers** (ALTER DATABASE)<br /><br /> 1048576 = **default to local cursor** (ALTER DATABASE)<br /><br /> 8388608 = **quoted identifier** (ALTER DATABASE)<br /><br /> 33554432 = **cursor close on commit** (ALTER DATABASE)<br /><br /> 67108864 = **ANSI nulls** (ALTER DATABASE)<br /><br /> 268435456 = **ANSI warnings** (ALTER DATABASE)<br /><br /> 536870912 = **full text enabled** (festgelegt mithilfe von **sp_fulltext_database**)|  
|**crdate**|**datetime**|Das Erstellungsdatum.|  
|**bleiben**|**datetime**|Für die zukünftige Verwendung reserviert.|  
|**Kategorie**|**int**|Enthält ein Bitmuster mit Informationen, die für die Replikation verwendet werden.<br /><br /> 1 = Veröffentlicht für die Momentaufnahme- oder Transaktionsreplikation.<br /><br /> 2 = Abonniert für eine Momentaufnahme- oder Transaktionsveröffentlichung.<br /><br /> 4 = Veröffentlicht für die Mergereplikation.<br /><br /> 8 = Abonniert für eine Mergeveröffentlichung.<br /><br /> 16 = Verteilungsdatenbank.|  
|**cmptlevel**|**tinyint**|Kompatibilitätsgrad für die Datenbank. Weitere Informationen finden Sie unter [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|  
|**Einfügen**|**nvarchar(260)**|Der Betriebssystempfad und -name für die primäre Datei der Datenbank.<br /><br /> der **Dateiname** ist für **dbcreator**, **sysadmin**, den Datenbankbesitzer mit CREATE ANY DATABASE-Berechtigungen oder berechtigte mit einer der folgenden Berechtigungen sichtbar: ALTER ANY DATABASE, CREATE ANY DATABASE, View any Definition. Führen Sie eine Abfrage der [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md) -Kompatibilitätssicht oder der [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) -Sicht aus, um den Pfad und den Dateinamen zurückzugeben.|  
|**Version**|**smallint**|Die interne Versionsnummer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Codes, mit dem die Datenbank erstellt wurde. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Alter Database &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitäts Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
