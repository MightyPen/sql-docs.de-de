---
title: Replikations-Agent-Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, administering
- Log Reader Agent, administering
- Queue Reader Agent, administering
- shared agents [SQL Server replication]
- Merge Agent, administering
- Distribution Agent, administering
- agents [SQL Server replication], administering
- replication cleanup jobs [SQL Server]
- administering replication, agents
- replication [SQL Server], administering
- independent agents [SQL Server replication]
ms.assetid: f27186b8-b1b2-4da0-8b2b-91f632c2ab7e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 00fc90be42bddd7feb43d96c9110def4db60835c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721806"
---
# <a name="replication-agent-administration"></a>Replikations-Agent-Verwaltung
  Die Replikations-Agents führen viele der der Replikation zugeordneten Aufgaben aus. Zu diesen Aufgaben gehören das Erstellen von Kopien des Schemas und der Daten, das Ermitteln von Aktualisierungen auf dem Verleger oder dem Abonnenten und das Weitergeben von Änderungen zwischen Servern. Standardmäßig werden Replikations- [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agents Unterauftrags Schritten des-Agents ausgeführt. Bei den Agents handelt es sich einfach nur um ausführbare Dateien, d. h., sie können auch direkt von der Befehlszeile und von Batchskripts aus aufgerufen werden. Jeder Replikations-Agent unterstützt einen Satz von Laufzeitparametern, mit denen gesteuert wird, wie der Agent ausgeführt wird. Diese Parameter werden in einem Agentprofil oder auf der Befehlszeile angegeben.  
  
> [!IMPORTANT]  
>  Standardmäßig ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Dienst bei der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deaktiviert, es sei denn, Sie haben den automatischen Start des Diensts während der Installation explizit ausgewählt.  
  
 Die Replikations-Agentdateien befinden sich unter [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]\COM. Die folgende Tabelle enthält eine Aufstellung der Namen der ausführbaren Replikationsdateien und der Dateien. Klicken Sie auf den Link für einen Agent, um sich die zugehörige Parameterreferenz anzeigen zu lassen.  
  
|Ausführbare Agent-Dateien|Dateiname|  
|----------------------|---------------|  
|[Replication Snapshot Agent](replication-snapshot-agent.md)|snapshot.exe|  
|[Replication Distribution Agent](replication-distribution-agent.md)|distrib.exe|  
|[Replikationsprotokolllese-Agent](replication-log-reader-agent.md)|logread.exe|  
|[Replication Queue Reader Agent](replication-queue-reader-agent.md)|qrdrsvc.exe|  
|[Replication Merge Agent](replication-merge-agent.md)|replmerg.exe|  
  
 Zusätzlich zu den Replikations-Agents besitzt die Replikation eine Reihe von Aufträgen, die geplante und Bedarfswartungen ausführen.  
  
 **So führen Sie Agents und Wartungsaufträge aus**  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]und Replikations Monitor: [ein Replikations-Agent &#40;SQL Server Management Studio&#41;wird gestartet und beendet ](start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
-   Replikationsprogrammierung: [Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md)  
  
## <a name="agent-profiles"></a>Agentprofile  
 Wenn die Replikation konfiguriert wird, wird ein Satz Agentprofile auf dem Verteiler installiert. Ein Agentprofil enthält eine Reihe Parameter, die bei jeder Ausführung des Agents zur Anwendung kommen: Jeder Agent meldet sich während seines Startprozesses beim Verteiler an und fragt die Parameter in seinem Profil ab. Die Replikation stellt ein Standardprofil für jeden Agent und zusätzliche vordefinierte Profile für den Protokolllese-Agent, den Verteilungs-Agent und den Merge-Agent bereit. Neben den bereitgestellten Profilen können Sie Profile erstellen, die sich für Ihre Anwendungsanforderungen eignen. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 Informationen zum direkten Angeben von Befehlszeilenparametern finden Sie unter [ Ausführbare Konzepte für die Programmierung von Replikations-Agents](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="monitoring-replication-agents"></a>Überwachen der Replikations-Agents  
 Im Replikationsmonitor können Sie Informationen zu den einzelnen Replikations-Agents anzeigen und agentbezogene Aufgaben ausführen. Die folgende Liste enthält alle Agents, die Registerkarten im Replikationsmonitor, auf denen die Agents zu finden sind, und einen Verweis darauf, wo Sie Informationen zum Zugreifen auf die jeweilige Registerkarte finden:  
  
-   Die folgenden Agents sind Veröffentlichungen im Replikationsmonitor zugeordnet:  
  
    -   Momentaufnahme-Agent  
  
    -   Protokolllese-Agent  
  
    -   Warteschlangenlese-Agent  
  
     Zugreifen auf Informationen und Tasks, die diesen Agents zugeordnet sind, über die Registerkarte **Agents** . Weitere Informationen finden Sie unter [Anzeigen von Informationen und Ausführen von Aufgaben mithilfe des Replikations Monitors](../monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Die folgenden Agents sind Abonnements im Replikationsmonitor zugeordnet:  
  
    -   Verteilungs-Agent  
  
    -   Merge-Agent  
  
     Auf die Informationen und Aufgaben im Zusammenhang mit diesen Agents kann über die folgenden Registerkarten zugegriffen werden: **Überwachungsliste für Abonnements** (verfügbar für jeden Verleger) bzw. **Alle Abonnements** (verfügbar für jede Veröffentlichung). Weitere Informationen finden Sie unter [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](../monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
## <a name="independent-and-shared-agents"></a>Unabhängige und freigegebene Agents  
 Ein unabhängiger Agent ist ein Agent, der ein Abonnement bedient. Ein freigegebener Agent bedient mehrere Abonnements. Wenn mehrere Abonnements, die denselben freigegebenen Agent verwenden, synchronisiert werden müssen, warten sie standardmäßig in einer Warteschlange. Der freigegebene Agent bedient die Abonnements einzeln nacheinander. Die Latenzzeit wird reduziert, wenn unabhängige Agents verwendet werden, da der Agent immer dann bereitsteht, wenn das Abonnement synchronisiert werden muss. Die Mergereplikation verwendet grundsätzlich unabhängige Agents, während die Transaktionsreplikation standardmäßig unabhängige Agents nur für Veröffentlichungen verwendet, die im Assistenten für neue Veröffentlichung erstellt wurden (in früheren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Versionen hat die Transaktionsreplikation standardmäßig freigegebene Agents verwendet).  
  
## <a name="replication-maintenance-jobs"></a>Aufträge zur Replikationswartung  
 Die Replikation verwendet die folgenden Aufträge zum Ausführen von geplanten und Bedarfswartungen.  
  
|Bereinigungsauftrag|BESCHREIBUNG|Standardzeitplan|  
|------------------|-----------------|----------------------|  
|Agentverlaufscleanup: Verteilung|Entfernt Verlaufseinträge des Replikations-Agents aus der Verteilungsdatenbank.|Wird alle zehn Minuten ausgeführt.|  
|Verteilungscleanup: Verteilung|Entfernt replizierte Transaktionen aus der Verteilungsdatenbank. Deaktiviert Abonnements, die innerhalb der maximalen Beibehaltungsdauer für Verteilung nicht synchronisiert wurden.|Wird alle zehn Minuten ausgeführt.|  
|Cleanup abgelaufener Abonnements|Ermittelt und entfernt abgelaufene Abonnements aus Veröffentlichungsdatenbanken.|Wird täglich um 1:00 Uhr nachts ausgeführt.|  
|Abonnements mit Datenüberprüfungsfehlern erneut initialisieren|Ermittelt alle Abonnements mit Datenüberprüfungsfehlern und kennzeichnet diese für eine erneute Initialisierung. Bei der nächsten Ausführung des Merge-Agents oder Verteilungs-Agents wird auf die Abonnenten eine neue Momentaufnahme angewendet.|Kein Standardzeitplan (nicht standardmäßig aktiviert).|  
|Überprüfung des Replikations-Agents|Ermittelt Replikations-Agents, die keinen Verlauf protokollieren. Schreibt in das [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Ereignisprotokoll, wenn ein Auftragsschritt einen Fehler erzeugt.|Wird alle zehn Minuten ausgeführt.|  
|Aktualisierung für die Replikationsüberwachung für die Verteilung|Aktualisiert die vom Replikationsmonitor verwendeten zwischengespeicherten Abfragen.|Wird fortlaufend ausgeführt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../monitoring-replication.md)  
  
  
