---
title: Installieren von Data Quality Services
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 486e4216-a946-4c6e-828c-61bc905f7ec1
author: swinarko
ms.author: sawinark
ms.openlocfilehash: b7a9d9ce36a3419883adae9050ffabd0d1f9b012
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75252187"
---
# <a name="install-data-quality-services"></a>Installieren von Data Quality Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssDQSnoversionLong](../../includes/ssdqsnoversionlong-md.md)](DQS) enthält die folgenden zwei Komponenten: **[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]** und **[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]**.  
  
|DQS-Komponente|BESCHREIBUNG|  
|-------------------|-----------------|  
|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]|
  [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] wird auf der [!INCLUDE[ssNoversion](../../includes/ssNoVersion-md.md)]-Datenbank-Engine installiert und enthält drei Datenbanken: DQS_MAIN, DQS_PROJECTS und DQS_STAGING_DATA. DQS_MAIN enthält DQS-gespeicherte Prozeduren, die DQS-Engine und veröffentlichte Knowledge Bases. DQS_PROJECTS enthält die Datenqualitätsprojektinformationen. DQS_STAGING_DATA ist der Stagingbereich, in den Sie die Quelldaten zum Ausführen von DQS-Vorgängen kopieren können, um die verarbeiteten Daten anschließend zu exportieren.|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|
  [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] ist eine eigenständige Anwendung, die eine Verbindung mit [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]ermöglicht und eine hochgradig intuitive grafische Benutzeroberfläche bereitstellt, um Data Quality- und andere Verwaltungsaufgaben für DQS auszuführen.|  
  
> [!IMPORTANT]  
>  Neben den beiden oben erwähnten DQS-Komponenten haben Sie folgende Möglichkeiten:  
>   
>  Verwenden Sie die DQS-Bereinigungstransformation in Integration Services, die die Datenbereinigung innerhalb des Integration Services-Verpackungsprozesses ausführt und automatisch mit Integration Services installiert wird. Informationen zum Installieren von Integration Services finden Sie unter [Installieren von Integration Services](../../integration-services/install-windows/install-integration-services.md).  
>   
>  Aktivieren Sie die DQS-Integration in Master Data Services, um die DQS-Abgleichfunktionalität im Master Data Services-Add-In für Excel zu verwenden. Weitere Informationen finden Sie unter [Aktivieren der Data Quality Services-Integration in Master Data Services](../../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 Die DQS-Installation besteht aus drei Teilen:  
  
-   [Aufgaben vor der Installation](#PreInstallationTasks): Überprüfen Sie die Systemanforderungen, bevor Sie DQS installieren.  
  
-   [Data Quality Services-Installations Tasks](#DQSInstallation): Installieren Sie DQS mithilfe SQL Server-Setup.  
  
-   [Aufgaben nach der Installation](#PostInstallationTasks): führen Sie diese Aufgaben nach der Fertigstellung mit dem SQL Server-Setup aus, um die Installation von DQS abzuschließen.  
  
> [!NOTE]  
>  Dieses Thema enthält keine Anweisungen zum Ausführen des Setups über die Befehlszeile. Informationen zu Befehlszeilenoptionen zum Installieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] und Client finden Sie unter [Funktionsparameter](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Feature) im Artikel [Installieren von SQL Server von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
##  <a name="PreInstallationTasks"></a>Aufgaben vor der Installation  
 Stellen Sie vor dem Installieren von DQS sicher, dass der Computer die Mindestsystemanforderungen erfüllt. Die folgende Tabelle enthält Informationen zu den Mindestsystemanforderungen für die DQS-Komponenten:  
  
|DQS-Komponente|Mindestsystemanforderungen|  
|-------------------|---------------------------------|  
|[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]|Arbeitsspeicher (RAM): Minimum: 2 GB/empfohlen: 4 GB oder mehr<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]Datenbank-Engine. Weitere Informationen finden Sie unter [Installieren der SQL Server-Datenbank-Engine](../../database-engine/install-windows/install-sql-server-database-engine.md).|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|.NET Framework 4.0 (wird mit dem [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] installiert, sofern nicht bereits installiert)<br /><br /> Internet Explorer 6.0 SP1 oder höher|  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] und [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] können auf demselben Computer oder auf verschiedenen Computern installiert werden. Beide Komponenten können unabhängig voneinander und in beliebiger Reihenfolge installiert werden. Damit der [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]verwendet werden kann, muss jedoch ein [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installiert sein, mit dem eine Verbindung hergestellt wird.  
>   
>  Sie können eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] -Version von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] unter Verwendung der aktuellen oder einer früheren Version von [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] und der DQS-Bereinigungstransformation herstellen. Informationen zum Aktualisieren der vorhandenen DQS-Version auf [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]finden Sie unter [Aktualisieren von Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md).  
>   
>  Obwohl Microsoft Excel keine erforderliche Komponente zum Installieren von Data Quality-Client ist, muss Microsoft Excel 2003 oder höher auf dem Data Quality-Clientcomputer installiert sein, damit verschiedene Vorgänge in der Clientanwendung wie das Importieren von Domänenwerten aus einer Excel-Datei oder das Zuordnen zu den Quelldaten in einer Excel-Datei für Wissensermittlungs-, Bereinigungs- oder Abgleichsaktivitäten durchgeführt werden können.  
  
 Detaillierte Informationen zu den Mindestsystemanforderungen für die Installation von [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
##  <a name="DQSInstallation"></a>Data Quality Services-Installations Tasks  
 Zum Installieren der DQS-Komponenten müssen Sie das [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] -Setup ausführen. Beim Ausführen des SQL Server-Setups müssen Sie mehrere Seiten des Installations-Assistenten durchgehen, um basierend auf Ihren Anforderungen die entsprechenden Optionen auszuwählen. In der folgenden Tabelle sind nur die Seiten des Installations-Assistenten mit den Optionen aufgeführt, die sich auf die Installation von DQS auswirken:  
  
|Seite|Action|  
|----------|------------|  
|Featureauswahl|Auswahl:<br /><br /> **Data Quality Services** unter **Datenbank-Engine Services** , um die [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]zu installieren. <br />Wenn Sie das Kontrollkästchen **Data Quality Services** aktivieren, kopiert SQL Server-Setup eine Installationsdatei, DQSInstaller.exe, im Verzeichnis der SQL Server-Instanz auf dem Computer. Sie müssen diese Datei nach dem Abschließen des SQL Server-Setups ausführen, um die Installation von ** abzuschließen[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]. Sie müssen außerdem einige zusätzliche Schritte zum Konfigurieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ausführen, bevor Sie ihn verwenden können. Weitere Informationen finden Sie unter [Installationsnachbereitung](#PostInstallationTasks).<br /><br /> **Data Quality-Client** zu installieren [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].<br /><br /> (Empfohlen) **Verwaltungstools > Vollständig** unter **Verwaltungstools > Einfach** zur Installation von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Ihnen steht eine grafische Benutzeroberfläche zur Verwaltung der SQL Server-Instanz zur Verfügung, und Sie werden bei der Ausführung weiterer Tasks während der Installationsnachbereitung unterstützt. Diese werden im folgenden Abschnitt erläutert.|  
|Konfiguration der Datenbank-Engine|Klicken Sie auf **Aktuellen Benutzer hinzufügen** , um der festen Serverrolle sysadmin das Windows-Benutzerkonto hinzuzufügen. Dies ist erforderlich, damit Sie später die Datei DQSInstaller.exe ausführen können, um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abzuschließen.|  
  
##  <a name="PostInstallationTasks"></a>Aufgaben nach der Installation  
 Nach dem Abschließen des SQL Server-Installations-Assistenten müssen Sie die in diesem Abschnitt erläuterten zusätzlichen Schritte ausführen, um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abzuschließen, ihn zu konfigurieren und in Betrieb zu nehmen.  
  
1.  Um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abzuschließen, führen Sie die Datei „DQSInstaller.exe“ aus. Beim Ausführen der Datei DQSInstaller.exe geschieht Folgendes:  
  
    -   Die Datenbanken DQS_MAIN, DQS_PROJECTS und DQS_STAGING_DATA werden erstellt.  
  
    -   Die Anmeldenamen ##MS_dqs_db_owner_login## und ##MS_dqs_service_login## werden erstellt.  
  
    -   Die Rollen dqs_administrator, dqs_kb_editor und dqs_kb_operator werden in der DQS_MAIN-Datenbank erstellt.  
  
    -   Die gespeicherte DQInitDQS_MAIN-Prozedur wird in der master-Datenbank erstellt.  
  
    -   Die Datei „DQS_install.log“ wird normalerweise im Ordner C:\Programme\Microsoft SQL Server\MSSQL13.*<Instanzname>* \MSSQL\Log erstellt. Die Datei enthält Informationen zu den Aktionen, die beim Ausführen der Datei DQSInstaller.exe ablaufen.  
  
    -   Wenn eine Master Data Services-Datenbank in der gleichen SQL Server-Instanz wie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]vorhanden ist, wird ein der Master Data Services-Anmeldung zugeordneter Benutzer erstellt und ihm die dqs_administrator-Rolle in der Datenbank DQS_MAIN erteilt.  
  
     Damit ist die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abgeschlossen.  
  
     Weitere Informationen finden [Sie unter Ausführen von dqsinstaller. exe, um die Installation von Data Quality Server abzuschließen](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
2.  Zuweisen von DQS-Rollen an Benutzer:  
  
     Um sich mithilfe des [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] bei [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]anzumelden, muss der Benutzer einer der folgenden drei Rollen auf der DQS_MAIN-Datenbank angehören:  
  
    -   **dqs_administrator**  
  
    -   **dqs_kb_editor**  
  
    -   **dqs_kb_operator**  
  
     Wenn das Benutzerkonto ein Element der festen Serverrolle sysadmin ist, können Sie sich standardmäßig am [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] anmelden, der den [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)] verwendet, auch wenn dem Benutzerkonto keine der DQS-Rollen gewährt wird. Weitere Informationen zu den drei DQS-Rollen finden Sie unter [DQS-Sicherheit](../../data-quality-services/dqs-security.md).  
  
     Weitere Informationen finden Sie unter [Zuweisen von DQS-Rollen an Benutzer](../../data-quality-services/install-windows/grant-dqs-roles-to-users.md).  
  
    > [!NOTE]  
    >  Die drei DQS-Rollen sind für die Datenbanken DQS_PROJECTS und DQS_STAGING_DATA nicht verfügbar.  
  
3.  Bereitstellen von Daten für DQS-Vorgänge. Stellen Sie sicher, dass Sie auf die Quelldaten für die DQS-Vorgänge zugreifen können, und dass Sie die verarbeiteten Daten in eine Tabelle in einer Datenbank exportieren können.  
  
     Weitere Informationen finden Sie unter  
                    [Zugreifen auf Daten für DQS-Vorgänge](../../data-quality-services/install-windows/access-data-for-the-dqs-operations.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Video: Installieren und Konfigurieren von DQS](https://go.microsoft.com/fwlink/?LinkId=238241)   
 [Aktualisieren von SQLCLR-Assemblys nach .NET Framework Update](../../data-quality-services/install-windows/upgrade-sqlclr-assemblies-after-net-framework-update.md)   
 [Exportieren und Importieren von DQS-Wissensdatenbanken mit dqsinstaller. exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)   
 [Aktualisieren von Data Quality Services](../../database-engine/install-windows/upgrade-data-quality-services.md)   
 [Entfernen von Data Quality Server-Objekten](../../sql-server/install/remove-data-quality-server-objects.md)   
 [Installieren von SQL Server Business Intelligence-Funktionen](../../sql-server/install/install-sql-server-business-intelligence-features.md)   
 [Deinstallations SQL Server](../../sql-server/install/uninstall-sql-server.md)   
 [Data Quality Services](../../data-quality-services/data-quality-services.md)   
 [Behandeln von Installations-und Konfigurationsproblemen in DQS](https://social.technet.microsoft.com/wiki/contents/articles/3776.aspx)  
  
  
