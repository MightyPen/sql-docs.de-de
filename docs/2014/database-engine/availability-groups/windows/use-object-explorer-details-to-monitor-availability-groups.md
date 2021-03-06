---
title: Verwenden der Objekt-Explorer Details zum Überwachen von Verfügbarkeits Gruppen (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.OEdetails.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: 84affc47-40e0-43d9-855e-468967068c35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5545b36aba250a04744b66abad5434f8573c053e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62788323"
---
# <a name="use-the-object-explorer-details-to-monitor-availability-groups-sql-server-management-studio"></a>Verwenden der Details zum Objekt-Explorer zum Überwachen von Verfügbarkeitsgruppen (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie der Bereich **Details zum Objekt-Explorer** von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] verwendet wird, um vorhandene AlwaysOn-Verfügbarkeitsgruppen, -Verfügbarkeitsreplikate und -Verfügbarkeitsdatenbanken zu überwachen und zu verwalten.  
  
> [!NOTE]  
>  Informationen zum Verwenden des Bereichs mit Details zum Objekt-Explorer finden Sie unter [Detailbereich des Objekt-Explorers](../../../ssms/object/object-explorer-details-pane.md).  
  
-   Vorbereitungen **:**[Voraussetzungen](#Prerequisites)    
  
-   So **Überwachen Sie eine Verfügbarkeits Gruppe mit:**[SQL Server Management Studio](#SSMSProcedure)    
  
-   **Objekt-Explorer Details:**  
  
     [Verfügbarkeits Gruppen Details](#AvGroupsDetails)  
  
     [Verfügbarkeits Replikat](#AvReplicaDetails)  
  
     [Verfügbarkeits Datenbank-Details](#AvDbDetails)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Voraussetzungen  
 Sie müssen mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (Serverinstanz) verbunden sein, die entweder das primäre Replikat oder ein sekundäres Replikat hostet.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **Überwachen von Verfügbarkeits Gruppen, Verfügbarkeits Replikaten und Verfügbarkeits Datenbanken**  
  
1.  Klicken Sie im Menü **Ansicht**auf **Details zum Objekt-Explorer** , oder drücken Sie F7.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] her, auf der Sie eine Verfügbarkeitsgruppe überwachen möchten, und klicken Sie auf den Servernamen, um die Serverstruktur zu erweitern.  
  
3.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** und den Knoten **Verfügbarkeitsgruppen** .  
  
4.  Der Bereich **Details zum Objekt-Explorer** zeigt jede Verfügbarkeitsgruppe an, für die die verbundene Serverinstanz ein Replikat hostet. Für jede Verfügbarkeitsgruppe zeigt die Spalte **Serverinstanz (primär)** den Namen der Serverinstanz an, die derzeit das primäre Replikat hostet.  Um weitere Informationen zu einer bestimmten Verfügbarkeitsgruppe anzuzeigen, wählen Sie diese im Objekt-Explorer aus.  
  
5.  Der Bereich **Details zum Objekt-Explorer** zeigt dann die Knoten **Verfügbarkeitsreplikate** und **Verfügbarkeitsdatenbanken** für diese Verfügbarkeitsgruppe an:  
  
    -   Wenn Sie den Knoten **Verfügbarkeitsgruppe** im Objekt-Explorer erweitern und den Knoten **Verfügbarkeitsreplikate** auswählen, werden im Bereich **Details zum Objekt-Explorer** Informationen zu jedem Verfügbarkeitsreplikat in der Gruppe angezeigt. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Verfügbarkeitsreplikatdetails](#AvReplicaDetails).  
  
         Um Vorgänge auf mehreren Verfügbarkeitsreplikaten auszuführen, wählen Sie diese aus, und klicken Sie mit der rechten Maustaste, um ein Kontextmenü zu öffnen, das die verfügbaren Befehle auflistet.  
  
    -   Wenn Sie den Knoten **Verfügbarkeitsgruppe** im Objekt-Explorer erweitern und den Knoten **Verfügbarkeitsdatenbanken** auswählen, werden im Bereich **Details zum Objekt-Explorer** Informationen zu jeder Verfügbarkeitsdatenbank in der Gruppe angezeigt. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Verfügbarkeitsdatenbank-Details](#AvDbDetails).  
  
         Um Vorgänge auf mehreren Verfügbarkeitsdatenbanken auszuführen, wählen Sie diese aus, und klicken Sie mit der rechten Maustaste, um ein Kontextmenü zu öffnen, das die verfügbaren Befehle auflistet.  
  
##  <a name="AvGroupsDetails"></a>Details zu Verfügbarkeits Gruppen  
 Im Detailbildschirm **Verfügbarkeitsgruppen** werden die folgenden Spalten angezeigt:  
  
 **Name**  
 Führt die Listenerordner **Verfügbarkeitsreplikate**, **Verfügbarkeitsdatenbanken**und **Verfügbarkeitsgruppe** der ausgewählten Verfügbarkeitsgruppe auf.  
  
##  <a name="AvReplicaDetails"></a>Verfügbarkeits Replikat  
 Im Detailbildschirm **Verfügbarkeitsreplikat** werden die folgenden Spalten angezeigt:  
  
 **Serverinstanz**  
 Zeigt den Namen der Serverinstanz an, die das Verfügbarkeitsreplikat hostet, zusammen mit einem Symbol, das den aktuellen Verbindungsstatus der Serverinstanz zur lokalen Serverinstanz angibt.  
  
 **Spielen**  
 Gibt die aktuelle Rolle des Verfügbarkeitsreplikats an, entweder **Primär** oder **Sekundär**. Informationen über [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Rollen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
 **Verbindungs Modus in sekundärer Rolle**  
 Gibt an, ob die Datenbanken eines bestimmten Verfügbarkeitsreplikats, das die sekundäre Rolle einnimmt (das heißt, als sekundäres Replikat dient), Verbindungen von Clients akzeptieren können.  
  
 Die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Verbindungen nicht zulassen**|Es sind keine direkten Verbindungen zu den Verfügbarkeitsdatenbanken zulässig, wenn dieses Verfügbarkeitsreplikat als sekundäres Replikat dient. Sekundäre Datenbanken sind nicht für Lesezugriff verfügbar.|  
|**Nur Verbindungen für beabsichtigte Lesevorgänge zulassen**|Es sind nur direkte, schreibgeschützte Verbindungen zulässig, wenn dieses Replikat als sekundäres Replikat dient. Alle Datenbanken im Replikat sind für den Lesezugriff verfügbar.|  
|**Alle Verbindungen zulassen**|Es sind alle Verbindungen zu diesen Datenbanken für den schreibgeschützten Zugriff zulässig, wenn dieses Replikat als sekundäres Replikat dient.|  
  
 **Verbindungsstatus**  
 Gibt an, ob ein sekundäres Replikat derzeit mit dem primären Replikat verbunden ist. Die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Koppelt**|Gibt bei einem Remoteverfügbarkeitsreplikat an, dass es vom lokalen Verfügbarkeitsreplikat getrennt ist. Die Antwort des lokalen Replikats auf den Status "Getrennt" hängt wie folgt von dessen Rolle ab:<br /><br /> Wenn auf dem primären Replikat ein sekundäres Replikat getrennt ist, werden die sekundären Datenbanken auf dem primären Replikat als **Nicht synchronisiert** gekennzeichnet, und das primäre Replikat wartet, bis das sekundäre Replikat wieder verbunden ist.<br /><br /> Wird erkannt, dass das sekundäre Replikat getrennt ist, wird versucht, die Verbindung des sekundären Replikats mit dem primären Replikat wiederherzustellen.|  
|**Hängt**|Ein Remoteverfügbarkeitsreplikat, das derzeit mit dem lokalen Replikat verbunden ist.|  
|**NULL**|Wenn das lokale Replikat ein sekundäres Replikat ist, ist dieser Wert für andere sekundäre Replikate NULL.|  
  
 **Synchronisierungs Status**  
 Gibt an, ob ein sekundäres Replikat gerade mit dem primärem Replikat synchronisiert wird. Die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Nicht synchronisiert**|Die Datenbank ist nicht synchronisiert oder wurde noch nicht mit der Verfügbarkeitsgruppe verknüpft.|  
|**Synchronisiert**|Die Datenbank ist mit der primären Datenbank auf dem aktuellen primären Replikat (falls vorhanden) oder auf dem letzten primären Replikat synchronisiert.<br /><br /> Hinweis: Im Leistungsmodus befindet sich die Datenbank nie im Status "Synchronisiert".|  
|**NULL**|Unbekannter Status. Dieser Wert tritt auf, wenn die lokale Serverinstanz nicht mit dem WSFC-Failovercluster kommunizieren kann (d. h., der lokale Knoten ist nicht Teil des WSFC-Quorums).|  
  
> [!NOTE]  
>  Informationen zu Leistungsindikatoren für Verfügbarkeitsreplikate finden Sie unter [SQL Server, Verfügbarkeitsreplikat](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).  
  
##  <a name="AvDbDetails"></a>Verfügbarkeits Datenbank-Details  
 Im Detailbildschirm **Verfügbarkeitsdatenbank** werden die folgenden Eigenschaften der Verfügbarkeitsdatenbanken in einer bestimmten Verfügbarkeitsgruppe angezeigt:  
  
 **Name**  
 Der Name der Verfügbarkeitsdatenbank.  
  
 **Synchronisierungs Status**  
 Gibt an, ob die Verfügbarkeitsdatenbank gerade mit dem primärem Replikat synchronisiert wird.  
  
 Folgende Werte sind für den Synchronisierungsstatus möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|Wird synchronisiert|Die sekundäre Datenbank hat die Transaktionsprotokoll-Datensätze für die primäre Datenbank empfangen, die noch nicht auf den Datenträger geschrieben (festgeschrieben) wurden.<br /><br /> Hinweis: Im Modus mit asynchronem Commit lautet der Synchronisierungsstatus immer **Wird synchronisiert**.|  
  
 **Gesperrt**  
 Gibt an, ob die Verfügbarkeitsdatenbank gerade online ist. Die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**Gesperrt**|Dieser Status gibt an, dass die Datenbank lokal angehalten wird und manuell fortgesetzt werden muss.<br /><br /> Auf dem primären Replikat ist der Wert für eine sekundäre Datenbank unzuverlässig. Um zuverlässig zu bestimmen, ob eine sekundäre Datenbank angehalten wird, fragen Sie sie auf dem sekundären Replikat ab, das die Datenbank hostet.|  
|**Nicht verknüpft**|Gibt an, dass die sekundäre Datenbank entweder nicht mit der Verfügbarkeitsgruppe verknüpft wurde oder aus der Gruppe entfernt wurde.|  
|**Internet**|Gibt an, dass die Datenbank nicht auf dem lokalen Verfügbarkeitsreplikat angehalten wird und dass die Datenbank verbunden ist.|  
|**Nicht verbunden**|Gibt an, dass das sekundäre Replikat derzeit keine Verbindung mit dem primären Replikat herstellen kann.|  
  
> [!NOTE]  
>  Weitere Informationen zu Leistungsindikatoren für Verfügbarkeitsdatenbanken finden Sie unter [SQL Server, Datenbankreplikat](../../../relational-databases/performance-monitor/sql-server-database-replica.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_os_performance_counters &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)   
 [Verwenden Sie das AlwaysOn-Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)   
 [Anzeigen der Eigenschaften der Verfügbarkeits Gruppe &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md)   
 [Anzeigen von Verfügbarkeitsreplikateigenschaften &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)  
  
  
