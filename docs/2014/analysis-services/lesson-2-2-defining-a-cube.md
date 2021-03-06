---
title: Definieren eines Cubes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8aa4ac2d-857f-4048-baa0-0f314e207cf6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 167121188939bcf82ed359ac3f8cf7e3aae47635
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079061"
---
# <a name="defining-a-cube"></a>Definieren eines Cubes
  Der Cube-Assistent unterstützt Sie beim Definieren der Measuregruppen und Dimensionen für einen Cube. In der folgenden Aufgabe verwenden Sie den Cube-Assistenten, um einen Cube zu erstellen.  
  
### <a name="to-define-a-cube-and-its-properties"></a>So definieren Sie einen Cube und seine Eigenschaften  
  
1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Cubes**, und klicken Sie dann auf **Neuer Cube**. Der Cube-Assistent wird angezeigt.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Cube-Assistenten** auf **Weiter**.  
  
3.  Überprüfen Sie, ob die Option **Vorhandene Tabellen verwenden** auf der Seite **Erstellungsmethode auswählen** ausgewählt ist, und klicken Sie anschließend auf **Weiter**.  
  
4.  Überprüfen Sie auf der Seite **Measuregruppentabellen auswählen** , ob die **Adventure Works DW 2012** -Datenquellensicht ausgewählt ist.  
  
5.  Klicken Sie auf **Vorschlagen** , damit der Cube-Assistent Tabellen zum Erstellen der Measuregruppen vorschlägt.  
  
     Der Assistent untersucht die Tabellen und schlägt **InternetSales** als Measuregruppentabelle vor. Measuregruppentabellen, die auch als Faktentabellen bezeichnet werden, enthalten die für Sie interessanten Measures wie die Anzahl von verkauften Einheiten.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Überprüfen Sie auf der Seite **Measures auswählen** die ausgewählten Measures in der Measuregruppe **Internetverkäufe** , und deaktivieren Sie anschließend die Kontrollkästchen für die folgenden Measures:  
  
    -   **Promotionschlüssel**  
  
    -   **Währungs Schlüssel**  
  
    -   **Sales Territory Key**  
  
    -   **Revisionsnummer**  
  
     Vom Assistenten werden standardmäßig als Measures alle numerischen Spalten in der Faktentabelle ausgewählt, die nicht mit Dimensionen verknüpft sind. Bei diesen vier Spalten handelt es sich allerdings nicht um tatsächliche Measures. Die ersten drei sind Schlüsselwerte, die die Faktentabelle mit Dimensionstabellen verknüpfen, die nicht in der anfänglichen Version dieses Cubes verwendet werden.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Stellen Sie auf der Seite **Vorhandene Dimensionen auswählen** sicher, dass die zuvor erstellte **Date** -Dimension ausgewählt ist, und klicken Sie auf **Weiter**.  
  
10. Auf der Seite **Neue Dimensionen auswählen** können Sie die neue Dimension auswählen, die erstellt werden soll. Überprüfen Sie dazu, ob die Kontrollkästchen **Customer**, **Geography**und **Product** aktiviert sind, und deaktivieren Sie das Kontrollkästchen **InternetSales** .  
  
11. Klicken Sie auf **Weiter**.  
  
12. Ändern Sie auf der Seite **Assistenten abschließen** den Namen des Cubes in `Analysis Services Tutorial`. Im Vorschaubereich können Sie die Measuregruppe **InternetSales** und ihre Measures sehen. Ihnen werden auch die Dimensionen **Date**, **Customer** und **Product** angezeigt.  
  
13. Klicken Sie auf **Fertig stellen**, um den Assistenten abzuschließen.  
  
     Im Projektmappen-Explorer im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Tutorialprojekt wird der Cube des [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Tutorials im Ordner **Cubes** angezeigt, und die Customer- und Product-Datenbankdimensionen werden im Ordner **Dimensionen** angezeigt. Zusätzlich wird auf der Registerkarte für die Cubestruktur in der Mitte der Entwicklungsumgebung der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube angezeigt.  
  
14. Ändern Sie auf der Symbolleiste der Registerkarte „Cubestruktur“ den Wert für den **Zoomfaktor** auf 50 %, damit Sie die Dimensionen und Faktentabellen im Cube besser sehen können. Beachten Sie, dass die Faktentabelle gelb ist und die Dimensionstabellen blau sind.  
  
15. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Hinzufügen von Attributen zu Dimensionen](lesson-2-3-adding-attributes-to-dimensions.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cubes in mehrdimensionalen Modellen](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Dimensionen in mehrdimensionalen Modellen](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
