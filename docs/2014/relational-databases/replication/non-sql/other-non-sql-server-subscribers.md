---
title: Andere Nicht-SQL Server-Abonnenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 135d317d74a720d51c966ed92f1c305f8c04b838
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63021948"
---
# <a name="other-non-sql-server-subscribers"></a>Andere Nicht-SQL Server-Abonnenten
  Eine Liste der von[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)]unterstützten nicht--Abonnenten finden Sie unter [nicht-SQL Server-Abonnenten](non-sql-server-subscribers.md). Dieses Thema enthält Informationen zu den Anforderungen für ODBC-Treiber und OLE DB-Anbieter.  
  
## <a name="odbc-driver-requirements"></a>Anforderungen für ODBC-Treiber  
 Der ODBC-Treiber muss folgende Voraussetzungen erfüllen:  
  
-   Er muss ODBC Level-1-kompatibel sein.  
  
-   Er muss threadsicher sein und sich für die Prozessorarchitektur (Intel oder Alpha) und die Plattform (32 Bit oder 64 Bit) eignen, auf der der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Verteiler ausgeführt wird.  
  
-   Er muss in der Lage sein, Transaktionen zu verarbeiten.  
  
-   Er muss die Datendefinitionssprache (Data Definition Language, DDL) unterstützen.  
  
-   Er darf nicht schreibgeschützt sein.  
  
-   Er muss lange Tabellennamen unterstützen, wie z. B. **MSreplication_subscriptions**.  
  
## <a name="replicating-using-ole-db-interfaces"></a>Replikation mithilfe von OLE DB-Schnittstellen  
 OLE DB-Anbieter müssen folgende Objekte für die Transaktionsreplikation unterstützen.  
  
-   **DataSource** -Objekt  
  
-   **Session** -Objekt  
  
-   **Command** -Objekt  
  
-   **** Rowsetobjekt  
  
-   **Error** -Objekt  
  
### <a name="datasource-object-interfaces"></a>Schnittstellen für DataSource-Objekte  
 Die folgenden Schnittstellen sind erforderlich, um eine Verbindung mit einer Datenquelle herzustellen:  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 Wenn der Anbieter die **IDBInfo** -Schnittstelle unterstützt, verwendet [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Schnittstelle zum Abrufen von Informationen, wie z. B. des Bezeichners in Anführungszeichen, der maximalen Länge einer SQL-Anweisung und der maximalen Anzahl von Zeichen in Tabellen- und Spaltennamen.  
  
### <a name="session-object-interfaces"></a>Schnittstellen für Session-Objekte  
 Die folgenden Schnittstellen sind erforderlich:  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### <a name="command-object-interfaces"></a>Schnittstellen für Command-Objekte  
 Die folgenden Schnittstellen sind erforderlich:  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** ist zum Erstellen von Parameteraccessoren erforderlich. Wenn der Anbieter **IColumnRowset**unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , verwendet diese Schnittstelle, um zu bestimmen, ob eine Spalte eine Identitäts Spalte ist.  
  
### <a name="rowset-object-interfaces"></a>Schnittstellen für Rowset-Objekte  
 Die folgenden Schnittstellen sind erforderlich:  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 Eine Anwendung sollte ein Rowset für eine replizierte Tabelle öffnen, das in der Abonnementdatenbank erstellt wird. **IColumnsInfo** und **IAccessor** sind erforderlich, um auf Daten im Rowset zuzugreifen.  
  
### <a name="error-object-interfaces"></a>Schnittstellen für Error-Objekte  
 Verwenden Sie die folgenden Schnittstellen zur Verwaltung von Fehlern:  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Verwenden Sie **ISQLErrorInfo** , wenn diese Schnittstelle vom OLE DB-Anbieter unterstützt wird.  
  
 Weitere Informationen zum OLE DB-Anbieter finden Sie in der Dokumentation zum jeweiligen OLE DB-Anbieter.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nicht-SQL Server-Abonnenten](non-sql-server-subscribers.md)  
  
  
