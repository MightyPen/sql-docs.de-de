---
title: sp_dropdevice (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropdevice_TSQL
- sp_dropdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], deleting
- sp_dropdevice
ms.assetid: c8b07189-7c35-414b-acc1-45bd6e7e17c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 998794fd2e5fe5521587ebbb2a88c61c80cff39e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67927827"
---
# <a name="sp_dropdevice-transact-sql"></a>sp_dropdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht ein Daten Bank Gerät oder Sicherungsmedium aus einer Instanz von [!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)]und löscht den Eintrag aus **Master. dbo. sysdevices**.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropdevice [ @logicalname = ] 'device'   
    [ , [ @delfile = ] 'delfile' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @logicalname = ] 'device'`Der logische Name des Daten Bank Geräts oder Sicherungs Mediums, wie in **Master.dbo.sysdevices.Name**aufgeführt. *Device* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @delfile = ] 'delfile'`Gibt an, ob die physische Sicherungsmedien Datei gelöscht werden soll. *Delta File ist vom Datentyp* **varchar (7)**. Wenn die Datenträger Datei des physischen Sicherungs Mediums als **Delta**Datei angegeben wird, wird Sie gelöscht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropdevice** kann nicht innerhalb einer Transaktion verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **diskadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das `tapedump1`-Bandsicherungsmedium aus [!INCLUDE[ssDE](../../includes/ssde-md.md)] gelöscht.  
  
```  
EXEC sp_dropdevice 'tapedump1';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherungsmedien &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Löschen eines Sicherungs Mediums &#40;SQL Server&#41;](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpdevice &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdevice-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
