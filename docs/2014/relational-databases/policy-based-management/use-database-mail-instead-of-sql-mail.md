---
title: Verwenden von Datenbank-E-Mail anstelle von SQL Mail | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cfce3fb95ddae03525b7f63f09d109c6dc80b47c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676966"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>Verwenden von Datenbank-E-Mail anstelle von SQL Mail
  Diese Regel überprüft die sys.configurations-Katalogsicht, um zu bestimmen, ob die serverweite Konfigurationoption von SQL Mail XPs auf ON festgelegt ist.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 SQL Mail wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie zum Versenden von E-Mail-Nachrichten Datenbank-E-Mail.  
  
 SQL Mail wird prozessintern zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt. Wenn SQL Mail beendet wird, wird der Server ebenfalls beendet. Datenbank-E-Mail wird in einem separaten Prozess außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt. Sie ist skalierbar und benötigt keine Extended MAPI-Clientkomponenten auf dem Produktionsserver.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Datenbank-E-Mail](../database-mail/database-mail.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
