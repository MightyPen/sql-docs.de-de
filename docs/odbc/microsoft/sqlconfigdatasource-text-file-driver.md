---
title: SQLConfigDataSource (Text Datei Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 46bb00fb01ed3fee8098420794af089f2d8b981e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054082"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (Textdateitreiber)
> [!NOTE]  
>  In diesem Thema werden Treiber spezifische Informationen zu Textdateien bereitstellt. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, um eine Datenquelle hinzuzufügen, zu ändern oder zu löschen, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|CHARACTERSET|Für den Text Treiber, OEM oder ANSI.|  
|COLNAMEHEADER|Gibt für den Text Treiber an, ob der erste Datensatz der Daten die Spaltennamen angibt. Entweder true oder false.|  
|DefaultDir|Die Pfadspezifikation für das Verzeichnis.|  
|Beschreibung|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie die **Beschreibung** im Setup Dialogfeld festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DriverID|Eine ganzzahlige ID für den Treiber. 27 (Text)|  
|Extensions|Listet die Dateinamen Erweiterungen der Text Dateien in der Datenquelle auf.<br /><br /> Dadurch wird die gleiche Option wie die **Erweiterungs Liste** im Setup Dialogfeld festgelegt.|  
|RA|Dateityp Text|  
|FILETYPE|Dateityp für den Text Treiber (Text).|  
|FORMAT|Für den Text Treiber kann FixedLength, tabdelikoff, csvdelikoff (durch Kommas) oder durch Trennzeichen () (durch das in den Klammern angegebene Sonderzeichen) sein. Das Sonderzeichen ist ein Zeichen lang und kann im Zeichen-, Dezimal-oder Hexadezimal Format vorliegen.|  
|MaxScanRows|Die Anzahl der Zeilen, die beim Festlegen des Datentyps einer Spalte auf Grundlage vorhandener Daten gescannt werden sollen.<br /><br /> Für den Text Treiber können Sie eine Zahl zwischen 1 und 32767 für die Anzahl der zu überprüfenden Zeilen eingeben. Allerdings ist der Wert immer standardmäßig 25. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)<br /><br /> Dadurch wird die Option für die **zu über** prüfenden Zeilen im Setup Dialogfeld festgelegt.|  
|READONLY|TRUE, wenn die Datei schreibgeschützt werden soll. FALSE, wenn die Datei nicht schreibgeschützt sein soll.<br /><br /> Dadurch wird die gleiche **Option wie im** Setup Dialogfeld schreibgeschützt festgelegt.|
