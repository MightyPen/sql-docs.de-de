---
title: Eintragen eines Zielservers bei einem Masterserver
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 936c40de1bebd463ad0213ebdfc99171a0fd91a2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75242390"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Eintragen eines Zielservers bei einem Masterserver
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In diesem Thema wird die Vorgehensweise zum Hinzufügen eines Zielservers zu einer Multiserververwaltungskonfiguration beschrieben. Führen Sie die folgenden Schritte auf dem Masterserver aus. Die Schritte können in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects (SMO) ausgeführt werden.  
  
Informationen zu den Auswirkungen des für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst verwendeten Windows-Kontos auf eine Multiserverumgebung finden Sie unter [Erstellen einer Multiserverumgebung](../../ssms/agent/create-a-multiserver-environment.md).  
  
Die vollständige SSL-Verschlüsselung (Secure Sockets Layer) und die Zertifikatüberprüfung sind für Verbindungen zwischen Masterservern und Zielservern standardmäßig aktiviert. Weitere Informationen finden Sie unter [Festlegen von Verschlüsselungsoptionen auf Zielservern](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>So tragen Sie einen Zielserver ein  
  
1.  Erweitern Sie im **Objekt-Explorer**einen Server, der als Masterserver konfiguriert ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserveradministration**, und klicken Sie dann auf **Zielserver hinzufügen**.  
  
3.  Schließen Sie den Zielservererstellungs-Assistenten ab, in dem Sie durch den Prozess geleitet werden.  
  
## <a name="TsqlProcedure"></a>Verwenden von Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>So tragen Sie einen Zielserver ein  
  
1.  Verwenden Sie die gespeicherte Prozedur **sp_msx_enlist** .  Weitere Informationen finden Sie unter [sp_msx_enlist (Transact-SQL)](https://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## <a name="see-also"></a>Weitere Informationen  
[Automatisierte Verwaltung in einem Unternehmen](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
