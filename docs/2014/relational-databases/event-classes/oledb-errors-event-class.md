---
title: OLEDB Errors-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB Errors event class
ms.assetid: 0ce1e906-5d92-42f2-ab38-8771ad5ca008
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a0f4e99247fe1a4a80734e56d8db1e05b961e43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62961066"
---
# <a name="oledb-errors-event-class"></a>OLEDB Errors-Ereignisklasse
  Die OLEDB Errors-Ereignisklasse tritt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in auf, wenn ein-Rückruf eines OLE DB Anbieters einen Fehler zurückgibt. Verwenden Sie diese Ereignisklasse in Ablaufverfolgungen, um ein fehlgeschlagenes HRESULT von einem OLE DB-Anbieter anzuzeigen.  
  
 Wenn die OLEDB Errors-Ereignisklasse in eine Ablaufverfolgung eingeschlossen ist, ist der Verarbeitungsaufwand davon abhängig, wie häufig im Rahmen der Ablaufverfolgung OLE DB-Anbieterfehler für die Datenbank auftreten. Wenn solche Fehler häufig auftreten, kann die Gesamtleistung durch die Ablaufverfolgung erheblich beeinträchtigt werden.  
  
## <a name="oledb-errors-event-class-data-columns"></a>OLEDB Errors-Ereignisklasse (Datenspalten)  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablauf Verfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|Fehler|`int`|Vom Anbieter zurückgegebenes HRESULT.|31|Ja|  
|EventClass|`int`|Ereignistyp = 61.|27|Nein|  
|EventSequence|`int`|Sequenz der OLE DB-Ereignisklasse im Batch|51|Nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LinkedServerName|`nvarchar`|Name des Verbindungsservers|45|Ja|  
|LoginName|`nvarchar`|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|MethodName|`nvarchar`|Der Name der OLE DB-Methode.|47|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|ProviderName|`nvarchar`|Name des OLE DB-Anbieters.|46|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|`nvarchar`|Während des OLE DB-Aufrufs gesendete und empfangene Parameter|1|Nein|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [OLE-Automatisierungsobjekte in Transact-SQL](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
