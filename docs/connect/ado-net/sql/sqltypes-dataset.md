---
title: SqlTypes und das Dataset
description: Beschreibt die Typunterstützung für SqlTypes im DataSet
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: a7ef43ca6afa243e313e8e38bdd05d929161e71f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75233792"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes und das Dataset

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Mit ADO.NET 2.0 wurde durch den Namespace <xref:System.Data.SqlTypes> erweiterte Typunterstützung für das `DataSet` eingeführt. Die Typen in <xref:System.Data.SqlTypes> stellen Datentypen mit derselben Semantik und Präzision wie die Datentypen in einer SQL Server-Datenbank bereit. Für jeden Datentyp in <xref:System.Data.SqlTypes> gibt es einen äquivalenten Datentyp in SQL Server mit derselben zugrunde liegenden Datendarstellung.  
  
Wenn Sie <xref:System.Data.SqlTypes> direkt in einem <xref:System.Data.DataSet> verwenden, profitieren Sie von einigen Vorteilen bei der Arbeit mit SQL Server-Datentypen. <xref:System.Data.SqlTypes> unterstützt die gleiche Semantik wie native SQL Server-Datentypen. Wenn Sie einen <xref:System.Data.SqlTypes>-Namespace in der Definition einer <xref:System.Data.DataColumn>-Klasse angeben, ist dies präziser als die Konvertierung von dezimalen oder numerische Datentypen in einen CLR-Datentyp (Common Language Runtime).  

Im folgenden Beispiel wird ein <xref:System.Data.DataTable>-Objekt erstellt. Dabei werden explizit die <xref:System.Data.DataColumn>-Datentypen definiert, wobei anstelle von CLR-Typen <xref:System.Data.SqlTypes> verwendet werden. Der Code füllt die <xref:System.Data.DataTable> mit Daten aus der Sales.SalesOrderDetail-Tabelle in der SQL Server-AdventureWorks-Datenbank. Die im Konsolenfenster angezeigte Ausgabe enthält die Datentypen der einzelnen Spalten und die von SQL Server abgerufenen Werte.  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
