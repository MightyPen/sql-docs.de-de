---
title: Task „Statistiken aktualisieren“ (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.statistics.f1
helpviewer_keywords:
- Updates Statistics Task dialog box
ms.assetid: 22902fd0-eb39-4f18-af94-3fcb69d2a3a4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 51a3deffc9db182f7b3ad8f50d27c24e0f74dc6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62807115"
---
# <a name="update-statistics-task-maintenance-plan"></a>Task 'Statistiken aktualisieren' (Wartungsplan)
  Verwenden Sie das Dialogfeld **Task ' Statistiken aktualisieren** ', um Informationen zu den Daten in den Tabellen und Indizes zu aktualisieren [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dieser Task erstellt erneut die Verteilungsstatistik jedes für Benutzertabellen in der Datenbank erstellten Index mithilfe einer neuen Stichprobe. Die Verteilungsstatistiken werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, um die Navigation durch die Tabellen während der Verarbeitung von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen zu optimieren. Um die Verteilungsstatistiken automatisch zu erstellen, nimmt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für jeden Index in regelmäßigen Abständen Daten in der entsprechenden Tabelle als Stichprobe. Die Größe der Stichprobe basiert auf der Anzahl der Zeilen in der Tabelle und der Häufigkeit der an den Daten vorgenommenen Änderungen. Verwenden Sie diese Option, um mithilfe des angegebenen Prozentsatzes der Tabellendaten eine zusätzliche Stichprobe auszuführen. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt mithilfe dieser Informationen bessere Abfragepläne.  
  
 Dieser Task führt die UPDATE STATISTICS-Anweisung aus.  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Datenbanken**  
 Gibt die Datenbanken an, die von dieser Aufgabe betroffen sind.  
  
-   **Alle Datenbanken**  
  
     Generieren Sie einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken außer tempdb ausführt.  
  
-   **Alle System Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken außer tempdb ausführt. Für benutzerdefinierte Datenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Alle Benutzer Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle benutzerdefinierten Datenbanken ausführt. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Diese speziellen Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks nur für die ausgewählten Datenbanken ausführt. Wenn diese Option ausgewählt wird, muss mindestens eine Datenbank in der Liste ausgewählt werden.  
  
 **Hinweis** Wartungspläne werden nur für Datenbanken ausgeführt, die auf Kompatibilitäts Grad 80 oder höher eingestellt sind. Datenbanken mit Kompatibilitätsgrad 70 oder niedriger werden nicht angezeigt.  
  
 **Object**  
 Begrenzt das Raster **Auswahl** auf die Anzeige von Tabellen, Sichten oder beides.  
  
 **End**  
 Gibt die Tabellen oder Indizes an, auf die sich dieser Task auswirkt. Nicht verfügbar, wenn im Objektfeld der Eintrag **Tabellen und Sichten** ausgewählt ist.  
  
 **Alle vorhandenen Statistiken**  
 Aktualisiert alle Statistiken für Spalten und für Indizes.  
  
 **Nur Spalten Statistiken**  
 Aktualisiert nur Spaltenstatistiken.  
  
 **Nur Index Statistiken**  
 Aktualisiert nur Indexstatistiken.  
  
 **Überprüfungstyp**  
 Der Typ des Scanvorgangs, der zum Zusammenstellen von aktualisierten Statistiken verwendet wird.  
  
 **Vollständige Überprüfung**  
 Liest zum Zusammenstellen der Statistiken alle Zeilen in der Tabelle oder Sicht.  
  
 **Beispiel nach**  
 Gibt den prozentualen Anteil der Tabelle oder der indizierten Sicht an bzw. die Anzahl der Zeilen, für die die Stichprobe vorgenommen werden soll, wenn Statistiken für größere Tabellen oder Sichten gesammelt werden.  
  
 **T-SQL anzeigen**  
 Zeigt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen an, die für diesen Task auf dem Server auf Basis der ausgewählten Optionen ausgeführt werden.  
  
> [!NOTE]  
>  Wenn die Anzahl der betroffenen Objekte groß ist, kann die Anzeige erhebliche Zeit in Anspruch nehmen.  
  
## <a name="new-connection-dialog-box"></a>Neue Verbindung (Dialogfeld)  
 **Verbindungs Name**  
 Geben Sie einen Namen für die neue Verbindung ein.  
  
 **Servernamen auswählen oder eingeben**  
 Wählen Sie den Server aus, zu dem bei der Ausführung dieses Tasks eine Verbindung hergestellt werden soll.  
  
 **Aktualisieren**  
 Mithilfe dieser Option aktualisieren Sie die Liste der verfügbaren Server.  
  
 **Geben Sie Informationen ein, um sich beim Server anzumelden.**  
 Legt fest, wie die Authentifizierung gegenüber dem Server stattfindet.  
  
 **Integrierte Sicherheit von Windows verwenden**  
 Stellen Sie mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung eine Verbindung mit einer Instanz von her.  
  
 **Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
