---
title: sys. dm_db_uncontained_entities (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_uncontained_entities
- dm_db_uncontained_entities_TSQL
- sys.dm_db_uncontained_entities_TSQL
- dm_db_uncontained_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_uncontained_entities dynamic management view
ms.assetid: f417efd4-8c71-4f81-bc9c-af13bb4b88ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 625c6134c91a9b452b8df2b7e235b78126c1354e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68026918"
---
# <a name="sysdm_db_uncontained_entities-transact-sql"></a>sys.dm_db_uncontained_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt alle nicht enthaltenen Objekte an, die in der Datenbank verwendet werden. Nicht enthaltene Objekte sind Objekte, die die Datenbankbegrenzung in einer eigenständigen Datenbank überschreiten. Auf diese Sicht kann sowohl von einer eigenständigen Datenbank als auch von einer abhängigen Datenbank zugegriffen werden. Wenn sys.dm_db_uncontained_entities leer ist, verwendet die Datenbank nur enthaltene Entitäten.  
  
 Wenn die Datenbankbegrenzung von einem Modul mehrmals überschritten wird, wird nur die erste Überschreitung gemeldet.  
  
||||  
|-|-|-|  
|**Spaltenname**|**Typ**|**Beschreibung**|  
|*klassi*|**int**|1 = Objekt oder Spalte (einschließlich Modulen, XPs, Sichten, Synonymen und Tabellen).<br /><br /> 4 = Daten Bank Prinzipal<br /><br /> 5 = Assembly<br /><br /> 6 = Typ<br /><br /> 7 = Index (Volltextindex)<br /><br /> 12 = DDL-Daten Bank Auslösung<br /><br /> 19 = Route<br /><br /> 30 = Überwachungsspezifikation|  
|*class_desc*|**nvarchar (120)**|Klassenbeschreibung der Entitätsklasse. Eine der folgenden, um der-Klasse zu entsprechen:<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **DATABASE_PRINCIPAL**<br /><br /> **ASSEMBLY**<br /><br /> **TYPE**<br /><br /> **INDEX**<br /><br /> **DATABASE_DDL_TRIGGER**<br /><br /> **ROUTE**<br /><br /> **AUDIT_SPECIFICATION**|  
|*major_id*|**int**|Die ID der Entität.<br /><br /> Wenn *Class* = 1, dann object_id<br /><br /> Wenn *Class* = 4, dann sys. database_principals. principal_id.<br /><br /> Wenn *Class* = 5, dann sys. Assemblys. assembly_id.<br /><br /> Wenn *Class* = 6, dann sys. types. user_type_id.<br /><br /> Wenn *Class* = 7, dann sys. Indexes. index_id.<br /><br /> Wenn *Class* = 12, dann sys. Triggers. object_id.<br /><br /> Wenn *Class* = 19, dann sys. routes. route_id.<br /><br /> Wenn *Class* = 30, dann sys. database_audit_specifications. database_specification_id.|  
|*statement_line_number*|**int**|Wenn die Klasse ein Modul ist, wird die Zeilennummer für die nicht enthaltene Verwendung zurückgegeben.  Anderenfalls ist der Wert NULL.|  
|*statement_ offset_begin*|**int**|Wenn die Klasse ein Modul ist, gibt dies die Startposition der nicht enthaltenen Verwendung in Byte an, beginnend bei 0. Andernfalls ist der Rückgabewert NULL.|  
|*statement_ offset_end*|**int**|Wenn die Klasse ein Modul ist, gibt dies die Endposition der nicht enthaltenen Verwendung in Byte an, beginnend bei 0. Der Wert -1 gibt das Ende des Moduls an. Andernfalls ist der Rückgabewert NULL.|  
|*statement_type*|**nvarchar(512)**|Der Typ der Anweisung.|  
|*feature_ Name*|**nvarchar(256)**|Gibt den externen Namen des Objekts zurück.|  
|*feature_type_name*|**nvarchar(256)**|Gibt den Typ der Funktion zurück.|  
  
## <a name="remarks"></a>Bemerkungen  
 sys. dm_db_uncontained_entities zeigt die Entitäten an, die die Daten Bank Grenze potenziell überschreiten können. Es werden alle Benutzerentitäten zurückgegeben, von denen Objekte außerhalb der Datenbank verwendet werden können.  
  
 Die folgenden Funktionstypen werden gemeldet.  
  
-   Unbekanntes Kapselungsverhalten (dynamisches SQL oder verzögerte Namensauflösung)  
  
-   DBCC-Befehl  
  
-   Gespeicherte Systemprozeduren  
  
-   Skalarsystemfunktion  
  
-   Tabellenwert-Systemfunktion  
  
-   Integrierte Systemfunktion  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 sys.dm_db_uncontained_entities gibt nur Objekte zurück, für die der Benutzer eine Berechtigung besitzt. Um die Kapselung der Datenbank vollständig auszuwerten, sollte diese Funktion von einem Benutzer mit hohen Berechtigungen verwendet werden, wie z. b. einem Mitglied der festen Server Rolle **sysadmin** oder der **db_owner** Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Prozedur P1 erstellt, und `sys.dm_db_uncontained_entities`wird abgefragt. Die Abfrage meldet, dass **sys.endpoints** von P1 außerhalb der Datenbank verwendet wird.  
  
```sql  
CREATE DATABASE Test;  
GO  
  
USE Test;  
GO  
CREATE PROC P1  
AS   
SELECT * FROM sys.endpoints ;  
GO  
SELECT SO.name, UE.* FROM sys.dm_db_uncontained_entities AS UE  
LEFT JOIN sys.objects AS SO  
    ON UE.major_id = SO.object_id;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenständige Datenbanken](../../relational-databases/databases/contained-databases.md)  
  
  
