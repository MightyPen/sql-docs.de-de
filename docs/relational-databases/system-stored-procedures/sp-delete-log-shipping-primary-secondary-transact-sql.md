---
title: sp_delete_log_shipping_primary_secondary (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_primary_secondary_TSQL
- sp_delete_log_shipping_primary_secondary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_primary_secondary
ms.assetid: d6f71a12-f7b1-4a1c-9639-a533b8287b0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8276a23224495b7bcc69721fd5317d0b2b87821a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68009167"
---
# <a name="sp_delete_log_shipping_primary_secondary-transact-sql"></a>sp_delete_log_shipping_primary_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt den Eintrag für eine sekundäre Datenbank auf dem primären Server.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_log_shipping_primary_secondary  
    [ @primary_database = ] 'primary_database',   
    [ @secondary_server = ] 'secondary_server',   
    [ @secondary_database = ] 'secondary_database'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @primary_database = ] 'primary_database'`Der Name der Datenbank auf dem primären Server. *primary_database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @secondary_server = ] 'secondary_server'`Der Name des sekundären Servers. *Secondary_server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @secondary_database = ] 'secondary_database'`Der Name der sekundären Datenbank. *secondary_database* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_delete_log_shipping_primary_secondary** muss von der **Master** -Datenbank auf dem primären Server ausgeführt werden. Mit dieser gespeicherten Prozedur wird der Eintrag für eine sekundäre Datenbank aus **log_shipping_primary_secondaries** auf dem primären Server entfernt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `sp_delete_log_shipping_primary_secondary` verwendet, um die sekundäre Datenbank `LogShipAdventureWorks` vom sekundären Server `FLATIRON` zu löschen.  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_secondary  
@primary_database = N'AdventureWorks'  
,@secondary_server = N'FLATIRON'  
,@secondary_database = N'LogShipAdventureWorks';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
