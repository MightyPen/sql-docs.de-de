---
title: Neuer Alias (Registerkarte Alias) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a64d4a3cc46a68a06367d51a3cf3511191c6232
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62912955"
---
# <a name="new-alias-alias-tab"></a>Neuer Alias (Registerkarte Alias)
  Bei einem Alias handelt es sich um einen alternativen Namen, der zum Herstellen einer Verbindung verwendet werden kann. In dem Alias eingeschlossen werden erforderliche Elemente einer Verbindungszeichenfolge. Diese Elemente werden mit einem vom Benutzer ausgewählten Namen offen gelegt. Verwenden Sie im Dialogfeld **Alias – Neu** die Seite **Alias** , um die Elemente der Verbindungszeichenfolge für einen Alias anzugeben. Informationen zum Ändern der Verbindungszeichenfolge eines vorhandenen Alias finden Sie unter [&#60;Alias&#62;-Eigenschaften &#40;Registerkarte „Alias“&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md).  
  
 Alle Werte im **Eigenschaften** -Raster müssen nicht vervollständigt werden. Gültige Kombinationen variieren abhängig vom ausgewählten Protokoll. Beispiele für gültige Kombinationen finden Sie in der folgenden Liste.  
  
 **Aliasname**  
 Der Name (Alias), der als Referenz auf diese Verbindung verwendet werden soll.  
  
 **Pipename** / **Port Nr** .  
 Zusätzliche Elemente der Verbindungszeichenfolge. Der Name dieses Dialogfelds unterscheidet sich je nach ausgewähltem Protokoll.  
  
 **Spezifische**  
 Das für die Verbindung verwendete Protokoll.  
  
 **Server**  
 Der Name [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Instanz, mit der eine Verbindung hergestellt wird.  
  
## <a name="when-to-use-an-alias"></a>Wann ein Alias verwendet werden sollte  
 Standardmäßig wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit einer lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des **Shared Memory** -Protokolls, sowie mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem anderen Computer mithilfe von **TCP/IP** oder **Named Pipes**hergestellt. Erstellen Sie einen Alias, wenn Sie TCP/IP oder Named Pipes verwenden und eine benutzerdefinierte Verbindungszeichenfolge zur Verfügung stellen oder einen anderen Namen als den Servernamen für die Verbindung verwenden möchten.  
  
### <a name="examples"></a>Beispiele  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauscht nicht wird am Standard-TCP/IP-Port 1433. Sie sollten deshalb eine Verbindungszeichenfolge mit einer anderen Portnummer zur Verfügung stellen.  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird an der standardmäßige Named Pipe nicht gelauscht. Sie möchten deshalb eine Verbindungszeichenfolge mit einem anderen Pipenamen zur Verfügung stellen.  
  
-   Eine Anwendung ist auf die Verbindung mit einer Datenbank auf dem Server `ACCT`festgelegt. Diese Datenbank wurde aber als Instanz `ACCT` auf einem Server mit dem Namen `CENTRAL`konsolidiert. Das Ändern der Anwendung ist nicht einfach. Erstellen Sie einen Alias mit dem Namen `ACCT`mit einer Verbindungszeichenfolge, die auf `CENTRAL\ACCT`zeigt.  
  
## <a name="creating-a-valid-connection-string"></a>Erstellen einer gültigen Verbindungszeichenfolge  
 In den folgenden Themen finden Sie Beschreibungen und Beispiele für gültige Kombinationen von Aliaseigenschaften:  
  
-   [Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-named-pipes.md)  
  
  
