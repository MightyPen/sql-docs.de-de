---
title: MSSQL_ENG002627 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002627 error
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a102991d08085f093e08a068a3d3127c9d7f7fc6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62666696"
---
# <a name="mssql_eng002627"></a>MSSQL_ENG002627
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2627|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name|–|  
|Meldungstext|Verletzung der %1!s!-Einschränkung '%2!s!'. Ein doppelter Schlüssel kann in das „%.\*ls“-Objekt nicht eingefügt werden.|  
  
## <a name="explanation"></a>Erklärung  
 Das ist ein allgemeiner Fehler, der unabhängig davon ausgelöst werden kann, ob eine Datenbank repliziert wird. Bei replizierten Datenbanken wird der Fehler in der Regel ausgelöst, weil Primärschlüssel in der Topologie nicht richtig verwaltet wurden. In einer verteilten Umgebung muss unbedingt sichergestellt werden, dass in mehreren Knoten nicht der gleiche Wert in eine Primärschlüsselspalte oder eine andere eindeutige Spalte eingefügt wird. Die folgenden Ursachen können zugrunde liegen:  
  
-   Einfügungen und Updates an einer Zeile finden in mehreren Knoten statt. Die Mergereplikation und aktualisierbare Abonnements für Transaktionsreplikationen stellen jeweils eine Konflikterkennung und -lösung bereit. Dennoch ist es besser, eine bestimmte Zeile nur in einem Knoten einzufügen oder zu aktualisieren. Die Peer-zu-Peer-Transaktionsreplikation stellt keine Konflikterkennung und -lösung bereit. Einfügungen und Updates müssen partitioniert werden.  
  
-   Auf einem Abonnenten wurde eine Zeile eingefügt, die schreibgeschützt sein sollte. Abonnenten von Momentaufnahmeveröffentlichungen sollten als schreibgeschützt behandelt werden, ebenso wie Abonnenten von Transaktionsveröffentlichungen, außer es werden aktualisierbare Abonnements oder die Peer-zu-Peer-Transaktionsreplikation verwendet.  
  
-   Es wird eine Tabelle mit einer Identitätsspalte verwendet, die Spalte wird jedoch nicht ordnungsgemäß verwaltet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Die erforderliche Aktion hängt davon ab, weshalb der Fehler ausgelöst wurde:  
  
-   Einfügungen und Updates an einer Zeile finden in mehreren Knoten statt.  
  
     Unabhängig vom Typ der verwendeten Replikation wird empfohlen, Einfügungen und Updates möglichst zu partitionieren, da dies den Verarbeitungsaufwand bei der Konflikterkennung und -lösung reduziert. Bei der Peer-zu-Peer-Transaktionsreplikation ist eine Partitionierung von Einfügungen und Updates erforderlich. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
-   Auf einem Abonnenten wurde eine Zeile eingefügt, die schreibgeschützt sein sollte.  
  
     Fügen Sie auf dem Abonnenten keine Zeilen ein und aktualisieren Sie keine Zeilen, es sei denn Sie verwenden die Mergereplikation, die Transaktionsreplikation mit aktualisierbaren Abonnements oder die Peer-zu-Peer-Transaktionsreplikation.  
  
-   Es wird eine Tabelle mit einer Identitätsspalte verwendet, die Spalte wird jedoch nicht ordnungsgemäß verwaltet.  
  
     Bei der Mergereplikation und der Transaktionsreplikation mit aktualisierbaren Abonnements sollten Identitätsspalten automatisch durch die Replikation verwaltet werden. Bei der Peer-zu-Peer-Transaktionsreplikation müssen sie manuell verwaltet werden. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](publish/replicate-identity-columns.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [Mergereplikation](merge/merge-replication.md)   
 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)   
 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
