---
title: MSpeer_conflictdetectionconfigresponse (T-SQL)
description: Beschreibt die gespeicherte Prozedur MSPeer_conflictdetectionconfigureresponse, die in der Peer-zu-Peer-Replikation verwendet wird, um die Antwort jedes Knotens auf eine topologieübergreifende Konfigurations neufrage zu speichern.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_conflictdetectionconfigresponse
- MSpeer_conflictdetectionconfigresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigureresponse
ms.assetid: 2685fb66-731d-40f7-af4b-596b9222c5d4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ed3a127d2527b35c301ab7f3d05305c4f8d2ced
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75322129"
---
# <a name="mspeer_conflictdetectionconfigresponse-transact-sql"></a>MSpeer_conflictdetectionconfigresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird in der Peer-zu-Peer-Replikation verwendet, um die Antwort jedes Knotens auf eine topologieübergreifende Konfigurationsanforderung zu speichern. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|request_id|**int**|Identifiziert einen Konflikt Konfigurations Anforderungs Eintrag in der [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md) Tabelle.|  
|peer_node|**sysname**|Name der Serverinstanz, die die Antwort generiert hat.|  
|peer_db|**sysname**|Abonnementdatenbank auf dem Peer, der die Antwort generiert hat.|  
|peer_version|**sysname**|Kennzeichnet die Versionsnummer des Verlegers|  
|peer_db_version|**sysname**|Kennzeichnet die Versionsnummer der Peer-Datenbank.|  
|is_peer|**bit**|Gibt an, ob ein Knoten ein schreibgeschützter Abonnent ist. Der Wert **0** gibt einen schreibgeschützten Abonnenten an.|  
|conflict_detection_enabled|**bit**|Gibt an, ob die Konflikterkennung für die Topologie aktiviert ist.|  
|originator_id|**varbinary(16)**|Identifiziert jeden Knoten in der Topologie zum Zweck der Konflikterkennung. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|peer_conflict_retention|**int**|Zeitraum in Tagen, für den Metadaten in Konflikttabellen gespeichert werden.|  
|peer_subscriptions|**XML**|Informationen über den Knoten, der auf die Anforderung reagiert hat.|  
|progress_phase|**nvarchar (32)**|Identifiziert die aktuelle Phase der Verarbeitung mit einem der folgenden Werte:<br /><br /> Gestartet<br /><br /> Peerversion erfasst<br /><br /> Status erfasst|  
|modified_date|**datetime**|Datum und Uhrzeit, zu der eine Phase abgeschlossen wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
