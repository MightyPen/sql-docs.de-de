---
title: Skalarfunktionsaufrufe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37209a75c03a051e3def4d26fa0d4e7f85d0e91d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67897747"
---
# <a name="scalar-function-calls"></a>Aufrufe von Skalarfunktionen
Skalare Funktionen geben einen Wert für jede Zeile zurück. Die Skalarfunktion "absoluter Wert" nimmt z. b. eine numerische Spalte als Argument an und gibt den absoluten Wert jedes Werts in der Spalte zurück. Die Escapesequenz zum Aufrufen einer Skalarfunktion ist  
  
 **{FN**  _Skalarfunktion_ **}**  
  
 wobei *Scalar-Function* eine der Funktionen ist, die in [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)aufgeführt sind. Weitere Informationen zur Escapesequenz der Skalarfunktion finden Sie unter [Skalarfunktion-Escapesequenz](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md) in Anhang C: SQL-Grammatik.  
  
 Beispielsweise werden mit den folgenden SQL-Anweisungen die gleichen Resultsets von Kundennamen in Großbuchstaben erstellt. In der ersten Anweisung wird die Escapesequenzsyntax verwendet. Die zweite Anweisung verwendet die systemeigene Syntax für Ingres für OS/2 und ist nicht interoperabel.  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 Eine Anwendung kann Aufrufe von Skalarfunktionen mischen, die systemeigene Syntax und Aufrufe von skalaren Funktionen verwenden, die die ODBC-Syntax verwenden. Nehmen Sie beispielsweise an, dass die Namen in der Employee-Tabelle als Nachname, als Komma und als Vorname gespeichert werden. Mit der folgenden SQL-Anweisung wird ein Resultset mit den Nachnamen von Mitarbeitern in der Employee-Tabelle erstellt. Die-Anweisung verwendet die **Teil Zeichenfolge** der ODBC-Skalarfunktion und die SQL Server Skalarfunktion **CHARINDEX** und wird nur auf SQL Server ordnungsgemäß ausgeführt.  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 Für eine maximale Interoperabilität sollten Anwendungen die **Convert** -Skalarfunktion verwenden, um sicherzustellen, dass die Ausgabe einer Skalarfunktion der erforderliche Typ ist. Die **Convert** -Funktion konvertiert Daten von einem SQL-Datentyp in den angegebenen SQL-Datentyp. Die Syntax der **Convert** -Funktion ist  
  
 **Konvertieren (** _value_exp_ **** _data_type_**)**  
  
 Wenn *value_exp* ein Spaltenname ist, das Ergebnis einer anderen Skalarfunktion oder ein Literalwert ist, und *data_type* ein Schlüsselwort ist, das mit dem **#define** Namen übereinstimmt, der von einem SQL-Datentyp Bezeichner verwendet wird, wie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md)definiert. Beispielsweise verwendet die folgende SQL-Anweisung die **Convert** -Funktion, um sicherzustellen, dass die Ausgabe der Funktion " **Cursor** " anstelle eines Zeitstempel-oder Zeichendaten ein Datum ist:  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 Um zu ermitteln, welche Skalarfunktionen von einer Datenquelle unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CONVERT_FUNCTIONS, SQL_NUMERIC_FUNCTIONS, SQL_STRING_FUNCTIONS, SQL_SYSTEM_FUNCTIONS und SQL_TIMEDATE_FUNCTIONS auf. Um zu ermitteln, welche Konvertierungs Vorgänge von der **Convert** -Funktion unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit allen Optionen auf, die mit SQL_CONVERT beginnen.
