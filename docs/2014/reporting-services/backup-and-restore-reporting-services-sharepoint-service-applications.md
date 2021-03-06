---
title: Sichern und Wiederherstellen Reporting Services SharePoint-Dienst Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dfb4ed77-90e5-4273-b690-89a945508ed2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e061ea2394c2fdad1e7d37f56016c73d7787eda0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109953"
---
# <a name="backup-and-restore-reporting-services-sharepoint-service-applications"></a>Sichern und Wiederherstellen von Reporting Services-SharePoint-Dienstanwendungen
  In diesem Thema wird das Sichern und Wiederherstellen einer [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung mit der SharePoint-Zentraladministration oder PowerShell beschrieben. Das Thema enthält:  
  
-   [Einschränkungen](#bkmk_Restrictions)  
  
-   [Sichern der Dienst Anwendung](#bkmk_backup)  
  
-   [Wiederherstellen der Dienst Anwendung](#bkmk_restore)  
  
##  <a name="bkmk_BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="bkmk_Restrictions"></a> Einschränkungen  
  
> [!NOTE]  
>  
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Dienstanwendungen können teilweise mithilfe der SharePoint-Funktionen zum Sichern und Wiederherstellen gesichert und wiederhergestellt werden. **Weitere Schritte sind erforderlich** , und die Schritte werden in diesem Thema dokumentiert. Derzeit lassen sich auf Basis des Sicherungsprozesses **keine** Verschlüsselungsschlüssel und Anmeldeinformationen für Konten mit unbeaufsichtigter Ausführung oder Windows-Authentifizierung für die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Datenbank sichern.  
  
###  <a name="bkmk_recommendations"></a> Empfehlungen  
  
-   Sichern Sie die Verschlüsselungsschlüssel vor dem Starten der SharePoint-Sicherung. Wenn Sie die Verschlüsselungsschlüssel nicht sichern, ist der Zugriff auf die verschlüsselten Daten nach der Wiederherstellung der Dienstanwendung nicht möglich. Sie müssen die verschlüsselten Daten löschen.  
  
-   Überprüfen Sie, ob die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung Konten mit unbeaufsichtigter Ausführung oder Windows-Authentifizierung für den Datenbankzugriff verwendet. Bei Verwendung einer dieser Kontotypen sind die entsprechenden Anmeldeinformationen zu ermitteln, damit Sie die Dienstanwendung nach der Wiederherstellung richtig konfigurieren können.  
  
-   Stellen Sie sicher, dass das SharePoint-Sicherungsprotokoll im gleichen Ordner wie die Sicherungsdatei erstellt wird. Die Datei wird in der Regel **spbackup.log**genannt.  
  
##  <a name="bkmk_backup"></a>Sichern der Dienst Anwendung  
 Führen Sie die folgenden Schritte wie folgt aus:  
  
1.  Sichern der Verschlüsselungsschlüssel  
  
2.  Sichern der Dienstanwendung  
  
3.  Überprüfen Sie, ob die Dienstanwendung ein Konto mit unbeaufsichtigter Ausführung oder Windows-Authentifizierung für den Datenbankzugriff verwendet. Bei Verwendung einer dieser Kontotypen müssen Sie sich die Anmeldeinformationen notieren, damit Sie die Dienstanwendung nach der Wiederherstellung konfigurieren können.  
  
### <a name="backup-the-encryption-keys-using-central-administration"></a>Sichern der Verschlüsselungsschlüssel mit der Zentraladministration  
 Weitere Informationen zum Sichern der Verschlüsselungsschlüssel für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] finden Sie im Abschnitt „Verschlüsselungsschlüssel“ unter [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
###  <a name="bkmk_centraladmin"></a>Sichern der Dienst Anwendung mithilfe der SharePoint-zentral Administration  
 So sichern Sie die Dienstanwendung:  
  
1.  Klicken Sie in der Gruppe **Sichern und Wiederherstellen** der SharePoint-Zentraladministration auf **Sicherung durchführen** .  
  
2.  Erweitern Sie unter dem Knoten **Gemeinsame Dienste** die Option für **gemeinsame Dienstanwendungen** , und wählen Sie die Dienstanwendung aus. Sie weist einen Typ von **SQL Server Reporting Services-Dienstanwendung**auf.  
  
3.  Klicken Sie auf **Weiter**.  
  
4.  Geben Sie im Feld **Sicherungsspeicherort:** den Pfad für den Speicherort an, und klicken Sie auf **Sicherung starten**.  
  
5.  Wiederholen Sie den oben beschriebenen Prozess. Erweitern Sie jedoch anstelle der Auswahl der Dienstanwendung den Knoten **Proxys der gemeinsamen Dienste** , und wählen Sie den Dienstanwendungsproxy aus. Er weist einen Typ von **Proxy für die SQL Server Reporting Services-Dienstanwendung**auf.  
  
 Weitere Information finden Sie in den folgenden Themen in der SharePoint-Dokumentation:  
  
 [Sichern einer Dienst Anwendung (SharePoint Foundation 2010) in der SharePoint-Dokumentation](https://msdn.microsoft.com/library/ee748601.aspx).  
  
 [Sichern einer Dienst Anwendung (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a>Überprüfen der Kontoausführung und Datenbankauthentifizierung  
 **Ausführungs Konto:** So überprüfen Sie, ob die Dienst Anwendung ein Ausführungs Konto verwendet:  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten** .  
  
2.  Klicken Sie auf den Namen der Dienstanwendung und dann im SharePoint-Menüband auf **Verwalten** .  
  
3.  Klicken Sie auf **Ausführungskonto**.  
  
4.  Ist ein Ausführungskonto konfiguriert, müssen Ihnen die Anmeldeinformationen bekannt sein, um die Sicherung der Dienstanwendung wiederherstellen zu können. Fahren Sie erst mit der Sicherungs- und Wiederherstellungsprozedur fort, wenn Sie die richtigen Anmeldeinformationen kennen.  
  
 **Daten Bank Authentifizierung:** So überprüfen Sie, ob die Dienst Anwendung die Windows-Authentifizierung für die Daten Bank Authentifizierung verwendet:  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten** .  
  
2.  Klicken Sie auf den Namen der Dienstanwendung und dann im SharePoint-Menüband auf **Eigenschaften** .  
  
3.  Lesen Sie den Abschnitt **Reporting Services-Dienstdatenbank (SSRS)** .  
  
4.  Ist die Windows-Authentifizierung konfiguriert, müssen Ihnen die Anmeldeinformationen bekannt sein, um die Dienstanwendung nach der Wiederherstellung konfigurieren zu können. Fahren Sie erst mit der Sicherungs- und Wiederherstellungsprozedur fort, wenn Sie die richtigen Anmeldeinformationen kennen.  
  
##  <a name="bkmk_restore"></a>Wiederherstellen der Dienst Anwendung  
 Führen Sie die folgenden Schritte wie folgt aus:  
  
1.  Stellen Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dienstanwendung wieder her.  
  
2.  Wiederherstellen der Verschlüsselungsschlüssel  
  
3.  Wurde für die Dienstanwendung ein Ausführungskonto oder die Windows-Authentifizierung für den Datenbankzugriff verwendet, konfigurieren Sie die Anmeldeinformationen.  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a>Wiederherstellen der Dienstanwendung mit der SharePoint-Zentraladministration  
  
1.  Klicken Sie in der Gruppe **Sichern und Wiederherstellen** der SharePoint-Zentraladministration auf die Option zum Wiederherstellen aus einer Sicherung **** .  
  
2.  Geben Sie in das Feld für den Sicherungsverzeichnisspeicherort **** den Pfad für die Sicherungsdatei ein, und klicken Sie auf **Aktualisieren**.  
  
3.  Wählen Sie die Dienstanwendungssicherung aus der Liste **Komponente der höchsten Ebene** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Anwendung aus, und klicken Sie dann auf **Weiter**.  
  
5.  Geben Sie im Abschnitt **Anmeldenamen und Kennwörter** das Kennwort für den Anmeldenamen ein. Das Feld für den Anmeldenamen muss mit der Anmeldung ausgefüllt werden, die von der Dienstanwendung vor der Sicherung verwendet wurde.  
  
6.  Klicken Sie auf **Wiederherstellung starten**.  
  
7.  Wiederholen Sie den oben beschriebenen Prozess. Erweitern Sie jedoch anstelle der Wiederherstellung der Dienstanwendung den Knoten **Gemeinsame Dienste** , und erweitern Sie anschließend den Knoten für **gemeinsame Dienstanwendungen** .  
  
 Weitere Information finden Sie in den folgenden Themen in der SharePoint-Dokumentation:  
  
 [Wiederherstellen einer Dienst Anwendung (SharePoint Foundation 2010)](https://msdn.microsoft.com/library/ee748615.aspx).  
  
 Stellen Sie [eine-Dienst Anwendung (SharePoint Server 2010) wieder her](ttp://technet.microsoft.com/library/ee428305.aspx).  
  
### <a name="restore-the-encryption-keys-using-central-administration"></a>Wiederherstellen der Verschlüsselungsschlüssel mit der Zentraladministration  
 Weitere Informationen zum Wiederherstellen der Verschlüsselungsschlüssel für [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] finden Sie im Abschnitt „Verschlüsselungsschlüssel“ unter [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
### <a name="configure-the-execution-account-and-database-authentication"></a>Konfigurieren des Ausführungskontos und der Datenbankauthentifizierung  
 **Ausführungs Konto:** Wenn die Dienst Anwendung ein Ausführungs Konto verwendet hat, führen Sie die folgenden Schritte aus, um Sie zu konfigurieren:  
  
1.  Klicken Sie in der SharePoint-Zentraladministration in der Gruppe **Anwendungsverwaltung** auf **Dienstanwendungen verwalten** .  
  
2.  Klicken Sie auf den Namen der Dienstanwendung und dann im SharePoint-Menüband auf **Verwalten** .  
  
3.  Klicken Sie auf **Ausführungskonto**.  
  
4.  Geben Sie das Konto und Kennwort ein, und wählen Sie das Feld **Ausführungskonto angeben** aus.  
  
5.  Klicken Sie auf **OK**.  
  
 **Daten Bank Authentifizierung:** Wenn die Dienst Anwendung die Windows-Authentifizierung für die Daten Bank Authentifizierung verwendet hat, führen Sie die folgenden Schritte aus:  
  
1.  Klicken Sie in der SharePoint-zentral Administration in der Gruppe **Anwendungs Verwaltung** auf **Dienst Anwendungen verwalten** .  
  
2.  Klicken Sie auf den Namen der Dienstanwendung und dann im SharePoint-Menüband auf **Eigenschaften** .  
  
3.  Lesen Sie den Abschnitt **Reporting Services-Dienstdatenbank (SSRS)** .  
  
4.  Wählen Sie **Windows-Authentifizierung** aus.  
  
5.  Geben Sie das Konto und Kennwort ein. Wählen Sie ggf. die Option **Windows-Anmeldeinformationen verwenden** aus.  
  
6.  Klicken Sie auf **OK**  
  
  
