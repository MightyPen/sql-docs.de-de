---
title: Öffnen des Abfrage- und Sicht-Designers (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- opening View Designer
- View Designer, opening
- Query Designer [SQL Server], opening
- opening Query Designer
ms.assetid: b473f258-d53c-41c0-9ad9-528a2ff141f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1b729c5652258deb0780ec129592e1a0f14217c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63195050"
---
# <a name="open-the-query-and-view-designer-visual-database-tools"></a>Öffnen des Abfrage- und Sicht-Designers (Visual Database Tools)
  Der Abfrage- und Sicht-Designer wird automatisch geöffnet, wenn Sie die Definition einer Sicht öffnen, die Ergebnisse für eine Abfrage oder Sicht anzeigen bzw. eine Abfrage erstellen oder öffnen. Er besteht aus vier separaten Bereichen:  
  
-   Der Diagrammbereich liefert eine grafische Darstellung der Tabellen bzw. Tabellenwertobjekte, die Sie aus der Datenverbindung ausgewählt haben. Weiterhin werden alle Joinbeziehungen zwischen ihnen angezeigt.  
  
-   Im Kriterienbereich können Sie Abfrageoptionen angeben, d.h. welche Datenspalten angezeigt oder wie die Ergebnisse sortiert werden und welche Zeilen ausgewählt werden sollen. Hierzu geben Sie die gewünschten Optionen in einem Datenblatt ähnlich einer Kalkulationstabelle ein.  
  
-   Sie können den SQL-Bereich verwenden, um eine eigene SQL-Anweisung zu erstellen. Sie können auch den Kriterienbereich und den Diagrammbereich verwenden, um die Anweisung zu erstellen, wobei dadurch die SQL-Anweisungen im SQL-Bereich erstellt werden. Beim Erstellen einer Abfrage wird der SQL-Bereich automatisch aktualisiert und zur besseren Lesbarkeit neu formatiert.  
  
-   Im Ergebnisbereich werden die Ergebnisse der zuletzt ausgeführten SELECT-Abfrage angezeigt. (Die Ergebnisse anderer Abfragetypen werden in Meldungsfeldern angezeigt.)  
  
-   Diese Bereiche sind sowohl beim Verwenden von Abfragen als auch beim Verwenden von Sichten nützlich.  
  
-   Beim Öffnen einer Sicht oder Abfrage werden gleichzeitig einige oder alle Bereiche geöffnet. Welche Bereiche geöffnet werden, hängt von den Einstellungen im Dialogfeld **Optionen** und von dem Datenbankmanagementsystem ab, mit dem Sie verbunden sind. Standardmäßig werden alle vier Bereiche geöffnet.  
  
### <a name="to-open-the-query-and-view-designer-for-a-view"></a>So öffnen Sie den Abfrage- und Sicht-Designer für eine Sicht  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Sicht, die Sie öffnen möchten, und klicken Sie dann auf **Entwerfen** oder **Sicht öffnen**.  
  
     Wenn Sie **Entwerfen**auswählen, werden die Bereiche des Abfrage- und Sicht-Designers entsprechend den Einstellungen im Dialogfeld **Optionen** geöffnet. Wenn Sie **Sicht öffnen**auswählen, wird standardmäßig nur der Ergebnisbereich geöffnet.  
  
### <a name="to-open-the-query-and-view-designer-for-an-existing-query"></a>So öffnen Sie den Abfrage- und Sicht-Designer für eine vorhandene Abfrage  
  
1.  Erweitern Sie im Projektmappen-Explorer den Ordner **Abfragen** .  
  
2.  Doppelklicken Sie auf die Abfrage, die Sie öffnen möchten.  
  
3.  Markieren Sie die Abfrageanweisung(en), klicken Sie mit der rechten Maustaste auf den markierten Bereich, und klicken Sie auf **Abfrage in Editor entwerfen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Themen zur Vorgehensweise beim Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Tools im Abfrage- und Sicht-Designer &#40;Visual Database Tools&#41;](query-and-view-designer-tools-visual-database-tools.md)  
  
  
