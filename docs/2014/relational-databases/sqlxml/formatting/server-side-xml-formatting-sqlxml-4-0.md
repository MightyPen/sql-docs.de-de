---
title: Server seitige XML-Formatierung (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af44d854ba28e8e8ac3b1a4572bf9b222f20299b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012210"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Serverseitige XML-Formatierung (SQLXML 4.0)
  Dieses Thema enthält Informationen über das serverseitige Formatieren von XML-Dokumenten aus den Rowsets, die von Abfragen generiert werden, die in einer Datenbank in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt werden.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie XML-Dokumente in Datenbanktabellen speichern und aus Datenbanktabellen abrufen. Um ein XML-Dokument abzurufen, verwenden Sie die FOR XML-Abfrageerweiterung in einer SELECT-Abfrage.  
  
 Nehmen Sie beispielsweise an, eine Client Anwendung führt einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Befehl für aus, der [!INCLUDE[tsql](../../../includes/tsql-md.md)] aus der folgenden Abfrage besteht:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 Der Server führt die Abfrage in zwei Schritten aus. Zuerst führt der Server diese SELECT-Anweisung aus:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Dann wendet der Server die FOR XML-Transformation auf das generierte Rowset an. Der resultierende XML-Code wird dann an den Client als ein einspaltiges Rowset gesendet. In dieser Dokumentation wird dieser Prozess als serverseitige XML-Formatierung bezeichnet.  
  
 Auf der Serverseite können Sie die folgenden Modi mit einer FOR XML-Klausel angeben:  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 Weitere Informationen zur for XML-Klausel finden Sie unter [Erstellen von XML mithilfe von for XML](../../xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Architektur der Client seitigen und Server seitigen XML-Formatierung &#40;SQLXML 4,0&#41;](architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Client seitige XML-Formatierung &#40;SQLXML 4,0&#41;](client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md)  
  
  
