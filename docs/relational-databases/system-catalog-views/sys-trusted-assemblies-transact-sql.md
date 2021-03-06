---
title: sys. trusted_assemblies (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: ''
author: VanMSFT
ms.author: vanto
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9682535c82f8a579259993e82560dfe6bc930f93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061362"
---
# <a name="systrusted_assemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Enthält eine Zeile für jede vertrauenswürdige Assembly für den Server.

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Spaltenname |Datentyp |BESCHREIBUNG |
|--- |--- |--- |
|hash |varbinary(8000) |SHA2_512 Hash des assemblyinhalts. |
|description |nvarchar(4000) |Optionale benutzerdefinierte Beschreibung der Assembly. Microsoft empfiehlt die Verwendung des kanonischen Namens, der den einfachen Namen, die Versionsnummer, die Kultur, den öffentlichen Schlüssel und die Architektur der Assembly codiert, die als vertrauenswürdig eingestuft wird. Durch diesen Wert wird die Assembly auf der Seite Common Language Runtime (CLR) eindeutig identifiziert, und Sie entspricht dem clr_name Wert in sys. Assemblys. |
|create_date |datetime2 |Datum, an dem die Assembly der Liste der vertrauenswürdigen Assemblys hinzugefügt wurde. |
|created_by |nvarchar(128) |Der Anmelde Name des Prinzipals, der die Assembly der Liste hinzugefügt hat. |
| | | |


## <a name="remarks"></a>Bemerkungen  

Verwenden Sie **müssen sp_add_trusted_assembly hinzufügen** und **sys. trusted_assemblies** hinzufügen oder Entfernen von `sys.trusted_assemblies`Assemblys hinzufügen.

## <a name="see-also"></a>Weitere Informationen  
  [sys. sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys. sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [Drop Assembly &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

