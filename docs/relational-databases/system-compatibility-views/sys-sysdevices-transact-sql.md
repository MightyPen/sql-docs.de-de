---
title: sys. sysdevices (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
author: rothja
ms.author: jroth
ms.openlocfilehash: 9cbd14a7ce8dd1cfb1571874a83a615065200014
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053524"
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Sicherungsdatei auf dem Datenträger und auf Band sowie für jede Datenbankdatei.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Logischer Name der Sicherungs- oder Datenbankdatei.|  
|**Größe**|**int**|Größe der Datei in Seiten mit einer Größe von 2 Kilobytes (KB)|  
|**Preis**|**int**|Nur aus Gründen der Abwärtskompatibilität beibehalten.|  
|**hochrangiger**|**int**|Nur aus Gründen der Abwärtskompatibilität beibehalten.|  
|**Stands**|**smallint**|Bitmuster, das den Medientyp anzeigt:<br /><br /> 1 = Standarddatenträger<br /><br /> 2 = Physischer Datenträger<br /><br /> 4 = Logischer Datenträger<br /><br /> 8 = Header auslassen<br /><br /> 16 = Sicherungsdatei<br /><br /> 32 = Serielle Schreibvorgänge<br /><br /> 4096 = Schreibgeschützt|  
|**CntrlType**|**smallint**|Controllertyp:<br /><br /> 0 = Nicht-CD-ROM-Datenbankdatei<br /><br /> 2 = Sicherungsdatei auf Datenträger<br /><br /> 3 - 4 = Sicherungsdatei auf Diskette<br /><br /> 5 = Sicherungsdatei auf Band<br /><br /> 6 = Named Pipe-Datei|  
|**phyname**|**nvarchar(260)**|Name der physischen Datei|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitäts Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
