---
title: Tabelle kopieren oder Datenbank abfragen (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 524e878933652699bef6e31da42d3a784b54df7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62892642"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a>Tabelle kopieren oder Datenbank abfragen (SQL Server-Import/Export-Assistent)
  Verwenden Sie die Seite **Tabelle kopieren oder Abfrage angeben** , um anzugeben, wie Daten kopiert werden sollen. Sie können eine grafische Oberfläche zum Auswählen zu kopierender vorhandener Datenbankobjekte verwenden, oder Sie erstellen mithilfe von Transact-SQL eine komplexere Abfrage.  
  
 Weitere Informationen zu diesem Assistenten finden Sie unter [SQL Server-Import/Export-Assistenten](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Weitere Informationen zu den Optionen für das Starten des Assistenten sowie zu den Berechtigungen, die zum erfolgreichen Ausführen des Assistenten erforderlich sind, finden Sie unter [Ausführen des SQL Server-Import/Export-Assistenten](start-the-sql-server-import-and-export-wizard.md).  
  
 Mit dem SQL Server-Import/Export-Assistenten werden Daten aus einer Quelle in ein Ziel kopiert. Mit dem Assistenten können auch eine Zieldatenbank und Zieltabellen erstellt werden. Wenn Sie jedoch mehrere Datenbanken, Tabellen oder andere Datenbankobjekte kopieren müssen, verwenden Sie stattdessen den Assistenten zum Kopieren von Datenbanken. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Tastatur  
 **Kopieren von Daten aus mindestens einer Tabelle oder Sicht**  
 Kopieren Sie Felder aus ausgewählten Quell Tabellen und-Sichten mithilfe des Dialog Felds **Quell Tabellen und-Sichten auswählen** in das angegebene Ziel bzw. die angegebenen Ziele. Verwenden Sie diese Option, wenn Sie alle Quelldaten ohne Filtern oder Ordnen der Datensätze kopieren möchten.  
  
 Wenn Sie einen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -Datenanbieter verwenden, um die Verbindung zur Datenquelle herzustellen, ist die Option **Daten aus mindestens einer Tabelle oder Sicht kopieren** unter Umständen nicht verfügbar. Diese Option ist nur für Anbieter verfügbar, die über einen ProviderDescription-Abschnitt in der Datei ProviderDescriptors.xml verfügen. Jeder ProviderDescription-Abschnitt enthält die Informationen, die erforderlich sind, um Metadaten von dem entsprechenden Anbieter abzurufen. Standardmäßig enthält die Datei ProviderDescriptors.xml nur für die folgenden Anbieter einen ProviderDescription-Abschnitt:  
  
-   System.Data.SqlClient  
  
-   System.Data.OracleClient  
  
-   System.Data.OleDb  
  
-   System.Data.Odbc  
  
 Um die Option **Daten aus mindestens einer Tabelle oder Sicht kopieren** für zusätzliche Anbieter verfügbar zu machen, können Drittanbieter Ihrer Datei "ProviderDescriptors. xml" eigene ProviderDescriptor-Abschnitte hinzufügen. Standardmäßig befindet sich diese Datei im \< *Laufwerk*>: \Programme\Microsoft SQL server\100\dt\providerdescriptors. Um die Anforderungen für den ProviderDescriptor-Abschnitt zu prüfen, öffnen Sie die Schemadatei ProviderDescriptors.xsd, die sich standardmäßig im selben Ordner befindet wie die Datei ProviderDescriptors.xml.  
  
 **Abfrage zum Angeben der zu übertragenden Daten schreiben**  
 Erstellen Sie SQL-Anweisungen zum Abrufen von Zeilen mithilfe des Dialog Felds **Quell Abfrage bereitstellen** . Mit dieser Option können Sie die Quelldaten während des Kopiervorgangs ändern oder einschränken. Nur die Zeilen, die den Auswahlkriterien entsprechen, stehen dann zum Kopieren zur Verfügung.  
  
  
