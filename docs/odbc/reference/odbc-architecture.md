---
title: ODBC-Architektur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], components
- ODBC architecture [ODBC]
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 781a214d3ca059a442680c332d79aad48914976c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111220"
---
# <a name="odbc-architecture"></a>ODBC-Architektur
Die ODBC-Architektur verfügt über vier Komponenten:  
  
-   **Anwendung** Führt die Verarbeitung durch und ruft ODBC-Funktionen auf, um SQL-Anweisungen zu senden und Ergebnisse abzurufen.  
  
-   **Treiber-Manager** Lädt Treiber im Namen einer Anwendung und entlädt Sie. Verarbeitet ODBC-Funktionsaufrufe oder übergibt sie an einen Treiber.  
  
-   **Treiber** Verarbeitet ODBC-Funktionsaufrufe, übermittelt SQL-Anforderungen an eine bestimmte Datenquelle und gibt Ergebnisse an die Anwendung zurück. Bei Bedarf ändert der Treiber die Anforderung einer Anwendung so, dass die Anforderung der vom zugeordneten DBMS unterstützten Syntax entspricht.  
  
-   **Datenquelle** Besteht aus den Daten, auf die der Benutzer zugreifen möchte, und dem zugeordneten Betriebssystem, DBMS und der Netzwerkplattform (sofern vorhanden), die für den Zugriff auf das DBMS verwendet werden.  
  
 Beachten Sie die folgenden Punkte zur ODBC-Architektur. Zuerst können mehrere Treiber und Datenquellen vorhanden sein, sodass die Anwendung gleichzeitig auf Daten aus mehreren Datenquellen zugreifen kann. Zweitens wird die ODBC-API an zwei Stellen verwendet: zwischen der Anwendung und dem Treiber-Manager und zwischen dem Treiber-Manager und den einzelnen Treibern. Die Schnittstelle zwischen dem Treiber-Manager und den Treibern wird manchmal als *Dienstanbieter Schnittstelle* oder *SPI*bezeichnet. Für ODBC sind die Anwendungsprogrammierschnittstelle (Application Programming Interface, API) und die Dienstanbieter Schnittstelle (SPI) identisch. Das heißt, der Treiber-Manager und jeder Treiber verfügen über dieselbe Schnittstelle wie die gleichen Funktionen.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Anwendungen](../../odbc/reference/applications.md)  
  
-   [Der Treiber-Manager](../../odbc/reference/the-driver-manager.md)  
  
-   [Treiber](../../odbc/reference/drivers.md)  
  
-   [Projektmappen-Explorer](../../odbc/reference/data-sources.md)
