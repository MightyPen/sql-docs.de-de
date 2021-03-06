---
title: Migrieren von Access-Datenbanken zu SQL Server Azure SQL-Datenbank | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 959af9bcb1879dc19d2bfb99253b4c40d637fd1e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68260235"
---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>Migrieren von Access-Datenbanken zu SQL Server-Azure SQL-Datenbank (accesstosql)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) ist ein Tool, das eine umfassende Umgebung bereitstellt, die Sie bei der schnellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration von Access-Datenbanken zu oder SQL Azure unterstützt. Mithilfe von SSMA können Sie den Zugriff und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure Datenbankobjekte überprüfen, die Access-Datenbank für die Migration bewerten, Access-Daten Bank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte konvertieren, Sie in oder SQL Azure laden und dann Daten migrieren.  
  
## <a name="recommended-migration-process"></a>Empfohlener Migrationsprozess  
Verwenden Sie den folgenden Prozess, um Objekte und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten erfolgreich vom Zugriff auf oder SQL Azure zu migrieren:  
  
1.  [Erstellen Sie ein neues SSMA-Projekt](creating-and-managing-projects-accesstosql.md). Nachdem Sie das Projekt erstellt haben, können Sie [Projektoptionen festlegen](setting-conversion-and-migration-options-accesstosql.md), einschließlich Konvertierungsoptionen, Migrations Optionen und Datentyp Zuordnungen.  
  
2.  [Fügen Sie dem Projekt Zugriffsdaten Bank Dateien hinzu](adding-and-removing-access-database-files-accesstosql.md) .  
  
    Sie können einzelne Dateien hinzufügen, einschließlich Dateien, die Sie auf dem Computer oder im Netzwerk finden.  
  
3.  Stellen [Sie eine Verbindung mit der-Ziel Instanz SQL Server](connecting-to-sql-server-accesstosql.md) her, oder stellen [Sie eine Verbindung mit der Ziel Instanz von SQL Azure](connecting-to-azure-sql-db-accesstosql.md)  
  
    Sie können entweder eine Verbindung mit SQL Server oder SQL Azure herstellen.  
  
4.  Ordnen Sie [die Quell-und Ziel Datenbanken](mapping-source-and-target-databases-accesstosql.md)zu, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Zuordnung zwischen einer oder mehreren Zugriffs Datenbanken und oder SQL Azure Schemas anzupassen.  
  
5.  Optional können Sie [einen Bewertungsbericht erstellen](assessing-access-database-objects-for-conversion-accesstosql.md) , um zu bestimmen, ob die Access-Datenbankobjekte erfolgreich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in konvertiert oder SQL Azure werden können.  
  
6.  [Konvertieren Sie Access-Datenbankobjekte](converting-access-database-objects-accesstosql.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Objekt Definitionen.  
  
7.  [Laden Sie die konvertierten Datenbankobjekte in SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
    Sie können entweder die Datenbankobjekte mithilfe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von SSMA in oder SQL Azure laden, oder Sie können [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts speichern.  
  
8.  [Migrieren Sie Zugriffsdaten in SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
    > [!NOTE]  
    > Sie können Schemas und Daten in einem Schritt konvertieren, laden und migrieren. Klicken Sie zum Durchführen einer Migration mit nur einem Klick auf die Schaltfläche **konvertieren, laden und Migrieren** .  
  
9. Wenn Sie möchten, dass ihre Zugriffs Anwendungen die Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure verwenden, [Verknüpfen Sie die Zugriffs Tabellen mit den SQL Server Tabellen](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
Sie können auch den Migrations-Assistenten verwenden, um Sie durch diesen Prozess zu führen. Weitere Informationen finden Sie unter [Migrations-Assistent](migration-wizard-accesstosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Ersten Schritte mit SQL Server Migration Assistant für den Zugriff](getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Vorbereiten einer Access-Datenbank für die Migration](preparing-access-databases-for-migration-accesstosql.md)
