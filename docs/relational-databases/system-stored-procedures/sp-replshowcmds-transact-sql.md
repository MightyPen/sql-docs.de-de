---
title: sp_replshowcmds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96a32ea04fc53f1a0bf3a842a5e68cde5586ac29
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770880"
---
# <a name="sp_replshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt die Befehle für Transaktionen, die für die Replikation in lesbarem Format markiert sind, zurück. **sp_replshowcmds** können nur ausgeführt werden, wenn Clientverbindungen (einschließlich der aktuellen Verbindung) keine replizierten Transaktionen aus dem Protokoll lesen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Argumente  
`[ @maxtrans = ] maxtrans`Die Anzahl der Transaktionen, für die Informationen zurückgegeben werden sollen. *maxtrans* ist vom Datentyp **int**und hat den Standardwert **1**, womit die maximale Anzahl von Transaktionen mit ausstehender Replikation angegeben wird, für die **sp_replshowcmds** Informationen zurückgibt.  
  
## <a name="result-sets"></a>Resultsets  
 **sp_replshowcmds** ist eine Diagnose Prozedur, die Informationen über die Veröffentlichungs Datenbank zurückgibt, von der Sie ausgeführt wird.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**Binär (10)**|Sequenznummer des Befehls.|  
|**originator_id**|**int**|ID des Befehls Erstellers, immer **0**.|  
|**publisher_database_id**|**int**|ID der Verleger Datenbank, immer **0**.|  
|**article_id**|**int**|ID des Artikels.|  
|**type**|**int**|Der Typ des Befehls.|  
|**s**|**nvarchar (1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]s.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_replshowcmds** wird bei der Transaktions Replikation verwendet.  
  
 Mithilfe **sp_replshowcmds**können Sie Transaktionen anzeigen, die derzeit nicht verteilt sind (die im Transaktionsprotokoll verbleibenden Transaktionen, die nicht an den Verteiler gesendet wurden).  
  
 Clients, die **sp_replshowcmds** ausführen und innerhalb derselben Datenbank **sp_replcmds** , erhalten den Fehler 18752.  
  
 Um diesen Fehler zu vermeiden, muss der erste Client die Verbindung trennen oder die Rolle des Clients, da der Protokoll Leser durch Ausführen von **sp_replflush**freigegeben werden muss. Nachdem alle Clients den Protokoll Leser getrennt haben, können **sp_replshowcmds** erfolgreich ausgeführt werden.  
  
> [!NOTE]  
>  **sp_replshowcmds** sollten nur zum Beheben von Problemen bei der Replikation ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_replshowcmds**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehlermeldungen](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
