---
title: Konfigurieren von Serverstartoptionen (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 91a48d4acd771c19617bac26c1393f30334768e8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62810368"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>Konfigurieren von Serverstartoptionen (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie Startoptionen, die bei jedem Starten von [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet werden, mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Managers konfigurieren. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a>Einschränkungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager schreibt Startparameter in die Registrierung. Diese werden beim nächsten Start von [!INCLUDE[ssDE](../../includes/ssde-md.md)]wirksam.  
  
 Bei einem Cluster müssen Änderungen auf dem aktiven Server vorgenommen werden, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] online ist und werden beim nächsten Start von [!INCLUDE[ssDE](../../includes/ssde-md.md)] wirksam. Die Registrierungsaktualisierung der Startoptionen auf dem anderen Knoten findet beim nächsten Failover statt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Konfiguration von Serverstartoptionen ist auf Benutzer beschränkt, die die entsprechenden Einträge in der Registrierung ändern können. Dazu gehören folgende Benutzer.  
  
-   Mitglieder der lokalen Administratorgruppe.  
  
-   Das Domänenkonto, das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird, wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] für die Ausführung unter einem Domänenkonto konfiguriert ist.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-configure-startup-options"></a>So konfigurieren Sie Startoptionen  
  
1.  Klicken Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf **SQL Server-Dienste**.  
  
    > [!NOTE]  
    >  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Verwaltungskonsolenprogramm und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
    >   
    >  -   **Windows 10**:  
    >          Um Configuration Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu öffnen, geben Sie auf der **Start Seite**SQLServerManager12. msc ( [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]für) ein. Ersetzen Sie für frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 12 durch eine kleinere Zahl. Durch Klicken auf SQLServerManager12.msc wird der Konfigurations-Manager geöffnet. Um die Configuration Manager an die Start Seite oder Task Leiste anzuheften, klicken Sie mit der rechten Maustaste auf SQLServerManager12. msc, und klicken Sie dann auf **Datei Speicherort öffnen**. Klicken Sie im Windows-Datei-Explorer mit der rechten Maustaste auf SQLServerManager12. msc, und klicken Sie dann auf am **Anfang anheften** oder **an Taskleiste**anheften  
    > -   **Windows 8**:  
    >          Um Configuration Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Charm **Suchen** unter **apps**zu öffnen, geben Sie **\<SQLServerManager Version>. msc** ein, z `SQLServerManager12.msc`. b., und drücken Sie dann die **Eingabe**Taste.  
  
2.  Klicken Sie im rechten Bereich mit der rechten Maustaste auf **SQL Server (***<instance_name>***)**, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Geben Sie auf der Registerkarte **Startparameter** im Feld **Startparameter angeben** den Parameter ein, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Wenn Sie z. b. im Einzelbenutzermodus starten möchten `-m` , geben Sie im Feld **Startparameter angeben ein** , und klicken Sie dann auf **Hinzufügen**. (Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus erneut starten, müssen Sie zunächst den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beenden. Andernfalls stellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent möglicherweise zuerst eine Verbindung her und verhindert, dass Sie als zweiter Benutzer eine Verbindung herstellen können.)  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Starten Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)]neu.  
  
    > [!WARNING]  
    >  Nachdem Sie die Verwendung des Einzelbenutzermodus abgeschlossen haben, wählen Sie im Feld Startparameter im `-m` Feld **vorhandene Parameter** den Parameter aus, und klicken Sie dann auf **Entfernen**. Starten Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] erneut, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im typischen Multibenutzermodus wiederherzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten von SQL Server im Einzelbenutzermodus](start-sql-server-in-single-user-mode.md)   
 [Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Diensts](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
