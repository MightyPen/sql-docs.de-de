---
title: Konfiguration für "SQL Server Profiler-Replay" (Erweiterte Wiedergabe Optionen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.generaloptions.advanced.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: b4eb34f7-3af6-4a44-ba7e-2b8430ec3cd7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0bf91032c1514037c754fd489ac266cf68063fa4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66089733"
---
# <a name="sql-server-profiler---replay-configuration-advanced-replay-options"></a>SQL Server Profiler - Wiedergabekonfiguration (Erweiterte Wiedergabeoptionen)
  Mithilfe der Registerkarte **Erweiterte Wiedergabeoptionen** des Dialogfelds **Wiedergabekonfiguration** können Sie angeben, auf welche Weise eine Ablaufverfolgungsdatei wiedergegeben werden soll.  
  
 Zum Anzeigen dieses Fensters öffnen Sie mithilfe von [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] eine Ablaufverfolgungsdatei oder -tabelle, die die zur Wiedergabe vorgesehenen Ereignisse enthält. Weitere Informationen finden Sie unter [Replay Requirements](../tools/sql-server-profiler/replay-requirements.md). Wenn die Ablaufverfolgungsdatei oder -tabelle geöffnet ist, klicken Sie im Menü **Wiedergeben** auf **Start**, und stellen Sie dann eine Verbindung mit der Instanz von SQL Server her, auf der die Ablaufverfolgung wiedergegeben werden soll. Klicken Sie anschließend auf die Registerkarte **Erweiterte Wiedergabeoptionen** .  
  
## <a name="options"></a>Tastatur  
 **System-SPIDs wiedergeben**  
 Gibt an, ob [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] die Systemprozess-IDs (SPIDs) wiedergibt.  
  
 **Nur eine SPID wiedergeben**  
 Gibt nur die Aktivität in der Ablaufverfolgungs-Quelldatei wieder, die mit der ausgewählten SPID in Beziehung steht.  
  
 **SPID für Wiedergabe**  
 Gibt an, welche SPID wiedergegeben werden soll.  
  
 **Wiedergabe nach Datum und Zeit beschränken**  
 Durch Aktivieren dieses Kontrollkästchens kann festgelegt werden, dass nur ein Teil der Ablaufverfolgungs-Quelldatei wiedergegeben wird.  
  
 **Startzeit**  
 Datum und Uhrzeit in der Ablaufverfolgungs-Quelldatei, zu der die Wiedergabe beginnen soll.  
  
 **Endzeit**  
 Datum und Uhrzeit in der Ablaufverfolgungs-Quelldatei, zu der die Wiedergabe enden soll.  
  
 **Wartezeit für Systemüberwachung (Sek.)**  
 Gibt die Wartezeit für die Wiedergabe in Sekunden an. Der Standardwert ist 3600 Sekunden (1 Stunde). Die Einstellung bestimmt den Zeitraum, in dem ein Prozess ausgeführt werden kann, bevor er von der Systemüberwachung beendet wird.  
  
 **Abruf Intervall für Systemüberwachung (Sek.)**  
 Gibt das Abrufinterval für die Systemüberwachung während der Wiedergabe in Sekunden an. Der Standardwert ist 60 Sekunden. Mit diesem Wert kann der Benutzer konfigurieren, wie oft die Systemüberwachung Informationen zu potenziell zu beendenden Vorgängen abruft.  
  
 **Überwachung blockierter SQL Server-Prozesse aktivieren**  
 Aktiviert einen Prozess, mit dem nach blockierten oder blockierenden Prozessen gesucht wird.  
  
 **Wartezeit für blockierte Prozesse Monitor Wartezeit (Sek.)**  
 Konfiguriert die Häufigkeit, mit der mithilfe der Überwachung für blockierte Prozesse nach blockierten oder blockierenden Prozessen gesucht wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wiedergeben einer Ablauf Verfolgungs Tabelle &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Wiedergeben einer Ablauf Verfolgungs Datei &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Wiedergeben von Ablaufverfolgungen](../tools/sql-server-profiler/replay-traces.md)  
  
  
