---
title: Erstellen eines Datenbankschemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 980b179f39edc3e93e5cb0bc105b6b2f8d12bb58
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "72903744"
---
# <a name="create-a-database-schema"></a>Erstellen eines Datenbankschemas
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  In diesem Thema wird beschrieben, wie ein Schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]erstellt wird.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Das neue Schema ist im Besitz einer der folgenden Prinzipale auf Datenbankebene: Datenbankbenutzer, Datenbankrolle oder Anwendungsrolle. Objekte, die innerhalb eines Schemas erstellt werden, gehören dem Besitzer des Schemas und haben für **principal_id** in **sys.objects** einen NULL-Wert. Der Besitz von Objekten, die Schemas als Bereich aufweisen, kann an jeden Prinzipal auf Datenbankebene übertragen werden, aber der Schemabesitzer behält immer die CONTROL-Berechtigung für Objekte innerhalb des Schemas.  
  
-   Wenn Sie beim Erstellen eines Datenbankobjekts einen gültigen Domänenprinzipal als Objektbesitzer (Benutzer oder Gruppe) angeben, wird der Domänenprinzipal der Datenbank als Schema hinzugefügt. Das neue Schema befindet sich im Besitz des Domänenprinzipals.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
  
-   Erfordert die CREATE SCHEMA-Berechtigung für die Datenbank.  
  
-   Um einen anderen Benutzer als den Besitzer des zu erstellenden Schemas anzugeben, benötigt der Aufrufer die IMPERSONATE-Berechtigung für diesen Benutzer. Wenn eine Datenbankrolle als Besitzer angegeben wird, muss der Aufrufer entweder über eine Mitgliedschaft in der Rolle oder die ALTER-Berechtigung für die Rolle verfügen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
##### <a name="to-create-a-schema"></a>So erstellen Sie ein Schema  
  
1.  Erweitern Sie im Objekt-Explorer den Ordner **Datenbanken** .  
  
2.  Erweitern Sie die Datenbank, in der das neue Datenbankschema erstellt werden soll.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Sicherheit** , zeigen Sie auf **Neu**, und wählen Sie **Schema**aus.  
  
4.  Geben Sie im Dialogfeld **Schema - Neu** auf der Seite **Allgemein** im Feld **Schemaname** einen Namen für das neue Schema ein.  
  
5.  Geben Sie im Feld **Schemabesitzer** den Namen eines Datenbankbenutzers oder einer Rolle ein, der bzw. die über das Schema verfügen soll. Klicken Sie alternativ auf **Suchen** , um das Dialogfeld **Rollen und Benutzer suchen** zu öffnen.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

> [!NOTE]
> Es wird kein Dialogfeld angezeigt, wenn Sie mithilfe von SSMS ein Schema für eine **Azure SQL-Datenbank** oder **Azure SQL Data Warehouse** erstellen. Sie müssen die generierte T-SQL-Anweisung zum Erstellen eines Schemas ausführen.
  
### <a name="additional-options"></a>Zusätzliche Optionen  
 Das Dialogfeld **Schema > Neu** verfügt zudem über Optionen auf zwei zusätzlichen Seiten: **Berechtigungen** und **Erweiterte Eigenschaften**.  
  
-   Auf der Seite **Berechtigungen** werden alle möglichen sicherungsfähigen Elemente und die Berechtigungen für diese sicherungsfähigen Elemente aufgelistet, die für die Anmeldung gewährt werden können.  
  
-   Mithilfe der Seite **Erweiterte Eigenschaften** können Sie Datenbankbenutzern benutzerdefinierte Eigenschaften hinzufügen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-schema"></a>So erstellen Sie ein Schema  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Im folgenden Beispiel wird das Schema `Chains` erstellt, und anschließend die Tabelle `Sizes`.  
    ```sql  
    CREATE SCHEMA Chains;
    GO
    CREATE TABLE Chains.Sizes (ChainID int, width dec(10,2));
    ```

4.  Weitere Optionen können in einer einzelnen Anweisung durchgeführt werden. In folgendem Beispiel wird das Schema `Sprockets` erstellt, das im Besitz von Annik ist und die Tabelle `NineProngs` enthält. Die Anweisung erteilt Mandar die Berechtigung für `SELECT` und verweigert Prasanna die Berechtigung für `SELECT`.  

    ```sql  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
5. Führen Sie die folgende Anweisung aus, um die Schemas in dieser Datenbank anzuzeigen:

   ```sql
   SELECT * FROM sys.schemas;
   ```

 Weitere Informationen finden Sie unter [CREATE SCHEMA &#40;Transact-SQL&#41;](../../../t-sql/statements/create-schema-transact-sql.md).  
  
  
