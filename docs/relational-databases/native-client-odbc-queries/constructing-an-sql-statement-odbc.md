---
title: Erstellen einer SQL-Anweisung (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 96e3c04692360bd13010fe40063b0e761d60b2ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73779978"
---
# <a name="constructing-an-sql-statement-odbc"></a>Erstellen einer SQL-Anweisung (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In ODBC-Anwendungen werden fast alle Datenbankzugriffe mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen ausgeführt. Die Form dieser Anweisungen richtet sich nach den Anforderungen der Anwendung. SQL-Anweisungen können auf folgende Weise gebildet werden:  
  
-   Hartcodiert  
  
     Statische Anweisungen, die von einer Anwendung als feste Aufgabe ausgeführt werden.  
  
-   Zur Laufzeit  
  
     SQL-Anweisungen, die zur Laufzeit gebildet werden und es den Benutzern ermöglichen, die Anweisung mit gängigen Klauseln wie SELECT, WHERE und ORDER BY anzupassen. Hierzu gehören auch von den Benutzern eingegebene Ad-hoc-Abfragen.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Client-ODBC-Treiber analysiert SQL-Anweisungen nur für ODBC-und ISO-Syntax [!INCLUDE[ssDE](../../includes/ssde-md.md)], die nicht direkt von unter [!INCLUDE[tsql](../../includes/tsql-md.md)]stützt werden, die der Treiber transformiert. Jede andere SQL-Syntax wird wie vorliegend an das [!INCLUDE[ssDE](../../includes/ssde-md.md)] weitergeleitet, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] überprüft, ob sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zulässig ist. Dieser Ansatz hat zwei Vorteile:  
  
-   Geringerer Arbeitsaufwand  
  
     Der Arbeitsaufwand des Treibers wird minimiert, weil er nur eine kleine Anzahl von ODBC- und ISO-Klauseln überprüfen muss.  
  
-   Flexibilität  
  
     Programmierer können die Portabilität ihrer Anwendungen anpassen. Um die Portabilität für mehrere Datenbanken zu verbessern, verwenden Sie primär die ODBC- und ISO-Syntax. Um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischen Erweiterungen zu verwenden, verwenden Sie die entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Syntax. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unter [!INCLUDE[tsql](../../includes/tsql-md.md)] stützt die vollständige Syntax, damit ODBC-basierte Anwendungen alle Funktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nutzen können.  
  
 Die Spaltenliste der SELECT-Anweisung sollte nur die Spalten enthalten, die zur Ausführung der aktuellen Aufgabe erforderlich sind. Dadurch werden nicht nur weniger Daten über das Netzwerk gesendet, sondern Datenbankänderungen wirken sich in geringerem Umfang auf die Anwendung aus. Wenn eine Anwendung nicht auf eine Spalte einer Tabelle verweist, dann ist die Anwendung von keinerlei Änderungen betroffen, die an dieser Spalte vorgenommen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
