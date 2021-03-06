---
title: Überprüfen der Wiedergabe Ergebnisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: da999781-f0ff-47eb-ba7a-09c0ed8f61ad
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b81d4e1aeb2192e6a32a34bed74b9cd55a1cb9a9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63149708"
---
# <a name="review-the-replay-results"></a>Überprüfen der Wiedergabeergebnisse
  Nachdem die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay Funktion eine verteilte Wiedergabe abgeschlossen hat, kann die Wiedergabe Aktivität für jeden Client aufgezeichnet und in Ergebnisdateien der Ablauf Verfolgung auf jedem Client gespeichert werden. Um diese Aktivität aufzuzeichnen, müssen Sie beim Ausführen des Verwaltungstools mit der **replay** -Option den **-o** -Parameter verwenden. Weitere Informationen zur Wiedergabeoption finden Sie unter [Wiedergabeoption &#40;Verwaltungstool „Distributed Replay“&#41;](replay-option-distributed-replay-administration-tool.md).  
  
 Der Speicherort für die Ergebnisdateien der Ablaufverfolgung wird vom `<ResultDirectory>` -XML-Element in der Clientkonfigurationsdatei `DReplayClient.xml`, die sich auf jedem Client befindet, angegeben. Die Ablaufverfolgungsdateien im Clientergebnisverzeichnis werden bei jeder Wiedergabe überschrieben.  
  
 Um anzugeben, welche Art von Ausgabe in den Ergebnisdateien der Ablaufverfolgung aufgezeichnet werden soll, ändern Sie die Wiedergabekonfigurationsdatei `DReplay.exe.replay.config`. Sie können mit dem `<OutputOptions>` -XML-Element angeben, ob die Zeilenanzahl oder der Resultsetinhalt aufgezeichnet werden soll.  
  
 Weitere Informationen zu diesen Konfigurationseinstellungen finden Sie unter [Konfigurieren von Distributed Replay](configure-distributed-replay.md).  
  
## <a name="event-classes-captured-in-result-trace-files"></a>In Ergebnisdateien der Ablaufverfolgung aufgezeichnete Ereignisklassen  
 In der folgenden Tabelle sind alle Ereignisklassen aufgeführt, die in den Ergebnisdaten der Ablaufverfolgung aufgezeichnet werden.  
  
|Category|EventClass-Name|Aufzeichnungshäufigkeit|Zeitpunkt der Aufzeichnung|  
|--------------|---------------------|-----------------------|----------------------|  
|Wiedergebbare Ereignisse|Audit Login|Einmal pro Audit Login-Ereignis in den ursprünglichen Ablaufverfolgungsdaten|Bei Fehlschlagen oder erfolgreichem Abschluss des Ereignisses|  
||Audit Logout|Einmal pro Audit Logout-Ereignis in den ursprünglichen Ablaufverfolgungsdaten|Bei Fehlschlagen oder erfolgreichem Abschluss des Ereignisses|  
||SQL:BatchCompleted|Einmal pro SQL:BatchStarting-Ereignis in den ursprünglichen Ablaufverfolgungsdaten|Bei Fehlschlagen oder erfolgreichem Abschluss des Ereignisses|  
||RPC:Completed|Einmal pro RPC:Starting-Ereignis in den ursprünglichen Ablaufverfolgungsdaten|Bei Fehlschlagen oder erfolgreichem Abschluss des Ereignisses|  
|Statistik und Ergebnisse|Replay Settings-Ereignis|Einmalig|Erstes Ereignis im Ergebnis der Ablaufverfolgung|  
||Replay Statistics-Ereignis|Einmalig|Letztes Ereignis im Ergebnis der Ablaufverfolgung|  
||Replay Result Set-Ereignis|Einmal pro SQL:BatchStarting-Ereignis und RPC:Starting-Ereignis<br /><br /> Nur aufgezeichnet, wenn der Wert der `<RecordResultSet>` -Option in der Wiedergabekonfigurationsdatei auf `Yes`festgelegt wurde.||  
||Replay Result Row-Ereignis|Einmal pro Zeile im Resultset für das SQL:BatchStarting-Ereignis und das RPC:Starting-Ereignis<br /><br /> Nur aufgezeichnet, wenn der Wert der `<RecordResultSet>` -Option in der Wiedergabekonfigurationsdatei auf `Yes`festgelegt wurde.||  
|Fehler und Warnungen|Replay Internal Error|Einmal für jeden internen Fehler|Bei interner Fehlerbedingung|  
||Replay Provider Error|Einmal pro Anbieterfehler|Bei Anbieterfehlerbedingung|  
  
 Beachten Sie Folgendes:  
  
-   Für jedes Ereignis, das erfolgreich auf dem Zielserver wiedergegeben wird, gibt es eine entsprechende Ausgabeereignisklasse.  
  
-   Für jeden Ereignisfehler oder -abbruch werden möglicherweise mehrere Fehler generiert.  
  
## <a name="event-class-column-mapping"></a>Zuordnung von Spalten zu Ereignisklassen  
 In der folgenden Abbildung wird gezeigt, welche Spalten im Ergebnis der Ablaufverfolgung für die einzelnen Typen von Ereignisklassen, die während der Wiedergabe aufgezeichnet werden, verfügbar sind.  
  
 ![Zuordnung von Ereignis Klassen Spalten](../../database-engine/media/eventclassmappings.gif "Zuordnung von Spalten zu Ereignisklassen")  
  
## <a name="column-descriptions-for-result-trace"></a>Beschreibungen der Spalten für das Ergebnis der Ablaufverfolgung  
 In der folgenden Tabelle werden die Spalten der Ergebnisdaten der Ablaufverfolgung beschrieben.  
  
|Name der Datenspalte|Datentyp|BESCHREIBUNG|Column ID|  
|----------------------|---------------|-----------------|---------------|  
|EventClass|`nvarchar`|Der Name der Ereignisklasse.|1|  
|EventSequence|`bigint`|Für Anbieterfehler sowie interne Fehler und Warnungen ist dies die Sequenz der Ereignisaufzeichnung, die dem Fehler bzw. der Warnung entspricht.<br /><br /> Für alle anderen Ereignisklassen ist dies die Sequenz des Ereignisses in den ursprünglichen Ablaufverfolgungsdaten.|2|  
|ReplaySequence|`bigint`|Für Anbieterfehler sowie interne Fehler und Warnungen ist dies die Sequenz der Ereigniswiedergabe, die dem Fehler bzw. der Warnung entspricht.<br /><br /> Für alle anderen Ereignisklassen ist dies die Sequenz des Ereignisses, die während der Wiedergabe zugewiesen wird.|3|  
|TextData|`ntext`|Der Inhalt von TextData hängt von der EventClass ab.<br /><br /> Für Audit Login und ExistingConnection sind dies die festgelegten Optionen für die Verbindung.<br /><br /> Für SQL:BatchStarting ist dies der Text der Batchanforderung.<br /><br /> Für RPC:Starting ist dies die gespeicherte Prozedur, die aufgerufen wurde.<br /><br /> Für das Replay Settings-Ereignis enthält diese Spalte die in der Wiedergabekonfigurationsdatei definierten Einstellungen.<br /><br /> Für das Replay Statistics-Ereignis enthält diese Spalte die folgenden Informationen:<br />Die Zielinstanz von SQL Server für die Wiedergabe<br />Die Gesamtanzahl der wiedergebbaren Ereignisse<br />Die Anzahl der Anbieterfehler<br />Die Anzahl der internen Fehler<br />Interne Warnungen<br />Gesamtzahl der Fehler<br />Gesamterfolgsquote<br />Die Wiedergabezeit (HH:MM:SS:MMM)<br /><br /> Für das Replay Result Set-Ereignis wird die Liste der Spaltenheader für die Rückgabeergebnisse angezeigt.<br /><br /> Für das Replay Result Row-Ereignis wird der Rückgabewert aller Spalten für diese Zeile angezeigt.<br /><br /> Für Replay Internal Warning und Replay Provider Error enthält diese Spalte die Anbieterwarnungen bzw. -fehler.|4|  
|Attention|`bigint`|Die Beachtungsdauer (in Millisekunden) für das Ereignis. Dies wird anhand des Attention-Ereignisses der Aufzeichnungsablaufverfolgung berechnet. Wenn kein Abfragetimeout für das Ereignis angegeben wurde, wird diese Spalte nicht aufgefüllt (NULL).|5|  
|SubmitTime|`datetime`|Der Zeitpunkt, zu dem das Ereignis an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gesendet wurde.|6|  
|IsSuccessful|`int`|Ein boolesches Flag, das angibt, ob ein bestimmtes Ereignis erfolgreich ausgeführt wurde und Resultsets an den Client zurückgegeben wurden.<br /><br /> Ein Ereignis, das eine Warnung generiert (wenn z. B. ein Ereignis aufgrund von Attention oder eines vom Benutzer angegebenen Timeouts abgebrochen wird), gilt als erfolgreich.<br /><br /> IsSuccessful kann die folgenden Werte aufweisen:<br /><br /> 1 = erfolgreich<br /><br /> 0 = Fehler|7|  
|Duration [microsec]|`bigint`|Die Antwortzeitdauer (in Mikrosekunden) für das Ereignis. Die Messung beginnt, wenn das Anmelde-/Abmelde-/RPC-/Sprachereignis an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gesendet wurde.<br /><br /> Bei erfolgreichem Ereignis wird die Messung beendet, wenn das vollständige Resultset verarbeitet wurde.<br /><br /> Wenn das Ereignis nicht erfolgreich ist, endet die Messung zum Zeitpunkt des Fehlschlags oder Abbruchs des Ereignisses.|8|  
|RowCount|`bigint`|Wird abhängig vom Wert von `<RecordRowCount>` in der Wiedergabekonfigurationsdatei aufgefüllt:<br /><br /> Wenn `<RecordRowCount>` gleich Yes ist, enthält diese Zelle die Anzahl der Zeilen im Resultset, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zurückgegeben werden.<br /><br /> Wenn `<RecordRowCount>` gleich No ist, wird diese Zelle nicht aufgefüllt (NULL).|9|  
|CaptureSPID|`int`|Die ID der Aufzeichnungssitzung für das Ereignis.|10|  
|ConnectionID|`int`|Die ID der Aufzeichnungsverbindung für das Ereignis.|11|  
|ReplaySPID|`int`|Die ID der Wiedergabesitzung für das Ereignis.|12|  
|DatabaseName|`nvarchar`|Der Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|13|  
|LoginName|`nvarchar`|Der Benutzeranmeldename. Dabei kann es sich entweder [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] um eine Sicherheits Anmeldung oder die Microsoft Windows-Anmelde Informationen im Format *domain_name*\\*user_name*handeln.|14|  
|CaptureHostName|`nvarchar`|Der Name des Computers, auf dem der Clientdienst während der Aufzeichnung ausgeführt wird.|15|  
|ReplayHostName|`nvarchar`|Der Name des Computers, auf dem der Client während der Wiedergabe ausgeführt wird|16|  
|ApplicationName|`nvarchar`|Der Name der Clientanwendung, die während der Aufzeichnung die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verbindung hergestellt hat.|17|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)   
 [Distributed Replay: Anforderungen](distributed-replay-requirements.md)   
 [Befehlszeilenoptionen für das Verwaltungstool &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md)   
 [Konfigurieren von Distributed Replay](configure-distributed-replay.md)  
  
  
