---
title: SQL Server, Datenbankspiegelung (Objekt) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Database Mirroring
- database mirroring [SQL Server], performance counters
- performance counters [SQL Server], database mirroring
- Database Mirroring object
ms.assetid: a27b51ee-7637-4525-9424-bcc16947dc13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7834d2f5d0fc8a8e849f796eab93259682ea377c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250668"
---
# <a name="sql-server-database-mirroring-object"></a>SQL Server, Datenbankspiegelung (Objekt)
  Das **SQLServer:Datenbankspiegelung** -Leistungsobjekt enthält Leistungsindikatoren, die Informationen zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankspiegelung melden. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|**Empfangene Bytes/Sekunde**|Anzahl von empfangenen Byte pro Sekunde.|  
|**Gesendete Byte/Sekunde**|Anzahl von gesendeten Byte pro Sekunde.|  
|**Empfangene Protokollbytes/s**|Anzahl von empfangenen Protokollbytes pro Sekunde.|  
|**Protokollbytes, die pro Sekunde aus dem Cache wiederholt wurden**|Anzahl der Protokollbytes, die in der letzten Sekunde aus dem Cache des Spiegelungsprotokolls abgerufen wurden.<br /><br /> Dieser Zähler wird auf nur dem Spiegelserver verwendet. Auf dem Prinzipalserver ist der Wert immer 0.|  
|**Protokollbytes, die vom Cache pro Sekunde gesendet wurden**|Anzahl der Protokollbytes, die in der letzten Sekunde aus dem Cache des Spiegelungsprotokolls gesendet wurden.<br /><br /> Dieser Zähler wird auf nur dem Prinzipalserver verwendet. Auf dem Spiegelserver ist der Wert immer 0.|  
|**Gesendete Protokollbytes/Sekunde**|Anzahl von gesendeten Protokollbytes pro Sekunde.|  
|**Empfangene komprimierte Protokollbytes/Sek**|Anzahl von komprimierten Protokollbytes, die in der letzten Sekunde empfangen wurden.|  
|**Gesendete komprimierte Protokollbytes/Sek**|Anzahl von komprimierten Protokollbytes, die in der letzten Sekunde gesendet wurden.|  
|**Protokollwartezeit für Festschreiben (ms)**|Millisekunden, die Protokollblöcke in der letzten Sekunde gewartet haben, bis sie auf dem Datenträger festgeschrieben werden.|  
|**Verbleibende Protokollkilobytes**|Gesamtanzahl von Protokollkilobytes, die nach dem Failover von dem neuen Spiegelserver noch durchsucht werden müssen.<br /><br /> Dieser Zähler wird während der Rollbackphase nur von dem Spiegelserver verwendet. Nachdem die Rollbackphase abgeschlossen ist, wird der Zähler auf 0 zurückgesetzt. Auf dem Prinzipalserver ist der Wert immer 0.|  
|**Gescannte Protokollkilobytes**|Gesamtanzahl von Protokollkilobytes, die seit dem Failover von dem neuen Spiegelserver durchsucht wurden.<br /><br /> Dieser Zähler wird während der Rollbackphase nur von dem Spiegelserver verwendet. Nachdem die Rollbackphase abgeschlossen ist, wird der Zähler auf 0 zurückgesetzt. Auf dem Prinzipalserver ist der Wert immer 0.|  
|**Protokollwartezeit für Sendeflusssteuerung (ms)**|Anzahl der Millisekunden, die die Protokolldatenstrom-Meldungen in der letzten Sekunde auf Sendedatenfluss-Steuerung gewartet haben.<br /><br /> Das Senden von Protokolldaten und Metadaten ist der datenintensivste Vorgang bei der Datenbankspiegelung, der die Datenbankspiegelungspuffer und die Service Broker-Sendepuffer möglicherweise monopolisiert. Verwenden Sie diesen Zähler, um die Verwendung dieses Puffers in der Datenbankspiegelungs-Sitzung zu überwachen.|  
|**Protokollsende-Warteschlange KB**|Gesamtanzahl von Protokollkilobytes, die noch nicht an den Spiegelserver gesendet wurden.|  
|**Gespiegelte geschriebene Transaktionen/Sek**|Anzahl von Transaktionen, die Daten in der letzten Sekunde in die gespiegelte Datenbank geschrieben und gewartet haben, bis das Protokoll zur Durchführung eines Commits an den Spiegel gesendet wird.<br /><br /> Dieser Zähler wird nur erhöht, wenn der Prinzipalserver aktiv Protokolldatensätze an den Spiegelserver sendet.|  
|**Gesendete Seiten/Sekunde**|Anzahl von gesendeten Seiten pro Sekunde.|  
|**Empfangsvorgänge/Sekunde**|Anzahl von empfangenen Spiegelungsmeldungen pro Sekunde.|  
|**Byte wiederholen/Sekunde**|Anzahl von Protokollbytes pro Sekunde, für die in der Spiegeldatenbank ein Rollforward ausgeführt wird.|  
|**Wiederholungswarteschlange KB**|Gesamtanzahl der Kilobytes des festgeschriebenen Protokolls, die derzeit noch auf die Spiegeldatenbank angewendet werden müssen, um ein Rollforward dafür auszuführen. Dieser Wert wird vom Spiegel an den Prinzipal gesendet.|  
|**Sende-/Empfangsbestätigungszeit**|Millisekunden, die Nachrichten pro Sekunde auf die Bestätigung vom Partner gewartet haben.<br /><br /> Dieser Zähler ist bei der Behandlung eines Problems hilfreich, das möglicherweise durch einen Netzwerkengpass verursacht wird, z. B. unerklärliche Failover, eine große Sendewarteschlage oder eine hohe Transaktionslatenzzeit. In einem solchen Fall können Sie den Wert dieses Zählers analysieren, um zu bestimmen, ob das Problem durch das Netzwerk verursacht wird.|  
|**Sendevorgänge/Sekunde**|Anzahl von gesendeten Spiegelungsmeldungen pro Sekunde.|  
|**Transaktionsverzögerung**|Verzögerung beim Warten auf die Bestätigung eines nicht abgeschlossenen Commits.|  
  
> [!NOTE]  
>  Auf jedem Partner wird abhängig von der Rolle, die der Partner derzeit ausführt, für einige der Indikatoren der Wert 0 angezeigt.  
  
## <a name="remarks"></a>Bemerkungen  
 Mithilfe der Leistungsindikatoren können Sie die Leistung der Datenbankspiegelung überwachen. Beispielsweise können Sie den Indikator **Transaktionsverzögerung** untersuchen, um festzustellen, ob die Datenbankspiegelung Auswirkungen auf die Leistung des Prinzipalservers hat, oder Sie können die Indikatoren **Wiederholungswarteschlange** und **Protokollsende-Warteschlange** untersuchen, um festzustellen, wie gut die Spiegeldatenbank mit der Prinzipaldatenbank Schritt halten kann. Mit dem Leistungsindikator **Gesendete Protokollbytes/Sekunde** können Sie überwachen, wie viele Protokollbytes pro Sekunde gesendet wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
