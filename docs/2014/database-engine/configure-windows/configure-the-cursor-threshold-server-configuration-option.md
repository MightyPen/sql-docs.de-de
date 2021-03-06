---
title: Konfigurieren der Serverkonfigurationsoption „Cursorschwellenwert“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cursor threshold option
ms.assetid: 189f2067-c6c4-48bd-9bd9-65f6b2021c12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a710ef8474ea0ce67d0b549febb3a9dd40aa36e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62811374"
---
# <a name="configure-the-cursor-threshold-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Cursorschwellenwert
  In diesem Thema wird beschrieben, wie die Serverkonfigurationsoption **Cursorschwellenwert** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]konfiguriert wird. Mit der Option **Cursorschwellenwert** können Sie die Anzahl der Zeilen im Cursorset angeben, bei der Cursor-Keysets asynchron generiert werden. Wenn Cursor ein Keyset für ein Resultset generieren, schätzt der Abfrageoptimierer die Anzahl der Zeilen, die für dieses Resultset zurückgegeben werden. Wenn der Abfrageoptimierer schätzt, dass die Anzahl der zurückgegebenen Zeilen über diesem Schwellenwert liegt, wird der Cursor asynchron generiert. Dadurch kann der Benutzer Zeilen aus dem Cursor abrufen, während der Cursor weiterhin aufgefüllt wird. Andernfalls wird der Cursor synchron generiert, und die Abfrage wartet, bis alle Zeilen zurückgegeben wurden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Cursorschwellenwert mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Cursorschwellenwert“](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt das asynchrone Generieren von keysetgesteuerten oder statischen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorn nicht. [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorvorgänge, z. B. OPEN oder FETCH, sind in Batches enthalten. Daher ist das asynchrone Generieren von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorn nicht erforderlich. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt weiterhin asynchrone keysetgesteuerte oder statische AP -Servercursor (Application Programming Interface), wobei Cursoroperationen des Typs „Open“ mit niedriger Latenz ein Problem darstellen. Dies ist auf Clientroundtrips zurückzuführen, die für jeden Cursorvorgang ausgeführt werden.  
  
-   Die Genauigkeit des Abfrageoptimierers beim Bestimmen der Anzahl der Zeilen in einem Keyset hängt davon ab, wie aktuell die Statistiken für die einzelnen Tabellen im Cursor sind.  
  
###  <a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Wenn Sie den **Cursorschwellenwert** auf -1 festlegen, werden alle Keysets synchron generiert, was für kleine Cursorsets vorteilhaft ist. Wenn Sie **Cursorschwellenwert** auf 0 festlegen, werden alle Cursor-Keysets asynchron generiert. Bei anderen Werten vergleicht der Abfrageoptimierer die Anzahl der erwarteten Zeilen im Cursorset und erstellt das Keyset asynchron, wenn die Anzahl der in **Cursorschwellenwert**festgelegten Zeilen überschritten wird. Sie sollten die Option **Cursorschwellenwert** nicht zu niedrig festlegen, da es besser ist, kleine Resultsets synchron zu erstellen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>So konfigurieren Sie die Option "Cursorschwellenwert"  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Geben Sie unter **Verschiedenes**für die Option **Cursorschwellenwert** den gewünschten Wert an.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-cursor-threshold-option"></a>So konfigurieren Sie die Option "Cursorschwellenwert"  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie Sie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) zum Festlegen der Option `cursor threshold` auf `0` verwenden, damit Cursor-Keysets asynchron generiert werden.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cursor threshold', 0 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option „Cursorschwellenwert“  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [@@CURSOR_ROWS &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-rows-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
