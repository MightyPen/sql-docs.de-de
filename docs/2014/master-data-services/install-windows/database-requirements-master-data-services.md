---
title: Datenbankanforderungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 75bd453d4540a675809973f711bd778ab8639d10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479316"
---
# <a name="database-requirements-master-data-services"></a>Datenbankanforderungen (Master Data Services)
  Alle Masterdaten werden in einer [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank gespeichert. Auf dem Computer, auf dem diese Datenbank gehostet wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]muss eine Instanz von ausgeführt werden.  
  
 Verwenden Sie [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] , um die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank auf einem lokalen oder Remotecomputer zu erstellen und zu konfigurieren. Wenn Sie die Datenbank zwischen Umgebungen verschieben, können Sie die Informationen in einer neuen Umgebung beibehalten, indem Sie den [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Webdienst und [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] mit der Datenbank verbinden.  
  
> [!NOTE]  
>  Jeder Computer, auf dem Sie Komponenten von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installieren, muss lizenziert werden. Weitere Informationen finden Sie im Endbenutzerlizenzvertrag (End User License Agreement, EULA).  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Bevor Sie eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank erstellen, stellen Sie sicher, dass die folgenden Anforderungen erfüllt werden.  
  
### <a name="sql-server-edition"></a>SQL Server-Edition  
 Die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank kann auf den folgenden Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gehostet werden:  
  
-   
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence (64-Bit) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Enterprise (64-Bit) x64  
  
-   
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer (64-Bit) x64  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence (64-Bit) x64  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise (64-Bit) x64 – Nur Upgrade von [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer (64-Bit) x64  
  
-   Microsoft SQL Server 2008 R2 Enterprise (64-Bit) x64  
  
-   Microsoft SQL Server 2008 R2 Developer (64-Bit) x64  
  
 Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
### <a name="operating-system"></a>Betriebssystem  
 Informationen zu den unterstützten Windows-Betriebssystemen und anderen Anforderungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]für finden Sie unter [Hardware-und Software Anforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="accounts-and-permissions"></a>Konten und Berechtigungen  
  
|type|BESCHREIBUNG|  
|----------|-----------------|  
|Benutzerkonto|Sie können in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]ein Windows-Konto oder ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto verwenden, um eine Verbindung mit der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herzustellen, die die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank hosten soll. Das Benutzerkonto muss auf der Instanz von **** zur sysadmin[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Serverrolle gehören. Weitere Informationen zur Rolle **sysadmin** finden Sie unter [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]Administrator Konto|Wenn Sie eine [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Datenbank erstellen, müssen Sie ein Domänenbenutzerkonto als [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Systemadministrator angeben. Bei allen [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendungen, die dieser Datenbank zugeordnet sind, kann dieser Benutzer alle Modelle und alle Daten in sämtlichen Funktionsbereichen aktualisieren. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../administrators-master-data-services.md).|  
  
### <a name="database-backup"></a>Datenbanksicherung  
 Je nach den Umgebungsanforderungen empfiehlt es sich, zu Zeiten niedriger Auslastung täglich eine vollständige Datenbanksicherung auszuführen und die Transaktionsprotokolle häufiger zu sichern. Weitere Informationen zu Datenbanksicherungen finden Sie unter [Übersicht über Sicherungen &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von Master Data Services](install-master-data-services.md)   
 [Erstellen einer Master Data Services Datenbank](create-a-master-data-services-database.md)   
 [Master Data Services Datenbank](../master-data-services-database.md)   
 [Dialog Feld "Verbindung mit einer Master Data Services Datenbank herstellen"](../connect-to-a-master-data-services-database-dialog-box.md)   
 [Der Assistent zum Erstellen von Datenbanken &#40;Konfigurations-Manager für Master Data Services&#41;](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  
