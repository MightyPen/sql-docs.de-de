---
title: sys. sysusers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysusers
- sys.sysusers_TSQL
- sysusers_TSQL
- sysusers
dev_langs:
- TSQL
helpviewer_keywords:
- sysusers system table
- sys.sysusers compatibility view
ms.assetid: 5f0e6a8d-c983-44f6-97e9-aab5bff67d18
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1b8bec28a2e7778a449cb36aeee81481a311c6b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018062"
---
# <a name="syssysusers-transact-sql"></a>sys.sysusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jeden [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzer, jede Windows [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Gruppe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jeden Benutzer oder jede Rolle in der Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**UID**|**smallint**|In dieser Datenbank eindeutiger Benutzername.<br /><br /> 1 = Datenbankbesitzer<br /><br /> Führt zu einem Überlauf oder gibt NULL zurück, wenn die Anzahl von Benutzern und Rollen 32.767 übersteigt.|  
|**Stands**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**name**|**sysname**|Der in dieser Datenbank eindeutige Benutzer- oder Gruppenname.|  
|**sid**|**varbinary(85)**|Sicherheitsbezeichner für diesen Eintrag.|  
|**Rollen**|**varbinary (2048)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**mit "up"**|**datetime**|Datum, an dem das Konto hinzugefügt wurde.|  
|**Update Date**|**datetime**|Datum, an dem das Konto zuletzt geändert wurde.|  
|**altuid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> Führt zu einem Überlauf oder gibt NULL zurück, wenn die Anzahl von Benutzern und Rollen 32.767 übersteigt.|  
|**anmelden**|**varbinary (256)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**ü**|**smallint**|ID der Gruppe, zu der dieser Benutzer gehört. Wenn **uid** mit **gid**identisch ist, definiert dieser Eintrag eine Gruppe. Führt zu einem Überlauf oder gibt NULL zurück, wenn die kombinierte Anzahl von Gruppen und Benutzern 32.767 übersteigt.|  
|**Environ**|**varchar (255)**|Reserviert.|  
|**hasdbaccess**|**int**|1 = Konto hat Datenbankzugriff.|  
|**IsLogin**|**int**|1 = Konto ist eine Windows-Gruppe, ein Windows-Benutzer oder ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer mit einem Anmeldekonto.|  
|**isntname**|**int**|1 = Konto ist eine Windows-Gruppe oder ein Windows-Benutzer.|  
|**Isntgroup**|**int**|1 = Konto ist eine Windows-Gruppe.|  
|**isntuser**|**int**|1 = Konto ist ein Windows-Benutzer.|  
|**issqluser**|**int**|1 = Konto ist ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer.|  
|**isalias**|**int**|1 = Konto wird als Alias für einen anderen Benutzer verwendet.|  
|**issqlrole**|**int**|1 = Konto ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Rolle.|  
|**isapprole**|**int**|1 = Konto ist eine Anwendungsrolle.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitäts Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
