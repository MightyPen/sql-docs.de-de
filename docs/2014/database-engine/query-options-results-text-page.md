---
title: Abfrage Options Ergebnisse (Textseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 8d96384a4a4f4adbb52855a45f1bc00d3aadd85d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088985"
---
# <a name="query-options-results-text-page"></a>Abfrageoptionen, Ergebnisse (Seite Text)
  Mithilfe dieser Seite können Sie die Anzeigeoptionen für Abfrageergebnisse bestimmen, die im Textformat ausgegeben werden. Die Einstellungen auf dieser Seite gelten auch dann, wenn **Ergebnisse in Datei** ausgewählt wurde.  
  
 **Ausgabeformat**  
 Standardmäßig werden die Ausgaben in Spalten angezeigt, die durch Auffüllen der Ergebnisse mit Leerstellen erstellt werden. Als weitere Optionen können Kommas, Tabstopps oder Leerzeichen zur Trennung der Spalten gewählt werden. Aktivieren Sie das Kontrollkästchen **Benutzerdefiniertes Trennzeichen** , um im Feld **Benutzerdefiniertes Trennzeichen** ein anderes Trennzeichen festzulegen.  
  
 **Benutzerdefiniertes Trennzeichen**  
 Geben Sie das gewünschte Zeichen zum Trennen der Spalten an. Diese Option ist nur verfügbar, wenn im Feld **Ausgabeformat** das Kontrollkästchen **Benutzerdefiniertes Trennzeichen** aktiviert wurde.  
  
 **Spaltenheader im Resultset einschließen**  
 Deaktivieren Sie dieses Kontrollkästchen, wenn Sie nicht möchten, dass jede Spalte mit einem Spaltentitel versehen wird.  
  
 **Scrollen beim Empfangen von Ergebnissen**  
 Aktivieren Sie dieses Kontrollkästchen, wenn zuerst die zuletzt zurückgegebenen Datensätze am unteren Ende der Ergebnisliste angezeigt werden sollen. Deaktivieren Sie dieses Kontrollkästchen, wenn zunächst die ersten empfangenen Zeilen angezeigt werden sollen.  
  
 **Numerische Werte rechtsbündig ausrichten**  
 Aktivieren Sie dieses Kontrollkästchen, um numerische Werte an der Spalte rechts auszurichten. Das kann die Überprüfung von Zahlen mit einer festen Anzahl von Dezimalstellen erleichtern.  
  
 **Ergebnis nach Ausführung der Abfrage verwerfen**  
 Gibt Arbeitsspeicher frei, indem die Abfrageergebnisse nach der Anzeige auf dem Bildschirm verworfen werden.  
  
 **Ergebnisse auf separater Registerkarte anzeigen**  
 Aktivieren Sie dieses Kontrollkästchen, um das Resultset in einem neuen Dokumentfenster anzuzeigen statt im unteren Bereich des Dokumentfensters der Abfrage.  
  
 **Nach Ausführung der Abfrage zur Ergebnisregister Karte wechseln**  
 Aktivieren Sie dieses Kontrollkästchen, wenn der Fokus automatisch auf das Resultset verschoben werden soll.  
  
 **Maximale Anzahl von Zeichen, die in jeder Spalte angezeigt werden**  
 Dieser Wert liegt standardmäßig bei 256. Erhöhen Sie diesen Wert, wenn Sie größere Resultsets ohne Kürzungen anzeigen möchten.  
  
 **Auf Standard zurücksetzen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
## <a name="saving-a-text-result-set-with-headers"></a>Speichern eines Resultsets als Text mit Header  
 Um Abfrageergebnisse als Textdatei mit Header zu speichern, aktivieren Sie das Kontrollkästchen **Spaltenheader im Resultset einschließen** , und wählen Sie ein getrenntes Ausgabeformat aus. Jetzt enthält die Berichtsdatei Header, wenn Sie auf der Symbolleiste auf **Ergebnisse in Datei** klicken, oder wenn Sie mit der rechten Maustaste auf Abfrageergebnisse klicken, dann auf **Ergebnisse speichern unter**klicken, einen Dateinamen eingeben und dann auf **Speichern**klicken.  
  
  
