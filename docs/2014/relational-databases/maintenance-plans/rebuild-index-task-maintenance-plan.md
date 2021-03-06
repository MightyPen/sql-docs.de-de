---
title: Task 'Index neu erstellen' (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reindex.f1
- reindex
helpviewer_keywords:
- Rebuild Index Task dialog box
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34bd5a607998c6e37f688ccbadcd4d612d3daea7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62806995"
---
# <a name="rebuild-index-task-maintenance-plan"></a>Task 'Index neu erstellen' (Wartungsplan)
  Mithilfe des Dialogfelds **Task „Index neu erstellen“** können Sie Indizes für Tabellen in der Datenbank mit einem neuen Füllfaktor neu erstellen. Der Füllfaktor bestimmt die Menge an leeren Speicherplatz auf jeder Seite im Index, der Platz für zukünftige Erweiterungen bieten soll. Wenn der Tabelle Daten hinzugefügt werden, wird der freie Speicherplatz aufgefüllt, da der Wert für den Füllfaktor nicht beibehalten wird. Der freie Speicherplatz kann durch Neuorganisieren der Daten- und Indexseiten wiederhergestellt werden.  
  
 **Task „Index neu erstellen“** verwendet die ALTER INDEX-Anweisung.  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Datenbanken**  
 Gibt die Datenbanken an, die von dieser Aufgabe betroffen sind.  
  
-   **Alle Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken außer tempdb ausführt.  
  
-   **Alle System Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken außer tempdb ausführt. Für benutzerdefinierte Datenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Alle Benutzer Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle benutzerdefinierten Datenbanken ausführt. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Diese speziellen Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks nur für die ausgewählten Datenbanken ausführt. Wenn diese Option ausgewählt wird, muss mindestens eine Datenbank in der Liste ausgewählt werden.  
  
    > [!NOTE]  
    >  Wartungspläne werden nur für Datenbanken mit Kompatibilitätsgrad 80 oder höher ausgeführt. Datenbanken mit Kompatibilitätsgrad 70 oder niedriger werden nicht angezeigt.  
  
 **Object**  
 Begrenzt das Raster **Auswahl** auf die Anzeige von Tabellen, Sichten oder beides.  
  
 **End**  
 Gibt die Tabellen oder Indizes an, auf die sich dieser Task auswirkt. Nicht verfügbar, wenn im Objektfeld der Eintrag **Tabellen und Sichten** ausgewählt ist.  
  
 **Seiten mit der standardmäßigen freien Speicherplatzmenge neu organisieren**  
 Löscht die Indizes für die Tabellen in der Datenbank und erstellt sie mit dem Füllfaktor, der beim Erstellen der Indizes angegeben wurde, neu.  
  
 **Ändern des freien Speicherplatzes pro Seiten Prozentsatz in**  
 Löscht die Indizes für die Tabellen in der Datenbank und erstellt sie mit einem neuen, automatisch berechneten Füllfaktor neu. Auf diese Weise wird der angegebene freie Speicherplatz auf den Indexseiten reserviert. Ein höherer Prozentsatz bedeutet, dass mehr freier Speicherplatz auf den Indexseiten reserviert wird und der Index entsprechend wachsen kann. Die gültigen Werte sind 0 bis 100.  
  
 **Ergebnisse in "tempdb" Sortieren**  
 Verwenden Sie `SORT_IN_TEMPDB`die-Option, die bestimmt, wo die während der Indexerstellung generierten Zwischenergebnisse der Sortierung temporär gespeichert werden. Wenn ein Sortiervorgang nicht erforderlich ist oder im Arbeitsspeicher ausgeführt werden kann, wird die Option `SORT_IN_TEMPDB`ignoriert.  
  
 **Index online während Neuindizierung**  
 Die Option `ONLINE` ermöglicht es Benutzern, während Indexvorgängen auf die zugrunde liegenden Tabellen- bzw. gruppierten Indexdaten und alle zugehörigen nicht gruppierten Indizes zuzugreifen.  
  
> [!NOTE]  
>  Onlineindexvorgänge sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
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
 Stellt mithilfe der Windows-Authentifizierung eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her.  
  
 **Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [DBCC DBREINDEX &#40;Transact-SQL-&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [SORT_IN_TEMPDB Option für Indizes](../indexes/indexes.md)   
 [Richtlinien für Online Index Vorgänge](../indexes/guidelines-for-online-index-operations.md)   
 [Funktionsweise von Online Index Vorgängen](../indexes/how-online-index-operations-work.md)   
 [Ausführen von Onlineindexvorgängen](../indexes/perform-index-operations-online.md)  
  
  
