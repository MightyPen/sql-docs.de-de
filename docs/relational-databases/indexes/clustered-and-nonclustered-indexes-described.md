---
title: Beschreibung von gruppierten und nicht gruppierten Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- query optimizer [SQL Server], index usage
- index concepts [SQL Server]
ms.assetid: b7d6b323-728d-4763-a987-92e6292f6f7a
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e3b0fdb182b3623f4461544d94347544d7d19bf6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68811133"
---
# <a name="clustered-and-nonclustered-indexes-described"></a>Beschreibung von gruppierten und nicht gruppierten Indizes

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Ein Index ist eine Struktur auf dem Datenträger, die einer Tabelle oder einer Sicht zugeordnet ist und durch die das Abrufen von Zeilen aus der Tabelle oder Sicht beschleunigt wird. Ein Index enthält Schlüssel, die aus einer oder mehreren Spalten in der Tabelle oder Sicht erstellt werden. Diese Schlüssel werden in einer Struktur (B-Struktur) gespeichert, die es [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht, die den Schlüsselwerten zugeordneten Zeilen schnell und effizient zu finden.

Eine Tabelle oder Sicht kann die folgenden Indextypen enthalten:

- Gruppiert

  - Gruppierte Indizes sortieren und speichern die Datenzeilen in der Tabelle oder Sicht basierend auf ihren Schlüsselwerten. Dies sind die Spalten, die in der Indexdefinition enthalten sind. Pro Tabelle kann nur ein gruppierter Index vorhanden sein, da die Datenzeilen nur in einer Reihenfolge gespeichert werden können.  
  - Datenzeilen in einer Tabelle werden nur dann in sortierter Reihenfolge gespeichert, wenn die Tabelle einen gruppierten Index enthält. Wenn eine Tabelle einen gruppierten Index besitzt, wird die Tabelle als gruppierte Tabelle bezeichnet. Wenn eine Tabelle nicht über einen gruppierten Index verfügt, werden die Datenzeilen in einer nicht geordneten Struktur gespeichert, die als Heap bezeichnet wird.

- Nicht gruppiert

  - Nicht gruppierte Indizes weisen eine Struktur auf, die von den Datenzeilen getrennt ist. Ein nicht gruppierter Index enthält die Schlüsselwerte des nicht gruppierten Indexes. Jeder Schlüsselwerteintrag verfügt über einen Zeiger auf die Datenzeile, die den Schlüsselwert enthält.
  - Der Zeiger von einer Indexzeile in einem nicht gruppierten Index auf eine Datenzeile wird als Zeilenlokator bezeichnet. Die Struktur des Zeilenlokators hängt davon ab, ob die Datenseiten in einem Heap oder einer gruppierten Tabelle gespeichert sind. Bei einem Heap ist der Zeilenlokator ein Zeiger auf die Zeile. Bei einer gruppierten Tabelle entspricht der Zeilenlokator dem Schlüssel des gruppierten Indexes.

  - Sie können der Blattebene des nicht gruppierten Indexes Nichtschlüsselspalten hinzufügen, um vorhandene Beschränkungen des Indexschlüssels zu umgehen und vollständig abgedeckte, indizierte Abfragen auszuführen. Weitere Informationen finden Sie unter [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md). Weitere Informationen zu Einschränkungen von Indexschlüsseln finden Sie unter [Spezifikationen der maximalen Kapazität für SQL Server](../../sql-server/maximum-capacity-specifications-for-sql-server.md).

Sowohl gruppierte als auch nicht gruppierte Indizes können eindeutig sein. Dies bedeutet, dass nicht derselbe Indexschlüsselwert für zwei oder mehr Zeilen verwendet werden darf. Andernfalls handelt es sich nicht um einen eindeutigen Index, und mehrere Zeilen können denselben Schlüsselwert verwenden. Weitere Informationen finden Sie unter [Erstellen eindeutiger Indizes](../../relational-databases/indexes/create-unique-indexes.md).

Indizes werden bei jeder Änderung der Tabellendaten automatisch für eine Tabelle oder Sicht verwaltet.

Zusätzliche Indextypen für besondere Zwecke finden Sie unter [Indexes](../../relational-databases/indexes/indexes.md) .

## <a name="indexes-and-constraints"></a>Indizes und Einschränkungen

Indizes werden automatisch erstellt, wenn PRIMARY KEY- und UNIQUE-Einschränkungen für Tabellenspalten definiert werden. Wenn Sie beispielsweise eine Tabelle mit einer UNIQUE-Einschränkung erstellen, erstellt [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatisch einen nicht gruppierten Index. Wenn Sie einen PRIMARY KEY konfigurieren, erstellt die [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatisch einen gruppierten Index, falls noch kein gruppierter Index vorhanden ist. Wenn Sie versuchen, eine PRIMARY KEY-Einschränkung für eine vorhandene Tabelle zu erzwingen, und für die Tabelle bereits ein gruppierter Index vorhanden ist, erzwingt SQL Server den primären Schlüssel mit einem nicht gruppierten Index.

Weitere Informationen finden Sie unter [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md) und [Create Unique Constraints](../../relational-databases/tables/create-unique-constraints.md).

## <a name="how-indexes-are-used-by-the-query-optimizer"></a>Verwenden von Indizes durch den Abfrageoptimierer

Sorgfältig entworfene Indizes können die E/A-Operationen dem Datenträger verringern und weniger Systemressourcen belegen. Sie optimieren aus diesem Grund die Abfrageleistung. Indizes können bei einer Vielzahl von Abfragen hilfreich sein, die die Anweisungen SELECT, UPDATE, DELETE oder MERGE enthalten. Sehen Sie sich die `SELECT Title, HireDate FROM HumanResources.Employee WHERE EmployeeID = 250` -Abfrage in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Beispieldatenbank an. Wenn diese Abfrage ausgeführt wird, wertet der Abfrageoptimierer alle verfügbaren Methoden zum Abrufen der Daten aus und wählt dann die effizienteste Methode aus. Bei dieser Methode kann es sich um einen Tabellenscan oder möglicherweise um einen Scan eines Indexes oder mehrerer Indizes handeln, wenn Indizes vorhanden sind.

Bei der Ausführung eines Tabellenscans liest der Abfrageoptimierer alle Zeilen in der Tabelle und extrahiert dann die Zeilen, die die Abfragekriterien erfüllen. Ein Tabellenscan generiert zahlreiche E/A-Operationen des Datenträgers und kann ressourcenintensiv sein. Ein Tabellenscan kann jedoch die effizienteste Methode sein, wenn z. B. das Resultset der Abfrage einen großen Prozentsatz der Zeilen aus der Tabelle enthält.

Wenn der Abfrageoptimierer einen Index verwendet, werden die Indexschlüsselspalten durchsucht, der Speicherort der von der Abfrage benötigten Zeilen ermittelt und die entsprechenden Zeilen aus diesem Speicherort extrahiert. Im Allgemeinen ist das Durchsuchen des Indexes wesentlich schneller als das Durchsuchen der Tabelle, weil ein Index im Gegensatz zu einer Tabelle häufig nur sehr wenige Spalten pro Zeile enthält und die Zeilen eine sortierte Reihenfolge aufweisen.

 Der Abfrageoptimierer wählt beim Ausführen von Abfragen normalerweise die effizienteste Methode aus. Wenn jedoch keine Indizes verfügbar sind, muss der Abfrageoptimierer einen Tabellenscan verwenden. Ihre Aufgabe besteht darin, Indizes zu entwerfen und zu erstellen, die optimal für Ihre Umgebung geeignet sind, damit der Abfrageoptimierer seine Auswahl unter mehreren effizienten Indizes treffen kann. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt den [Datenbankoptimierungsratgeber](../../relational-databases/performance/database-engine-tuning-advisor.md) bereit, der Sie bei der Analyse Ihrer Datenbankumgebung und der Auswahl der geeigneten Indizes unterstützt.

> [!IMPORTANT]
> Weitere Informationen zu den Richtlinien und Besonderheiten für das Entwerfen von Indizes finden Sie unter [SQL Server Index Design Guide (Handbuch zum Entwerfen von SQL Server-Indizes)](../../relational-databases/sql-server-index-design-guide.md).

## <a name="related-content"></a>Verwandte Inhalte

- [Handbuch zum SQL Server Indexentwurf](../../relational-databases/sql-server-index-design-guide.md)
- [Erstellen gruppierter Indizes](../../relational-databases/indexes/create-clustered-indexes.md)
- [Erstellen nicht gruppierter Indizes](../../relational-databases/indexes/create-nonclustered-indexes.md)
