---
title: Lesezeichen für Zeilen in ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fc90fd2a24e8850922e45d17fb331ce412dde482
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784086"
---
# <a name="scrolling-and-fetching-rows---bookmarking-rows-in-odbc"></a>Scrollen und Abrufen von Zeilen: Kennzeichnen von Zeilen in ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ein Lesezeichen ist ein Wert, der verwendet wird, um eine Zeile mit Daten zu identifizieren. Die Bedeutung des Lesezeichenwerts ist nur dem Treiber oder der Datenquelle bekannt. Der Wert kann so einfach wie eine Zeilennummer oder so komplex wie eine Datenträgeradresse sein. In ODBC fordert die Anwendung ein Lesezeichen für bestimmte Zeilen an, speichert es und gibt es an den Cursor für die Rückgabe an die Zeile zurück.  
  
 Beim Abrufen von Zeilen mit [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)kann eine Anwendung ein Lesezeichen als Grundlage für die Auswahl der Anfangs Zeile verwenden. Dies ist eine Form der absoluten Adressierung, da sie nicht von der aktuellen Cursorposition abhängt. Um einen Bildlauf zu einer mit einem Lesezeichen markierten Zeile durchführen zu können, ruft die Anwendung **SQLFetchScroll** mit der *FetchOrientation* SQL_FETCH_BOOKMARK auf. Dieser Vorgang verwendet das Lesezeichen, auf das das SQL_ATTR_FETCH_BOOKMARK_PTR-Optionsattribut zeigt. Es gibt das Rowset zurück, das mit der Zeile beginnt, die von diesem Lesezeichen identifiziert wird. Eine Anwendung kann einen Offset für diesen Vorgang im *FetchOffset* -Argument des Aufrufens von **SQLFetchScroll**angeben. Wenn ein Offset angegeben ist, wird die erste Zeile des zurückgegebenen Rowsets durch Hinzufügen der Zahl im FetchOffset-Argument zu der Zahl der Zeile, die vom Lesezeichen identifiziert wird, bestimmt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Native Client-ODBC-Treiber unterstützt nur Lesezeichen auf statischen und Keysetcursorn. Wenn beim Festlegen von Lesezeichen ein dynamischer Cursor angefordert wird, wird stattdessen ein Keysetcursor geöffnet.  
  
 Lesezeichen können auch mit der **SQLBulkOperations** -Funktion verwendet werden, um Vorgänge für eine Reihe von Zeilen ab dem Lesezeichen auszuführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bildläufe und Abrufen von Zeilen](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
  
