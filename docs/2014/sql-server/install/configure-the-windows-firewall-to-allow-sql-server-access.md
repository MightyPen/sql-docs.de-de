---
title: Konfigurieren der Windows-Firewall für den SQL Server-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Windows Firewall ports
- WMI firewall ports
- Windows Firewall [Database Engine]
- firewall systems, configuring
- advfirewall
- firewall systems
- rules firewall
- firewall systems, overview and port list
- 1433 TCP port
- portopening using netsh
- ports [SQL Server], TCP
- netsh to open firewall ports
ms.assetid: f55c6a0e-b6bd-4803-b51a-f3a419803024
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5dcbf0aae9c96e788fdbf9544114d226fa8f0bfd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73637855"
---
# <a name="configure-the-windows-firewall-to-allow-sql-server-access"></a>Configure the Windows Firewall to Allow SQL Server Access
  Durch Firewallsysteme kann der nicht autorisierte Zugriff auf Computerressourcen verhindert werden. Wenn eine Firewall aktiviert, aber nicht richtig konfiguriert ist, können Versuche der Verbindungsherstellung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] blockiert werden.  
  
 Um über eine Firewall auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen zu können, müssen Sie die Firewall auf dem Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entsprechend konfigurieren. Die Firewall ist eine Komponente von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Sie können auch eine Firewall von einem anderen Unternehmen installieren. In diesem Thema wird erläutert, wie die Windows-Firewall konfiguriert wird. Die Grundprinzipien gelten jedoch auch für andere Firewallprogramme.  
  
> [!NOTE]  
>  Dieses Thema bietet einen Überblick über die Firewallkonfiguration und fasst Informationen zusammen, die für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administrator interessant sind. Weitere Informationen zur Firewall sowie autorisierende Informationen für diese finden Sie in der Dokumentation der Firewall, z. B. in [Windows-Firewall mit erweiterter Sicherheit und IPsec](https://go.microsoft.com/fwlink/?LinkID=116904).  
  
 Benutzer, die mit dem Element **Windows-Firewall** in der Systemsteuerung und mit dem MMC-Snap-In (Microsoft Management Console) „Windows Firewall mit erweiterter Sicherheit“ vertraut sind und wissen, welche Firewalleinstellungen sie konfigurieren möchten, können direkt zu den Themen in der folgenden Liste wechseln:  
  
-   [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../../../2014/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
  
-   [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  

  
##  <a name="BKMK_basic"></a> Grundlegende Firewallinformationen  
 Firewalls überprüfen eingehende Pakete und vergleichen diese mit einer Gruppe von Regeln. Wenn die Regeln das Paket zulassen, leitet die Firewall das Paket an das TCP/IP-Protokoll zur zusätzlichen Verarbeitung weiter. Wenn die Regeln das Paket nicht zulassen, verwirft die Firewall das Paket und erstellt, wenn die Protokollierung aktiviert ist, einen Eintrag in der Firewallprotokolldatei.  
  
 Die Liste des zugelassenen Datenverkehrs wird auf eine der folgenden Arten aufgefüllt:  
  
-   Wenn der Computer, auf dem die Firewall aktiviert ist, die Kommunikation startet, erstellt die Firewall einen Eintrag in der Liste, sodass die Antwort zugelassen wird. Da die eingehende Antwort als angeforderter Datenverkehr betrachtet wird, müssen Sie dies nicht konfigurieren.  
  
-   Ein Administrator konfiguriert Ausnahmen für die Firewall. Dies ermöglicht entweder den Zugriff auf angegebene Programme, die auf dem Computer ausgeführt werden, oder den Zugriff auf angegebene Verbindungsports auf dem Computer. In diesem Fall akzeptiert der Computer den unangefordert eingehenden Datenverkehr, wenn er als Server, Listener oder Peer fungiert. Dieser Typ der Konfiguration muss durchgeführt werden, damit eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt werden kann.  
  
 Das Festlegen einer Firewallstrategie ist komplexer als die bloße Entscheidung, ob ein bestimmter Port geöffnet oder geschlossen werden sollte. Beim Entwickeln einer Firewallstrategie für Ihr Unternehmen sollten Sie sicherstellen, dass Sie alle Regeln und Konfigurationsoptionen berücksichtigen, die Ihnen zur Verfügung stehen. In diesem Thema werden nicht alle möglichen Firewalloptionen behandelt. Es wird empfohlen, die folgenden Dokumente zu beachten:  
  
 [Leitfaden "Windows-Firewall mit erweiterter Sicherheit"](https://go.microsoft.com/fwlink/?LinkId=116080)  
  
 [Entwurfs Handbuch für die Windows-Firewall mit erweiterter Sicherheit](https://go.microsoft.com/fwlink/?LinkId=116904)  
  
 [Introduction to Server and Domain Isolation](https://go.microsoft.com/fwlink/?LinkId=116081)  
  
##  <a name="BKMK_default"></a> Standardeinstellungen der Firewall  
 Der erste Schritt bei der Planung der Firewallkonfiguration ist die Bestimmung des aktuellen Status der Firewall Ihres Betriebssystems. Wenn das Betriebssystem aus einer vorherigen Version aktualisiert wurde, wurden die früheren Firewalleinstellungen möglicherweise beibehalten. Außerdem kann es sein, dass die Firewalleinstellungen von einem anderen Administrator oder von einer Gruppenrichtlinie in Ihrer Domäne geändert wurden.  
  
> [!NOTE]  
>  Das Einschalten der Firewall wirkt sich auf andere Programme aus, die auf diesen Computer zugreifen, wie z. B. die Datei- und Druckerfreigabe und Remotedesktopverbindungen. Administratoren sollten vor dem Anpassen der Firewalleinstellungen alle auf dem Computer ausgeführten Anwendungen berücksichtigen.  
  
##  <a name="BKMK_programs"></a> Programme zur Konfiguration der Firewall  
 Es gibt drei Möglichkeiten, die Einstellungen der Windows-Firewall zu konfigurieren.  
  
-   **Element "Windows-Firewall" in der Systemsteuerung**  
  
     Das Element **Windows-Firewall** kann in der Systemsteuerung geöffnet werden.  
  
    > [!IMPORTANT]  
    >  Änderungen, die in der Systemsteuerung am Element **Windows-Firewall** vorgenommenen werden, wirken sich nur auf das aktuelle Profil aus. Für mobile Geräte, wie z. B. einen Laptop, sollte das Element **Windows-Firewall** in der Systemsteuerung nicht verwendet werden, da sich das Profil ändern kann, wenn es in einer anderen Konfiguration angeschlossen wird. Dann ist das zuvor konfigurierte Profil nicht wirksam. Weitere Informationen zu Profilen finden Sie unter [Erste Schritte mit der Windows-Firewall mit erweiterter Sicherheit](https://go.microsoft.com/fwlink/?LinkId=116080).  
  
     Das Element **Windows-Firewall** in der Systemsteuerung ermöglicht Ihnen die Konfiguration grundlegender Optionen. Dabei handelt es sich z. B. um:  
  
    -   Ein- oder Ausschalten des Elements **Windows-Firewall** in der Systemsteuerung  
  
    -   Aktivieren und Deaktivieren von Regeln  
  
    -   Gewähren von Ausnahmen für Ports und Programme  
  
    -   Festlegen einiger Bereichseinschränkungen  
  
     Das Element **Windows-Firewall** in der Systemsteuerung eignet sich am besten für Benutzer, die mit der Konfiguration einer Firewall keine Erfahrung haben und grundlegende Firewalloptionen für nicht mobile Computer konfigurieren. Mithilfe des folgenden Verfahrens können Sie auch das Element **Windows-Firewall** in `run` der Systemsteuerung öffnen:  
  
    #### <a name="to-open-the-windows-firewall-item"></a>So öffnen Sie das Element „Windows-Firewall“  
  
    1.  Klicken Sie im Menü **Start** auf **Ausführen**, und geben Sie dann `firewall.cpl`ein.  
  
    2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
-   **Microsoft Management Console (MMC)**  
  
     Mithilfe des MMC-Snap-Ins „Windows-Firewall mit erweiterter Sicherheit“ können Sie erweiterte Firewalleinstellungen konfigurieren. Dieses Snap-In stellt die meisten Firewalloptionen in einer benutzerfreundlichen Form sowie alle Firewallprofile bereit. Weitere Informationen finden Sie unter [Verwenden des Snap-Ins „Windows-Firewall mit erweiterter Sicherheit“](#BKMK_WF_msc) weiter unten in diesem Thema.  
  
-   **Netsh**  
  
     Das Tool **netsh.exe** kann von einem Administrator verwendet werden, um Windows-basierte Computer an der Eingabeaufforderung oder mittels einer Batchdatei zu konfigurieren und zu überwachen **.** Mit dem Tool **netsh** können Sie die Kontextbefehle leiten, die Sie für das entsprechende Hilfsprogramm eingeben, und das Hilfsprogramm führt dann den Befehl aus. Ein Hilfsprogramm ist eine DLL-Datei (Dynamic Link Library), die die Funktionalität des Tools **netsh** erweitert, indem sie die Konfiguration, Überwachung und Unterstützung eines oder mehrerer Dienste, Hilfsprogramme oder Protokolle ermöglicht. Alle Betriebssysteme, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützen, haben ein Firewallhilfsprogramm. [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]verfügt auch über ein erweitertes Firewallhilfsprogramm namens " **advfirewall**". Die Details der Verwendung von **netsh** werden in diesem Thema nicht erläutert. Viele der beschriebenen Konfigurationsoptionen können jedoch mit **netsh** konfiguriert werden. Führen Sie beispielsweise über eine Eingabeaufforderung das folgende Skript aus, um TCP-Port 1433 zu öffnen:  
  
    ```  
    netsh firewall set portopening protocol = TCP port = 1433 name = SQLPort mode = ENABLE scope = SUBNET profile = CURRENT  
    ```  
  
     Im Folgenden finden Sie ein ähnliches Beispiel, in dem die Windows-Firewall für das Hilfsprogramm für die erweiterte Sicherheit verwendet wird:  
  
    ```  
    netsh advfirewall firewall add rule name = SQLPort dir = in protocol = tcp action = allow localport = 1433 remoteip = localsubnet profile = DOMAIN  
    ```  
  
     Weitere Informationen zu **netsh** finden Sie unter den folgenden Links:  
  
    -   [Verwenden des Tools "Netsh. exe" und der Befehls Zeilenschalter](https://support.microsoft.com/kb/242468)  
  
    -   [Verwenden des Kontexts "netsh advfirewall Firewall" anstelle des "netsh Firewall"-Kontexts, um das Verhalten der Windows-Firewall in Windows Server 2008 und Windows Vista zu steuern](https://support.microsoft.com/kb/947709)  
  
    -   [Der Befehl "netsh Firewall" in Verbindung mit dem Parameter "Profile = all" konfiguriert nicht das öffentliche Profil auf einem Windows Vista-basierten Computer.](https://support.microsoft.com/kb/947213)  
  
## <a name="ports-used-by-includessnoversionincludesssnoversion-mdmd"></a>Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Die folgenden Tabellen können Sie dabei unterstützen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendeten Ports zu identifizieren.  
  
###  <a name="BKMK_ssde"></a>Vom Datenbank-Engine verwendete Ports  
 In der folgenden Tabelle werden die häufig von [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendeten Ports aufgeführt.  
  
|Szenario|Port|Kommentare|  
|--------------|----------|--------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Standard Instanz, die über TCP ausgeführt wird|TCP-Port 1433|Dies ist der häufigste für die Firewall zulässige Port. Er gilt für Routineverbindungen mit der Standardinstallation von [!INCLUDE[ssDE](../../includes/ssde-md.md)] oder einer benannten Instanz, bei der es sich um die einzige auf dem Computer ausgeführte Instanz handelt. (Für benannte Instanzen gelten spezielle Bedingungen. Weitere Informationen finden Sie unter [Dynamische Ports](#BKMK_dynamic_ports) weiter unten in diesem Thema.)|  
|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der Standardkonfiguration|Der TCP-Port ist ein dynamischer Port, der zu dem Zeitpunkt bestimmt wird, zu dem die [!INCLUDE[ssDE](../../includes/ssde-md.md)] startet.|Weitere Informationen finden Sie in den Ausführungen im Abschnitt [Dynamische Ports](#BKMK_dynamic_ports) weiter unten. Wenn Sie benannte Instanzen verwenden, ist möglicherweise UDP-Port 1434 für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst erforderlich.|  
|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wenn sie für die Verwendung eines festen Ports konfiguriert sind|Die vom Administrator konfigurierte Portnummer.|Weitere Informationen finden Sie in den Ausführungen im Abschnitt [Dynamische Ports](#BKMK_dynamic_ports) weiter unten.|  
|Dedizierte Administratorverbindung|TCP-Port 1434 für die Standardinstanz. Andere Ports werden für benannte Instanzen verwendet. Überprüfen Sie das Fehlerprotokoll auf die Portnummer.|Standardmäßig werden Remoteverbindungen über die dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC) nicht aktiviert. Zum Aktivieren der Remote-DAC verwenden Sie das Facet für die Oberflächenkonfiguration. Weitere Informationen finden Sie unter [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md).|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser Dienst|UDP-Port 1434|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst lauscht auf einer benannten Instanz nach eingehenden Verbindungen und liefert dem Client die TCP-Portnummer, die dieser benannten Instanz entspricht. Normalerweise wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst immer dann gestartet, wenn benannte Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] verwendet werden. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst muss nicht gestartet werden, wenn der Client so konfiguriert ist, dass er eine Verbindung mit dem speziellen Port der benannten Instanz herstellt.|  
|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, die über einen HTTP-Endpunkt ausgeführt wird.|Kann angegeben werden, wenn ein HTTP-Endpunkt erstellt wird. Als Standard wird TCP-Port 80 für den CLEAR_PORT-Datenverkehr und 443 für den SSL_PORT-Datenverkehr verwendet.|Wird für eine HTTP-Verbindung über eine URL verwendet|  
|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Standardinstanz, die über einen HTTPS-Endpunkt ausgeführt wird.|TCP-Port 443|Wird für eine HTTPS-Verbindung über eine URL verwendet. HTTPS ist eine HTTP-Verbindung, die SSL (Secure Sockets Layer) verwendet.|  
|[!INCLUDE[ssSB](../../includes/sssb-md.md)]|TCP-Port 4022. Führen Sie die folgende Abfrage aus, um den verwendeten Port zu überprüfen:<br /><br /> `SELECT name, protocol_desc, port, state_desc`<br /><br /> `FROM sys.tcp_endpoints`<br /><br /> `WHERE type_desc = 'SERVICE_BROKER'`|Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSB](../../includes/sssb-md.md)] ist kein Standardport festgelegt, jedoch ist dies die herkömmliche, in Beispielen der Onlinedokumentation verwendete Konfiguration.|  
|Datenbankspiegelung|Vom Administrator ausgewählter Port. Führen Sie die folgende Abfrage aus, um den Port zu bestimmen:<br /><br /> `SELECT name, protocol_desc, port, state_desc FROM sys.tcp_endpoints`<br /><br /> `WHERE type_desc = 'DATABASE_MIRRORING'`|Für die Datenbankspiegelung ist kein Standardport festgelegt, in Beispielen der Onlinedokumentation wird jedoch TCP-Port 7022 verwendet. Es ist sehr wichtig, eine Unterbrechung eines bereits verwendeten Spiegelungsendpunkts zu vermeiden, insbesondere im Modus für hohe Sicherheit mit automatischem Failover. Die Firewallkonfiguration muss eine Unterbrechung des Quorums vermeiden. Weitere Informationen finden Sie unter [Angeben einer Servernetzwerkadresse &#40;Datenbankspiegelung&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md).|  
|Replikation|Für Replikationsverbindungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden die typischen regulären [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Ports (TCP-Port 1433 für die Standardinstanz usw.) verwendet.<br /><br /> Die Websynchronisierung und der FTP-/UNC-Zugriff für die Replikationsmomentaufnahme erfordern das Öffnen zusätzlicher Ports auf der Firewall. Zur Übertragung der Anfangsdaten und des Schemas zwischen unterschiedlichen Standorten kann für die Replikation FTP (TCP-Port 21), die Synchronisierung über HTTP (TCP-Port 80) oder die Dateifreigabe verwendet werden. Die Dateifreigabe verwendet die UDP-Ports 137 und 138 und den TCP-Port 139, wenn NetBIOS verwendet wird. Für die Dateifreigabe wird der TCP-Port 445 verwendet.|Bei der Synchronisierung über HTTP wird für die Replikation der IIS-Endpunkt (Ports, die dafür konfigurierbar sind, standardmäßig aber Port 80) verwendet, aber der IIS-Prozess stellt eine Verbindung mit Back-End- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über die Standardports (1433 für die Standardinstanz) her.<br /><br /> Bei der Websynchronisierung mittels FTP findet die FTP-Übertragung zwischen IIS und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger und nicht zwischen Abonnent und IIS statt.|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)]Debugger|TCP-Port 135<br /><br /> Siehe [Spezielle Überlegungen zu Port 135](#BKMK_port_135)<br /><br /> Die [IPsec](#BKMK_additional_ports) -Ausnahme ist möglicherweise auch erforderlich.|Bei Verwendung von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] müssen Sie außerdem auf dem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Hostcomputer **Devenv.exe** zur Ausnahmeliste hinzufügen und den TCP-Port 135 öffnen.<br /><br /> Bei Verwendung von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]müssen Sie außerdem auf dem [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] -Hostcomputer **ssms.exe** zur Ausnahmeliste hinzufügen und TCP-Port 135 öffnen. Weitere Informationen finden Sie unter [Konfigurieren des Transact-SQL-Debuggers](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md).|  
  
 Eine Schritt-für-Schritt-Anleitung zum Konfigurieren der Windows-Firewall für die [!INCLUDE[ssDE](../../includes/ssde-md.md)] finden Sie unter [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).  
  
####  <a name="BKMK_dynamic_ports"></a>Dynamische Ports  
 Standardmäßig verwenden benannte Instanzen (einschließlich [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) dynamische Ports. Dies bedeutet, dass immer dann, wenn die [!INCLUDE[ssDE](../../includes/ssde-md.md)] startet, ein verfügbarer Port identifiziert und die entsprechende Portnummer verwendet wird. Wenn es sich bei der benannten Instanz um die einzige von [!INCLUDE[ssDE](../../includes/ssde-md.md)] installierte Instanz handelt, wird wahrscheinlich TCP-Port 1433 verwendet. Wenn weitere Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert sind, wird wahrscheinlich ein anderer TCP-Port verwendet. Da sich der ausgewählte Port bei jedem Start von [!INCLUDE[ssDE](../../includes/ssde-md.md)] ändern kann, ist es schwierig, die Firewall so zu konfigurieren, dass der Zugriff auf die richtige Portnummer ermöglicht wird. Daher wird bei Verwendung einer Firewall eine Neukonfiguration von [!INCLUDE[ssDE](../../includes/ssde-md.md)] empfohlen, damit jedes Mal dieselbe Portnummer verwendet wird. Der betreffende Port wird als fester oder statischer Port bezeichnet. Weitere Informationen finden Sie unter [Konfigurieren eines Servers zur Überwachung eines bestimmten TCP-Ports &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
 Eine Alternative zum Konfigurieren einer benannten Instanz für das Lauschen auf einem festen Port ist die Erstellung einer Ausnahme für ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Programm wie z.B. **sqlservr.exe** (für [!INCLUDE[ssDE](../../includes/ssde-md.md)]) in der Firewall. Dies kann zwar zweckmäßig sein, aber die Portnummer wird nicht in der Spalte **Lokaler Port** auf der Seite **Eingehende Regeln** angezeigt, wenn Sie das MMC-Snap-In „Windows-Firewall mit erweiterter Sicherheit“ verwenden. Damit kann es schwieriger werden, zu verfolgen, welche Ports geöffnet sind. Ein weiterer Aspekt ist, dass ein Service Pack oder kumulatives Update den Pfad zur ausführbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datei ändern kann, wodurch die Firewallregel ungültig wird.  
  
> [!NOTE]  
>  Im folgenden Verfahren wird das Element **Windows-Firewall** in der Systemsteuerung verwendet. Mithilfe des MMC-Snap-Ins „Windows-Firewall mit erweiterter Sicherheit“ kann eine komplexere Regel konfiguriert werden. Dazu gehört das Konfigurieren einer Dienstausnahme, was nützlich sein kann, um einen tiefgreifenden Schutz zu ermöglichen. Siehe [Verwenden des Snap-Ins „Windows-Firewall mit erweiterter Sicherheit“](#BKMK_WF_msc) weiter unten.  
  
###### <a name="to-add-a-program-exception-to-the-firewall-using-the-windows-firewall-item-in-control-panel"></a>So fügen Sie der Firewall mithilfe des Elements „Windows-Firewall“ in der Systemsteuerung eine Programmausnahme hinzu  
  
1.  Klicken Sie unter dem Element **Windows-Firewall** in der Systemsteuerung auf der Registerkarte **Ausnahmen** auf **Programm hinzufügen**.  
  
2.  Navigieren Sie zum Speicherort der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die Sie durch die Firewall zulassen möchten, z. b. " **c:\Programme\Microsoft SQL server\mssql12. <instance_name> \MSSQL\Binn**", wählen Sie " **sqlservr. exe**" aus, und klicken Sie dann auf " **Öffnen**".  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Weitere Informationen über Endpunkte finden Sie unter [Konfigurieren der Datenbank-Engine zum Überwachen mehrerer TCP-Ports](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md) und [Endpunkte-Katalogsichten &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql).  
  
###  <a name="BKMK_ssas"></a>Von Analysis Services verwendete Ports  
 In der folgenden Tabelle werden die häufig von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendeten Ports aufgeführt.  
  
|Funktion|Port|Kommentare|  
|-------------|----------|--------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|TCP-Port 2383 für die Standardinstanz|Der Standardport für die Standardinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser Dienst|TCP-Port 2382, nur für eine benannte Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] notwendig|Clientverbindungsanforderungen für eine benannte Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], in denen keine Portnummer angegeben ist, werden an Port 2382 weitergeleitet. Dies ist der Port, auf dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser lauscht. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser leitet dann die Anforderung an den Port um, der von der benannten Instanz verwendet wird.|  
|
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zur Verwendung durch IIS/HTTP konfiguriert<br /><br /> (Die pivotfähig? Der Dienst verwendet http oder HTTPS.)|TCP-Port 80|Wird für eine HTTP-Verbindung über eine URL verwendet|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zur Verwendung durch IIS/HTTPS konfiguriert<br /><br /> (Die pivotfähig? Der Dienst verwendet http oder HTTPS.)|TCP-Port 443|Wird für eine HTTPS-Verbindung über eine URL verwendet. HTTPS ist eine HTTP-Verbindung, die SSL (Secure Sockets Layer) verwendet.|  
  
 Wenn Benutzer über IIS und das Internet auf [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zugreifen, müssen Sie den Port öffnen, den IIS überwacht, und diesen Port in der Clientverbindungszeichenfolge angeben. In diesem Fall müssen keine Ports für den direkten Zugriff auf [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] geöffnet sein. Der Standardport 2389 und Port 2382 sollten gemeinsam mit allen anderen Ports eingeschränkt werden, die nicht benötigt werden.  
  
 Eine Schritt-für-Schritt-Anleitung zum Konfigurieren der Windows-Firewall für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] finden Sie unter [Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../../../2014/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
###  <a name="BKMK_ssrs"></a>Von Reporting Services verwendete Ports  
 In der folgenden Tabelle werden die häufig von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verwendeten Ports aufgeführt.  
  
|Funktion|Port|Kommentare|  
|-------------|----------|--------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Webdienste|TCP-Port 80|Wird für eine HTTP-Verbindung mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] über eine URL verwendet. Die Verwendung der vorkonfigurierten Regel **WWW-Dienste (HTTP)** wird nicht empfohlen. Weitere Informationen finden Sie im Abschnitt [Interaktion mit anderen Firewallregeln](#BKMK_other_rules) weiter unten.|  
|
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zur Verwendung durch HTTPS konfiguriert|TCP-Port 443|Wird für eine HTTPS-Verbindung über eine URL verwendet. HTTPS ist eine HTTP-Verbindung, die SSL (Secure Sockets Layer) verwendet. Die Verwendung der vorkonfigurierten Regel **Sichere WWW-Dienste (HTTPS)** wird nicht empfohlen. Weitere Informationen finden Sie im Abschnitt [Interaktion mit anderen Firewallregeln](#BKMK_other_rules) weiter unten.|  
  
 Wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] oder [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] herstellt, müssen Sie auch die entsprechenden Ports für diese Dienste öffnen. Eine Schritt-für-Schritt-Anleitung zum Konfigurieren der Windows-Firewall für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] finden Sie unter [Konfigurieren einer Firewall für den Zugriff auf den Berichtsserver](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md).  
  
###  <a name="BKMK_ssis"></a>Von Integration Services verwendete Ports  
 In der folgenden Tabelle werden die vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Dienst verwendeten Ports aufgeführt.  
  
|Funktion|Port|Kommentare|  
|-------------|----------|--------------|  
|
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Remoteprozeduraufrufe (MS RPC)<br /><br /> Wird von der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Laufzeit verwendet.|TCP-Port 135<br /><br /> Siehe [Spezielle Überlegungen zu Port 135](#BKMK_port_135)|Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst verwendet DCOM auf Port 135. Der Dienstkontroll-Manager verwendet Port 135, um Tasks wie z. B. das Starten und Beenden des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Diensts und das Übertragen von Kontrollanforderungen an den laufenden Dienst auszuführen. Die Portnummer kann nicht geändert werden.<br /><br /> Dieser Port muss nur dann geöffnet sein, wenn Sie eine Verbindung mit einer Remoteinstanz des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Diensts von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] oder einer benutzerdefinierten Anwendung aus herstellen.|  
  
 Eine Schritt-für-Schritt-Anleitung zum Konfigurieren der Windows-Firewall für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]finden Sie unter [Configure a Windows Firewall for Access to the SSIS Service](../../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)(Konfigurieren einer Windows-Firewall für den Zugriff auf den SSIS-Dienst).  
  
###  <a name="BKMK_additional_ports"></a>Zusätzliche Ports und Dienste  
 Die folgende Tabelle enthält Ports und Dienste, von denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abhängig sein kann.  
  
|Szenario|Port|Kommentare|  
|--------------|----------|--------------|  
|Windows-Verwaltungsinstrumentation<br /><br /> Weitere Informationen zu WMI finden Sie unter [WMI-Anbieter für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md).|WMI wird als Teil eines Hosts für gemeinsame Dienste ausgeführt, wobei Ports über DCOM zugewiesen werden. WMI verwendet möglicherweise den TCP-Port 135.<br /><br /> Siehe [Spezielle Überlegungen zu Port 135](#BKMK_port_135)|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager verwendet WMI zum Auflisten und Verwalten von Diensten. Es wird empfohlen, die vorkonfigurierte Regelgruppe **Windows-Verwaltungsinstrumentation (WMI)** zu verwenden. Weitere Informationen finden Sie im Abschnitt [Interaktion mit anderen Firewallregeln](#BKMK_other_rules) weiter unten.|  
|
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC)|TCP-Port 135<br /><br /> Siehe [Spezielle Überlegungen zu Port 135](#BKMK_port_135)|Wenn Ihre Anwendung verteilte Transaktionen verwendet, müssen Sie die Firewall möglicherweise so konfigurieren, dass MS DTC-Datenverkehr ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) zwischen separaten MS DTC-Instanzen sowie zwischen MS DTC und Ressourcen-Managern wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übermittelt werden kann. Es wird empfohlen, die vorkonfigurierte Regelgruppe **Distributed Transaction Coordinator** zu verwenden.<br /><br /> Bei Konfiguration eines einzelnen freigegebenen MS-DTCs für den gesamten Cluster in einer separaten Gruppe sollten Sie sqlservr.exe der Firewall als Ausnahme hinzufügen.|  
|Die Schaltfläche zum Durchsuchen in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] verwendet UDP, um eine Verbindung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browserdienst herzustellen. Weitere Informationen finden Sie unter [SQL Server-Browserdienst &#40;Datenbank-Engine und SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md).|UDP-Port 1434|UDP ist ein verbindungsloses Protokoll.<br /><br /> Die Firewall verfügt über eine Einstellung mit dem Namen [UnicastResponsesToMulticastBroadcastDisabled Property of the INetFwProfile Interface](https://go.microsoft.com/fwlink/?LinkId=118371) , die das Verhalten der Firewall in Hinblick auf Unicast-Antworten auf eine Broadcast- (oder Multicast-) UDP-Anforderung steuert.  Es sind zwei Verhaltensweisen möglich:<br /><br /> Wenn die Einstellung TRUE ist, werden überhaupt keine Unicastantworten auf einen Broadcast zugelassen. Das Auflisten der Dienste schlägt fehl.<br /><br /> Wenn die Einstellung FALSE (Standard) ist, werden Unicastantworten 3 Sekunden lang zugelassen. Die Zeitdauer ist nicht konfigurierbar. In einem überlasteten Netzwerk oder einem Netzwerk mit häufiger Latenz oder bei stark ausgelasteten Servern wird bei den Versuchen, Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufzulisten, möglicherweise eine Teilliste zurückgegeben, die die Benutzer irreführen kann.|  
|IPsec-Datenverkehr|UDP-Port 500 und UDP-Port 4500|Wenn die Domänenrichtlinie eine Netzwerkkommunikation über IPSec erfordert, müssen Sie auch den UDP-Port 4500 und den UDP-Port 500 der Ausnahmeliste hinzufügen. IPsec ist eine Option, die den **Assistenten für neue eingehende Regel** im Windows-Firewall-Snap-In verwendet. Weitere Informationen finden Sie unter [Verwenden des Snap-Ins „Windows-Firewall mit erweiterter Sicherheit“](#BKMK_WF_msc) weiter unten in diesem Thema.|  
|Verwenden der Windows-Authentifizierung mit vertrauenswürdigen Domänen|Firewalls müssen konfiguriert werden, um Authentifizierungsanforderungen zuzulassen.|Weitere Informationen finden Sie unter [Konfigurieren einer Firewall für Domänen und Vertrauensstellungen](https://support.microsoft.com/kb/179442/).|  
|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Windows-Clusterunterstützung|Die Clusterunterstützung erfordert zusätzliche Ports, die keine direkte Beziehung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aufweisen.|Weitere Informationen finden Sie unter [Enable a network for cluster use](https://go.microsoft.com/fwlink/?LinkId=118372).|  
|In der HTTP-Server-API (HTTP.SYS) reservierte URL-Namespaces|Wahrscheinlich TCP-Port 80, kann jedoch für andere Ports konfiguriert werden. Allgemeine Informationen finden Sie unter [Konfigurieren von HTTP und HTTPS](https://go.microsoft.com/fwlink/?LinkId=118373).|Spezifische Informationen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Reservieren eines HTTP.SYS-Endpunkts mittels „HttpCfg.exe“ finden Sie unter [Informationen zu URL-Reservierungen und -Registrierungen &#40;SSRS-Konfigurations-Manager&#41;](../../reporting-services/install-windows/about-url-reservations-and-registration-ssrs-configuration-manager.md).|  
  
##  <a name="BKMK_port_135"></a>Besondere Überlegungen zu Port 135  
 Wenn Sie RPC mit TCP/IP oder mit UDP/IP als Transportprotokoll verwenden, werden eingehende Ports den Systemdiensten häufig dynamisch nach Bedarf zugewiesen; hierbei werden TCP/IP- und UDP/IP-Ports verwendet, die größer als Port 1024 sind. Diese werden informell häufig als „zufällige RPC-Ports“ bezeichnet. In solchen Fällen sind die RPC-Clients auf die Information der RPC-Endpunktzuordnung angewiesen, welche dynamischen Ports dem Server zugeordnet wurden. Für einige RPC-basierte Dienste können Sie einen bestimmten Port konfigurieren, statt RPC einen Port dynamisch zuweisen zu lassen. Außerdem können Sie den Bereich der Ports, die von RPC dynamisch zugewiesen werden, unabhängig vom Dienst verkleinern. Da Port 135 für zahlreiche Dienste verwendet wird, wird dieser häufig von böswilligen Benutzern angegriffen. Wenn Sie Port 135 öffnen, erwägen Sie, den Gültigkeitsbereich der Firewallregel einzuschränken.  
  
 Weitere Informationen zu Port 135 finden Sie in den folgenden Ressourcen:  
  
-   [Dienst Übersicht und Netzwerk Port Anforderungen für das Windows Server-System](https://support.microsoft.com/kb/832017)  
  
-   [Beheben von Fehlern bei der RPC-Endpunkt Zuordnung mithilfe der Windows Server 2003-Support Tools von der Produkt-CD](https://support.microsoft.com/kb/839880)  
  
-   [Remote Prozedur Aufruf (RPC)](https://go.microsoft.com/fwlink/?LinkId=118375)  
  
-   [Konfigurieren der dynamischen RPC-Port Zuweisung zum Arbeiten mit Firewalls](https://support.microsoft.com/kb/154596/)  
  
##  <a name="BKMK_other_rules"></a>Interaktion mit anderen Firewallregeln  
 Die Windows-Firewall verwendet Regeln und Regelgruppen, um ihre Konfiguration festzulegen. Jede Regel oder Regelgruppe ist normalerweise mit einem bestimmten Programm oder Dienst verknüpft, und dieses Programm oder dieser Dienst kann diese Regel ohne Ihr Wissen ändern oder löschen. Beispielsweise sind die Regelgruppen **WWW-Dienste (HTTP)** und **Sichere WWW-Dienste (HTTPS)** mit IIS verknüpft. Die Aktivierung dieser Regeln öffnet die Ports 80 und 443, und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen, die auf den Ports 80 und 443 beruhen, werden ausgeführt, wenn diese Regeln aktiviert sind. Administratoren, die IIS konfigurieren, können diese Regeln jedoch ändern oder deaktivieren. Deshalb sollten Sie, wenn Sie Port 80 oder Port 443 für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden, Ihre eigene Regel oder Regelgruppe erstellen, die Ihre gewünschte Portkonfiguration unabhängig von den anderen IIS-Regeln beibehält.  
  
 Das MMC-Snap-In „Windows-Firewall mit erweiterter Sicherheit“ erlaubt jeden Datenverkehr, der mit einer entsprechenden Zulassungsregel übereinstimmt. Wenn also zwei Regeln vorhanden sind, die beide für Port 80 gelten (mit unterschiedlichen Parametern), wird derjenige Datenverkehr zugelassen, der mit einer der beiden Regeln übereinstimmt. Wenn eine Regel den Datenverkehr über Port 80 von einem lokalen Subnetz und eine Regel den Datenverkehr von einer beliebigen Adresse erlaubt, wird letztendlich der gesamte Datenverkehr über Port 80 unabhängig von der Quelle zugelassen. Um den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]effektiv zu verwalten, sollten Administratoren alle auf dem Server aktivierten Firewallregeln in regelmäßigen Abständen überprüfen.  
  
##  <a name="BKMK_profiles"></a>Übersicht über Firewallprofile  
 Firewallprofile werden unter [Erste Schritte mit der Windows-Firewall mit erweiterter Sicherheit](https://go.microsoft.com/fwlink/?LinkId=116080) im Abschnitt **NLA-Hostfirewall (Network Location Awareness)** behandelt. Zusammenfassend gilt: Die Betriebssysteme identifizieren und "erinnern" alle Netzwerke, mit denen sie eine Verbindung herstellen, in Bezug auf die Konnektivität, Verbindungen und Kategorie.  
  
 In Windows-Firewall mit erweiterter Sicherheit gibt es drei Netzwerkstandorttypen:  
  
-   Domäne: Windows kann den Zugriff auf den Domänencontroller für die Domäne des Netzwerks, mit dem der Computer verbunden ist, authentifizieren.  
  
-   Öffentlich. Alle neu erkannten Netzwerke, außer Domänennetzwerke, werden zunächst als öffentlich kategorisiert. Netzwerke, die direkte Verbindungen zum Internet darstellen oder sich an öffentlichen Orten wie z. B. auf Flughäfen und in Cafés befinden, sollten auch öffentlich bleiben.  
  
-   Privat. Ein Netzwerk, das von einem Benutzer oder einer Anwendung als privat gekennzeichnet wird. Es sollten nur vertrauenswürdige Netzwerke als private Netzwerke gekennzeichnet werden. Benutzer können Heim- oder kleine Firmennetzwerke als privat kennzeichnen.  
  
 Der Administrator kann für jeden Netzwerkstandorttyp ein Profil erstellen. Dabei kann jedes Profil unterschiedliche Firewallrichtlinien enthalten. Es wird immer nur ein Profil angewendet. Die Profilreihenfolge wird wie folgt angewendet:  
  
1.  Wenn alle Schnittstellen gegenüber dem Domänencontroller für die Domäne, deren Mitglied der Computer ist, authentifiziert werden, wird das Domänenprofil angewendet.  
  
2.  Wenn alle Schnittstellen entweder gegenüber dem Domänencontroller authentifiziert oder mit Netzwerken, die als private Netzwerkstandorte klassifiziert sind, verbunden werden, wird das private Profil angewendet.  
  
3.  Andernfalls wird das öffentliche Profil angewendet.  
  
 Verwenden Sie das MMC-Snap-In „Windows-Firewall mit erweiterter Sicherheit“, um alle Firewallprofile anzuzeigen und zu konfigurieren. Mithilfe des Elements **Windows-Firewall** in der Systemsteuerung kann nur das aktuelle Profil konfiguriert werden.  
  
##  <a name="BKMK_additional_settings"></a>Zusätzliche Firewalleinstellungen mithilfe des Elements "Windows-Firewall" in der Systemsteuerung  
 Ausnahmen, die Sie der Firewall hinzufügen, können das Öffnen des Ports bei eingehenden Verbindungen von bestimmten Computern oder vom lokalen Subnetz einschränken. Diese Einschränkung des Bereichs der Portöffnung kann den Umfang, in dem Ihr Computer böswilligen Benutzern ausgesetzt ist, verringern und wird daher empfohlen.  
  
> [!NOTE]  
>  Mithilfe des Elements **Windows-Firewall** in der Systemsteuerung wird nur das aktuelle Firewallprofil konfiguriert.  
  
#### <a name="to-change-the-scope-of-a-firewall-exception-using-the-windows-firewall-item-in-control-panel"></a>So ändern Sie den Bereich einer Firewallausnahme mithilfe des Elements „Windows-Firewall“ in der Systemsteuerung  
  
1.  Wählen Sie unter dem Element **Windows-Firewall** in der Systemsteuerung auf der Registerkarte **Ausnahmen** ein Programm oder einen Port aus, und klicken Sie dann auf **Eigenschaften** oder **Bearbeiten**.  
  
2.  Klicken Sie im Dialogfeld **Programm bearbeiten** oder **Port bearbeiten** auf **Bereich ändern**.  
  
3.  Wählen Sie eine der folgenden Optionen:  
  
    -   **Alle Computer (einschließlich der im Internet)**  
  
         Nicht empfohlen. Dies ermöglicht es jedem Computer, der mit Ihrem Computer Kontakt aufnehmen kann, eine Verbindung mit einem bestimmten Programm oder Port herzustellen. Diese Einstellung kann notwendig sein, um die Anzeige von Informationen für anonyme Benutzer im Internet zuzulassen, erhöht aber die Gefahr, die von böswilligen Benutzern ausgeht. Ihre Gefährdung kann sich noch weiter erhöhen, wenn Sie diese Einstellung aktivieren und außerdem NAT-Traversal (Network Address Translation) zulassen, wie z. B. die Option Randüberquerung zulassen.  
  
    -   **Nur mein Netzwerk (Subnetz)**  
  
         Diese Einstellung ist sicherer als **Alle Computer**. Nur Computer im lokalen Subnetz Ihres Netzwerks können eine Verbindung mit dem Programm oder Port herstellen.  
  
    -   **Benutzerdefinierte Liste:**  
  
     Nur Computer, die über die von Ihnen aufgeführten IP-Adressen verfügen, können eine Verbindung herstellen. Dies kann eine sicherere Einstellung als **Nur für eigenes Netzwerk (Subnetz)** sein; Clientcomputer, die DHCP verwenden, können jedoch gelegentlich ihre IP-Adresse ändern. Dann kann der beabsichtigte Computer keine Verbindung herstellen. Ein anderer Computer, den Sie nicht autorisieren wollten, könnte die aufgeführte IP-Adresse akzeptieren und dann in der Lage sein, eine Verbindung herzustellen. Die Option **Benutzerdefinierte Liste** eignet sich möglicherweise zum Auflisten anderer Server, die für eine feste IP-Adresse konfiguriert sind; es besteht jedoch die Möglichkeit, dass IP-Adressen von einem Eindringling gefälscht (gespooft) werden. Restriktive Firewallregeln sind nur so stark wie Ihre Netzwerkinfrastruktur.  
  
##  <a name="BKMK_WF_msc"></a>Verwenden des Snap-Ins "Windows-Firewall mit erweiterter Sicherheit"  
 Mithilfe des MMC-Snap-Ins „Windows-Firewall mit erweiterter Sicherheit“ können zusätzliche erweiterte Firewalleinstellungen konfiguriert werden. Das Snap-In enthält einen Regel-Assistenten und bietet Zusatzeinstellungen, die im Element **Windows-Firewall** in der Systemsteuerung nicht verfügbar sind. Dies umfasst die folgenden Einstellungen:  
  
-   Verschlüsselungseinstellungen  
  
-   Einschränkungen für Dienste  
  
-   Einschränken von Verbindungen für Computer nach Name  
  
-   Einschränken von Verbindungen für bestimmte Benutzer oder Profile  
  
-   Randüberquerung, die dem Datenverkehr die Umgehung von NAT-Routern (Network Address Translation) erlaubt  
  
-   Konfigurieren von ausgehenden Regeln  
  
-   Konfigurieren von Sicherheitsregeln  
  
-   Erfordern von IPsec für eingehende Verbindungen  
  
#### <a name="to-create-a-new-firewall-rule-using-the-new-rule-wizard"></a>So erstellen Sie eine neue Firewallregel mit dem Assistenten für neue Regeln  
  
1.  Klicken Sie im Startmenü auf **Ausführen**, geben Sie **WF.msc**ein, und klicken Sie anschließend auf **OK**.  
  
2.  Klicken Sie im linken Bereich von **Windows-Firewall mit erweiterter Sicherheit**mit der rechten Maustaste auf **Eingehende Regeln**, und klicken Sie dann auf **Neue Regel**.  
  
3.  Schließen Sie den **Assistenten für neue eingehende Regel** mit den gewünschten Einstellungen ab.  
  
##  <a name="BKMK_troubleshooting"></a>Problembehandlung für Firewall  
 Die folgenden Tools und Techniken können bei der Behandlung von Problemen mit der Firewall nützlich sein:  
  
-   Der effektive Portstatus ist die Gesamtheit aller Regeln, die den Port betreffen. Beim Versuch, den Zugriff über einen Port zu blockieren, kann es hilfreich sein, alle Regeln, die die Portnummer nennen, zu überprüfen. Verwenden Sie hierzu das MMC-Snap-In „Windows-Firewall mit erweiterter Sicherheit“, und sortieren Sie die ein- und ausgehenden Regeln nach Portnummer.  
  
-   Überprüfen Sie die Ports, die auf dem Computer aktiv sind, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Dazu muss überprüft werden, welche TCP/IP-Ports überwacht werden und welchen Status diese Ports besitzen.  
  
     Um zu überprüfen, welche Ports überwacht werden, verwenden Sie das Befehlszeilen-Hilfsprogramm **netstat** . Zusätzlich zur Anzeige der aktiven TCP-Verbindungen werden mit dem **netstat**-Hilfsprogramm auch eine Reihe von IP-Statistiken und -Informationen angezeigt.  
  
    #### <a name="to-list-which-tcpip-ports-are-listening"></a>So führen Sie auf, auf welchen TCP/IP-Ports die Überwachung erfolgt  
  
    1.  Öffnen Sie das Eingabeaufforderungsfenster.  
  
    2.  Geben Sie an der Eingabeaufforderung Folgendes ein: `netstat -n -a`.  
  
         Mit dem **-n**-Schalter wird **netstat** angewiesen, die Adressen und Portnummern der aktiven TCP-Verbindungen numerisch anzuzeigen. Mit dem **-a**-Schalter wird **netstat** angewiesen, die vom Computer überwachten TCP- und UDP-Ports anzuzeigen.  
  
-   Mit dem **PortQry**-Hilfsprogramm kann der Status der TCP/IP-Ports als überwacht, nicht überwacht oder gefiltert gemeldet werden. (Der gefilterte Status bedeutet, dass der Port überwacht oder nicht überwacht wird. Dieser Status gibt an, dass das Hilfsprogramm keine Antwort vom Port empfangen hat.) Das Hilfsprogramm **PortQry** steht im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=17148)zum Herunterladen zur Verfügung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dienst Übersicht und Netzwerk Port Anforderungen für das Windows Server-System](https://support.microsoft.com/kb/832017)  
