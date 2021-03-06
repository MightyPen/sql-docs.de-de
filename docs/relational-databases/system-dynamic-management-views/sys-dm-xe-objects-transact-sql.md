---
title: sys. dm_xe_objects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_objects
- sys.dm_xe_objects
- sys.dm_xe_objects_TSQL
- dm_xe_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_objects dynamic management view
- extended events [SQL Server], views
ms.assetid: 5d944b99-b097-491b-8cbd-b0e42b459ec0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 023ee54178c5f303797c6db83cc646353304b051
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090274"
---
# <a name="sysdm_xe_objects-transact-sql"></a>sys.dm_xe_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jedes Objekt zurück, das von einem Ereignispaket verfügbar gemacht wird. Folgende Objekte sind möglich:  
  
-   Ereignisse. Ereignisse geben interessierende Punkte in einem Ausführungspfad an. Alle Ereignisse enthalten Informationen über einen interessierenden Punkt.  
  
-   Aktionen Aktionen werden synchron ausgeführt, wenn Ereignisse ausgelöst werden. Eine Aktion kann Laufzeitdaten an ein Ereignis anfügen.  
  
-   Ziele. Ziele nutzen Ereignisse entweder synchron für den Thread, der das Ereignis auslöst, oder asynchron für einen vom System bereitgestellten Thread.  
  
-   Prädikate. Prädikatquellen rufen Werte aus Ereignisquellen zur Verwendung in Vergleichsvorgängen ab. Prädikatvergleiche vergleichen bestimmte Datentypen und geben einen booleschen Wert zurück.  
  
-   Typen. Typen kapseln die Länge und Eigenschaften der Byte-Auflistung, die zum Interpretieren der Daten benötigt wird.  

 |Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**nvarchar (60)**|Der Name des Objekts. der Name ist innerhalb eines Pakets für einen bestimmten Objekttyp eindeutig. Lässt keine NULL-Werte zu.|  
|object_type|**nvarchar (60)**|Der Typ des Objekts. object_type ist einer der folgenden:<br /><br /> Ereignis<br /><br /> action<br /><br /> target<br /><br /> pred_source<br /><br /> pred_compare<br /><br /> type<br /><br /> Lässt keine NULL-Werte zu.|  
|package_guid|**uniqueidentifier**|Die GUID für das Paket, das diese Aktion verfügbar macht. Es gibt eine n:1-Beziehung mit sys.dm_xe_packages.package_id. Lässt keine NULL-Werte zu.|  
|description|**nvarchar(256)**|Eine Beschreibung der Aktion. die Beschreibung wird vom Paket Ersteller festgelegt. Lässt keine NULL-Werte zu.|  
|capabilities|**int**|Eine Bitmap, die die Fähigkeiten des Objekts beschreibt. Lässt NULL-Werte zu.|  
|capabilities_desc|**nvarchar(256)**|Listet alle Fähigkeiten des Objekts auf. Lässt NULL-Werte zu.<br /><br /> **Funktionen, die für alle Objekttypen gelten**<br /><br /> -<br />                                **Privat**. Das einzige für die interne Verwendung verfügbare Objekt. Der Zugriff auf das Objekt kann nicht über CREATE/ALTER EVENT SESSION DDL erfolgen. Überwachungsereignisse und Ziele gehören zu dieser Kategorie, zusätzlich zu einer kleinen Anzahl an intern verwendeten Objekten.<br /><br /> ===============<br /><br /> **Ereignisfunktionen**<br /><br /> -<br />                                **No_block**. Das Ereignis ist in einem wichtigen Codepfad, der aus keinem Grund blockieren kann. Ereignisse mit dieser Funktion werden möglicherweise keiner Ereignissitzung hinzugefügt, die NO_EVENT_LOSS angibt.<br /><br /> ===============<br /><br /> **Funktionen, die für alle Objekttypen gelten**<br /><br /> -<br />                                **Process_whole_buffers**. Das Ziel verwendet jeweils Ereignispuffer, anstelle von Ereignis zu Ereignis vorzugehen.<br /><br /> -<br />                        **Singleton**. Nur eine Instanz des Ziels kann in einem Prozess vorhanden sein. Obwohl mehrere Ereignissitzungen auf dasselbe Singletonziel verweisen können, ist jedoch nur eine einzige Instanz vorhanden. Für diese Instanz wird jedes eindeutige Ereignis nur einmal angegeben. Dies ist wichtig, wenn das Ziel mehreren Sitzungen hinzugefügt wird, die dasselbe Ereignis erfassen.<br /><br /> -<br />                                **Synchron**. Das Ziel wird auf dem Thread ausgeführt, der das Ereignis erzeugt, bevor die Steuerung an die aufrufende Codezeile zurückgegeben wird.|  
|type_name|**nvarchar (60)**|Der Name für das pred_source-Objekt und das pred_compare-Objekt. Lässt NULL-Werte zu.|  
|type_package_guid|**uniqueidentifier**|Die GUID für das Paket, das den Typ verfügbar macht, auf dem dieses-Objekt angewendet wird. Lässt NULL-Werte zu.|  
|type_size|**int**|Größe des Datentyps in Bytes. Dies ist nur für gültige Objekttypen vorgesehen. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|To|Beziehung|  
|----------|--------|------------------|  
|sys.dm_xe_objects.package_guid|sys.dm_xe_packages.guid|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

