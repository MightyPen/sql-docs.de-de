---
title: Überprüfen von Partitionsinformationen für einen Mergeabonnenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3bada5fc49dc344510164260330699b60a3288cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255310"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a>Überprüfen von Partitionsinformationen für einen Mergeabonnenten
  Beim Definieren eines parametrisierten Zeilenfilters für eine Mergeveröffentlichung kommt eine Funktion zum Einsatz, die die Abonnenteninformationen, wie z. B. den Benutzernamen des Abonnenten, referenziert. Standardmäßig überprüft die Replikation die Abonnenteninformationen auf der Basis dieser Funktion. Erst dann erfolgt die jeweilige Synchronisierung. Die Überprüfung erfolgt auch immer dann, wenn eine Momentaufnahme auf den Abonnenten angewendet wird. Mit der Überprüfung wird sichergestellt, dass die Daten ordnungsgemäß für die einzelnen Abonnenten partitioniert sind. Das Überprüfungsverhalten wird von der **validate_subscriber_info**-Veröffentlichungseigenschaft gesteuert, die mithilfe von [sp_changemergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) oder auf der Seite **Abonnementoptionen** des Dialogfelds **Veröffentlichungseigenschaften** geändert werden kann. Weitere Informationen zum Ändern der Veröffentlichungseigenschaften finden Sie unter [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
## <a name="how-partition-validation-works"></a>Funktionsweise der Partitionsüberprüfung  
 Wenn eine Veröffentlichung z. B. mithilfe der **SUSER_SNAME()**-Funktion gefiltert wird, weist der Merge-Agent auf der Basis der für den **SUSER_SNAME()** -Ausdruck geltenden Daten jedem Abonnenten die Anfangsmomentaufnahme zu.  
  
 Wenn die Überprüfung aktiviert ist und der Abonnent für die nächste Synchronisierung erneut eine Verbindung mit dem Verleger herstellt, überprüft der Merge-Agent die Informationen auf dem Abonnenten und stellt sicher, dass die Partition auf den Abonnenten mit der Partition identisch ist, die in der Anfangsmomentaufnahme gesendet wurde. Bei allen nachfolgenden Merge- bzw. Momentaufnahmeanwendungen überprüft der Merge-Agent die Partition der einzelnen Abonnenten.  
  
 Wenn der Merge-Agent feststellt, dass die im Filterausdruck verwendete Funktion einen anderen Wert zurückgibt als in der Anfangsmomentaufnahme, schlägt die Merge- bzw. Momentaufnahmeanwendung fehl, und das Abonnement des Abonnenten muss möglicherweise erneut initialisiert werden. Diese erneute Initialisierung kann nötig werden, um Probleme zu vermeiden, die sich aus der Änderung der Mergeeinstellungen eines Abonnenten ergeben können. Es reicht möglicherweise aber auch aus, die Informationen auf dem Abonnenten, wie z. B. den Benutzernamen, auf den Wert zum Zeitpunkt der ursprünglichen Momentaufnahme zurückzusetzen.  
  
 Beim Überprüfen einer Partition gleicht der Merge-Agent aber nicht nur die Partition mit den Werten ab, die von den in den Filterausdrücken verwendeten Funktionen zurückgegeben werden, sondern er kontrolliert auch, ob die Momentaufnahme generiert wurde, bevor Änderungen vorgenommen wurden, durch die sie ungültig geworden ist. Solche Änderungen können z. B. Metadaten-Cleanupoperationen oder Schemaänderungen sein. Wenn eine partitionierte Momentaufnahme zu alt ist, gibt der Merge-Agent einen Fehler zurück. In diesem Fall müssen Sie auf der Grundlage einer aktuellen regulären Momentaufnahme eine neue partitionierte Momentaufnahme für diesen Abonnenten generieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Häufig gestellte Fragen für Replikationsadministratoren](administration/frequently-asked-questions-for-replication-administrators.md)   
 [Bewährte Methoden für die Replikations Verwaltung](administration/best-practices-for-replication-administration.md)   
 [Abonnements erneut initialisieren](reinitialize-subscriptions.md)   
 [Überprüfen von replizierten Daten](validate-data-at-the-subscriber.md)  
  
  
