---
title: SQL Server Native Client von ODBC-Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b8ae0fdf9c28ecb488a0b5f0aa285e8597d84072
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784987"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>SQL Server Native Client ODBC-Datenquellen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquellenname (DSN) identifiziert eine ODBC-Datenquelle, die alle Informationen enthält, die eine ODBC-Anwendung zur Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank auf einem bestimmten Server benötigt. Es gibt zwei Methoden, wie Sie einen ODBC-Datenquellennamen definieren können:  
  
-   Öffnen Sie auf einem Client Computer in der Systemsteuerung die Option Verwaltung, und doppelklicken Sie auf **Datenquellen (ODBC)**. Daraufhin wird der ODBC-Datenquellen-Administrator geöffnet, mit dem Sie einen DSN erstellen können.  
  
-   Nennen Sie in einer ODBC-Anwendung [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle enthält Folgendes:  
  
-   Der Name der Datenquelle.  
  
-   Informationen, die zur Verbindung mit einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigt werden.  
  
-   Die Standarddatenbank, die auf einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden soll (optional).  
  
-   Einstellungen, z. B. welche ANSI-Optionen verwendet werden, ob Leistungsstatistiken protokolliert werden (optional) usw.  
  
 Eine ODBC-Anwendung muss nicht unbedingt über eine Datenquelle eine Verbindung herstellen. Die Anwendung muss jedoch dieselben Verbindungsinformationen an die ODBC-Verbindungsfunktion liefern, die der Treiber andernfalls im DSN finden würde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kommunikation mit SQL Server &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
