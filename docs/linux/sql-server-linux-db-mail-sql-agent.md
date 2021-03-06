---
title: Datenbank-E-Mail und E-Mail-Warnungen mit dem SQL-Agent unter Linux
description: In diesem Artikel wird beschrieben, wie die Datenbank-E-Mail und E-Mail-Warnungen mit SQL Server für Linux verwendet werden.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: tbd
ms.openlocfilehash: 31f8931f6e0eddc67b2e58ae794631a9ae6555b7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68077451"
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>Datenbank-E-Mail und E-Mail-Warnungen mit dem SQL-Agent unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Die folgenden Schritte zeigen Ihnen, wie die Datenbank-E-Mail eingerichtet und mit dem SQL Server-Agent (**mssql-server-agent**) unter Linux verwendet wird. 

## <a name="1-enable-db-mail"></a>1. Aktivieren der Datenbank-E-Mail

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2. Erstellen eines neuen Kontos
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3. Erstellen eines Standardprofils

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. Hinzufügen des Kontos der Datenbank-E-Mail zu einem Datenbank-E-Mail-Profil
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5. Hinzufügen eines Kontos zu einem Profil 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6. Senden einer Test-E-Mail
> [!NOTE]
> Möglicherweise müssen Sie zu Ihrem E-Mail-Client wechseln und die Option „allow less secure clients to send mail“ (weniger sicheren Clients das Senden von E-Mails erlauben) aktivieren. Nicht alle Clients erkennen die Datenbank-E-Mail als E-Mail-Daemon.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Festlegen des Datenbank-E-Mail-Profils mithilfe der Umgebungsvariable „mssql-conf“
Sie können das Hilfsprogramm „mssql-conf“ oder die Umgebungsvariablen verwenden, um Ihr Datenbank-E-Mail-Profi zu registrieren. Nennen wir in diesem Fall unser Profil „default“ (Standard).

```bash
# via mssql-conf
sudo /opt/mssql/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. Einrichten eines Operators für SQLAgent-Auftragsbenachrichtigungen 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. Senden einer E-Mail, wenn der 'Agent Test Job' erfolgreich ist 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen dazu, wie der SQL Server-Agent verwendet wird, um Aufträge zu erstellen, zu planen und auszuführen, finden Sie unter [Erstellen und Ausführen von SQL Server-Agent-Aufträgen unter Linux](sql-server-linux-run-sql-server-agent-job.md).
