---
title: Ändern von Ansichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef528fb128c81de1d2be07196dfe2a20ceaebba4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68196394"
---
# <a name="modify-views"></a>Ändern von Sichten
  Nachdem eine Sicht definiert wurde, können Sie ihre Definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ändern, ohne die Sicht mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen und neu erstellen zu müssen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So ändern Sie eine Sicht mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Das Ändern einer Sicht hat keine Auswirkungen auf abhängige Objekte, z. B. gespeicherte Prozeduren oder Trigger, es sei denn, die Definition der Sicht wird so geändert, dass das abhängige Objekt nicht mehr gültig ist.  
  
-   Wird eine derzeit verwendete Sicht mithilfe von ALTER VIEW geändert, belegt [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Sicht mit einer exklusiven Schemasperre. Wenn die Sperre erteilt wird und keine aktiven Benutzer der Sicht vorhanden sind, löscht [!INCLUDE[ssDE](../../includes/ssde-md.md)] alle Kopien der Sicht aus dem Prozedurcache. Vorhandene Pläne, die auf die Sicht verweisen, bleiben im Cache, werden aber beim Aufrufen erneut kompiliert.  
  
-   ALTER VIEW kann auf indizierte Sichten angewendet werden; ALTER VIEW löscht jedoch vorbehaltlos alle Indizes in der Sicht.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Für die Ausführung von ALTER VIEW wird zumindest die ALTER-Berechtigung für OBJECT benötigt.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-modify-a-view"></a>So ändern Sie eine Sicht  
  
1.  Klicken Sie im **Objekt-Explorer**auf das Pluszeichen neben der Datenbank, in der sich die Sicht befindet, und klicken Sie dann auf das Pluszeichen neben dem Ordner **Sichten** .  
  
2.  Klicken Sie mit der rechten Maustaste auf die Sicht, die Sie ändern möchten, und klicken Sie anschließend auf **Entwurf**.  
  
3.  Nehmen Sie im Diagrammbereich des Abfrage-Designers Änderungen an der Sicht vor, indem Sie eine oder mehrere der folgenden Vorgehensweisen anwenden:  
  
    1.  Aktivieren oder deaktivieren Sie die Kontrollkästchen beliebiger Elemente, die Sie hinzufügen oder entfernen möchten.  
  
    2.  Klicken Sie mit der rechten Maustaste innerhalb des Diagrammbereichs, wählen Sie die Option **Tabelle hinzufügen...** , und wählen Sie im Dialogfeld **Tabelle hinzufügen** dann die weiteren Spalten aus, die Sie der Ansicht hinzufügen möchten.  
  
    3.  Klicken Sie mit der rechten Maustaste auf die Titelleiste der Tabelle, die Sie entfernen möchten, und wählen Sie die Option **Entfernen**.  
  
4.  Klicken Sie im Menü **Datei** auf **Speichern**_view name_.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-modify-a-view"></a>So ändern Sie eine Sicht  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im Beispiel wird zuerst eine Sicht erstellt, und anschließend wird die Sicht mithilfe von ALTER VIEW geändert. Der Sichtdefinition wird eine WHERE-Klausel hinzugefügt.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql).  
  
  
