---
title: Schreiben internationaler Transact-SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 64dc9129373a57de2924b2983e14266a67d4915e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62873523"
---
# <a name="write-international-transact-sql-statements"></a>Schreiben internationaler Transact-SQL-Anweisungen
  Datenbanken und Datenbankanwendungen, die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwenden, können leichter von einer Sprache in eine andere übertragen werden bzw. unterstützen mehrere Sprachen, wenn die folgenden Richtlinien eingehalten werden:  
  
-   Ersetzen Sie alle Vorkommen der Datentypen `char`, `varchar` und `text` durch `nchar`, `nvarchar` und `nvarchar(max)`. Auf diese Weise müssen Sie keine Schwierigkeiten mit der Codepagekonvertierung berücksichtigen. Weitere Informationen finden Sie unter [Collation and Unicode Support](collation-and-unicode-support.md).  
  
-   Wenn Vergleiche und Vorgänge in bestimmten Monaten oder an bestimmten Arbeitstagen ausgeführt werden, verwenden Sie die numerischen Datumseinheiten anstelle der Namenszeichenfolgen. Unterschiedliche Spracheinstellungen geben verschiedene Namen für Monate und Arbeitstage zurück. Beispielsweise gibt DATENAME(MONTH,GETDATE()) den Monat May zurück, wenn die Sprache auf US- Englisch festgelegt ist, beim Festlegen der Sprache Deutsch wird Mai und beim Festlegen der Sprache Französisch mai zurückgegeben. Verwenden Sie stattdessen eine Funktion wie DATEPART, die die Monatszahl anstelle des Namens verwendet. Verwenden Sie DATEPART-Namen, wenn Sie Resultsets erstellen, die für einen Benutzer angezeigt werden sollen, da Datumsbezeichnungen häufig aussagekräftiger sind als eine numerische Darstellung. Kopieren Sie jedoch keine logischen Befehle, die davon abhängen, dass die angezeigten Namen aus einer bestimmten Sprache stammen.  
  
-   Wenn Sie Datumseingaben in Vergleichen oder als Eingabe in INSERT- oder UPDATE-Anweisungen angeben, verwenden Sie Konstanten, die in allen Spracheinstellungen gleich interpretiert werden:  
  
    -   ADO-, OLE DB- und ODBC-Anwendungen sollten folgende ODBC-Timestamps und folgende ESCAPE-Klauseln für Datum und Zeit verwenden:  
  
         **{TS '** JJJJ**-**_mm_**-**_DDHH_**:**_mm_**:**_SS_[**.** _fff_] **'}** Beispiel: **{TS '** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **'}**  
  
         **{d '** _JJJJ_ **-** _mm_ **-** _DD_ **'}** Beispiel: **{d '** 1998**-** 09**-** 24 **'}**  
  
         **{t '** _HH_ **:** _mm_ **:** _SS_ **'}** Beispiel: **{t '** 10:02:20 **'}**  
  
    -   Anwendungen, die andere APIs verwenden, oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts, gespeicherte Prozedure und Trigger sollten unstrukturierte Zeichenfolgen verwenden. Zum Beispiel *yyyymmdd* für 19980924.  
  
    -   Anwendungen [!INCLUDE[tsql](../../includes/tsql-md.md)] , die andere APIs oder Skripts, gespeicherte Prozeduren und Trigger verwenden, sollten die Convert-Anweisung mit einem expliziten Formatvorlagen Parameter `time`für `date`alle `smalldate`Konvertierungen zwischen den Datentypen,,, `datetime`, **datetime2**und `datetimeoffset` Datentypen und Zeichen folgen-Datentypen verwenden. Die folgende Anweisung wird beispielsweise für alle Verbindungseinstellungen für Sprach- oder Datumsformate gleich interpretiert:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Weitere Informationen finden Sie unter [CAST und CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
  
