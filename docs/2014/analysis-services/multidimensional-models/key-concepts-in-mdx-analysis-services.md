---
title: Schlüsselkonzepte in MDX (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], about MDX
- dimensional modeling [MDX]
- MDX [Analysis Services], about MDX
- Multidimensional Expressions [Analysis Services], dimensional modeling
- MDX [Analysis Services], dimensional modeling
ms.assetid: 4797ddc8-6423-497a-9a43-81a1af7eb36c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b51c763987fdfe8bbaf08851094a5e6e6d267c36
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074861"
---
# <a name="key-concepts-in-mdx-analysis-services"></a>Schlüsselkonzepte in MDX (Analysis Services)
  Bevor Sie mehrdimensionale Daten mit MDX (Multidimensional Expressions) abfragen können oder MDX-Ausdrücke zur Verwendung in einem Cubes zu erstellen, sollten Sie sich mit Konzepten und Begriffen der Mehrdimensionalität vertraut machen.  
  
 Wir beginnen hierzu mit einem Beispiel für Datenzusammenfassung, das Sie bereits kennen, und stellen anschließend den Bezug zu MDX her. Hier sehen Sie eine in Excel erstellte pivotberechtigung, die mit Daten aus einem Analysis Services-Beispielcube aufgefüllt ist.  
  
 ![PivotTable mit Measures und Dimensionen als Legende](../media/ssas-keyconcepts-pivot1-measures-dimensions.png "PivotTable mit Measures und Dimensionen als Legende")  
  
## <a name="measures-and-dimensions"></a>Measures und Dimensionen  
 Ein Analysis Services-Cube besteht aus Measures, Dimensionen und Dimensionsattributen, die allesamt im PivotTable-Beispiel vorhanden sind.  
  
 **Measures** sind numerische Datenwerte in Zellen, die als Summe, Anzahl, Prozentsatz, min, Max oder Average aggregiert werden. Measure-Werte sind dynamisch und werden in Echtzeit anhand der Navigation und Interaktion von Benutzern in der PivotTable berechnet. In diesem Beispiel enthalten die Zellen steigende oder sinkende Reseller Sales-Werte, je nachdem, ob Sie die Achsen erweitern oder reduzieren. Sie können Reseller Sales-Werte summiert im jeweiligen Kontext für beliebige Kombinationen aus Datum (Jahr, Quartal, Monat oder Datum) und Vertriebsgebiet (Ländergruppe, Land, Region) abrufen. Measures werden auch als Fakten (in Data Warehouses) und berechnete Felder (in Tabellen- und Exceldatenmodellen) bezeichnet.  
  
 **Dimensionen** befinden sich auf den Spalten-und Zeilen Achsen einer PivotTables und stellen die Bedeutung hinter dem Measure dar. Dimensionen sind das Gegenstück zu Tabellen in relationalen Datenmodellen. Typische Beispiele für Dimensionen sind Zeit, Geografie, Produkte, Kunden, Mitarbeiter usw. Das aktuelle Beispiel enthält zwei Dimensionen: Vertriebsgebiet in den Zeilen und Datum in den Spalten. Sie könnten jedoch jederzeit weitere Dimensionen für Reseller Sales per Ziehen und Ablegen hinzufügen, um die Vertriebsleistung für diese Dimensionen anzuzeigen, wie z. B. Angebote oder Produkte. Die Möglichkeit zur Erkundung der Daten auf interessante Arten hängt von Ihren Dimensionen sowie von deren Verknüpfung mit Faktentabellen in Ihrer Datenquelle ab.  
  
 **Dimensions Attribute** sind benannte Elemente innerhalb einer Dimension, ähnlich wie Spalten in einer Tabelle. In diesem Fall bestehen die Dimensionsattribute für das Vertriebsgebiet aus Ländergruppen (Europa, Nordamerika, Pazifik), Ländern (Kanada, USA) und Regionen (Zentral, Nordost, Nordwest, Südost, Südwest).  
  
 Mit jedem Attribut ist eine Sammlung von Datenwerten oder Elementen verknüpft. Elemente des Ländergruppen-Attributs sind in diesem Fall Europa, Nordamerika und Pazifik. **Members** bezieht sich auf die tatsächlichen Datenwerte, die zu einem Attribut gehören.  
  
> [!NOTE]  
>  Ein Aspekt der Datenmodellierung ist die Formalisierung von Mustern und Beziehungen, die bereits zwischen den eigentlichen Daten existieren. Bei der Arbeit mit Daten, die eine natürliche Hierarchie haben, wie im aktuellen Beispiel Länder-Regionen-Städte, können Sie diese Beziehung durch die Erstellung einer **Attributbeziehung**formalisieren. Eine Attribut Beziehung ist eine 1: n-Beziehung zwischen Attributen, z. b. eine Beziehung zwischen einem Bundesland und einem Ort, in der ein Bundesstaat viele Städte hat, aber eine Stadt zu nur einem Bundesstaat gehört. Wenn Sie Attribut Beziehungen im Modell erstellen, beschleunigt dies die Abfrageleistung. Daher empfiehlt es sich, diese zu erstellen, wenn Sie von den Daten unterstützt werden. Sie können Attributbeziehungen auch im Dimensions-Designer in den SQL Server Data Tools erstellen. Siehe [Define Attribute Relationships](attribute-relationships-define.md).  
  
 Modell-Metadaten werden in Excel in der Feldliste der PivotTable angezeigt.  Vergleichen Sie die obige PivotTable mit der folgenden Feldliste. Beachten Sie, dass die Feldliste Vertriebsgebiet, Gruppe, Land, Region (Metadaten) enthält, und die PivotTable dagegen nur die Elemente (Datenwerte). Wenn Sie die Symbole kennen, können Sie die Teile von mehrdimensionalen Modellen schnell und einfach einer PivotTable in Excel zuordnen.  
  
 ![PivotTables-Feldliste](../media/ssas-keyconcepts-ptfieldlist.png "PivotTables-Feldliste")  
  
## <a name="attribute-hierarchies"></a>Attributhierarchien  
 Sie wissen beinahe intuitiv, welche Werte in einer PivotTable steigen oder fallen, wenn Sie die Werte auf den Achsen erweitern und reduzieren. Warum ist dies so? Die Antwort liegt in den Attributhierarchien.  
  
 Reduzieren Sie alle Achsenwerte und sehen Sie sich die Gesamtsummen der einzelnen Ländergruppen und Kalenderjahre an. Dieser Wert wird vom sogenannten **(Alle-) Element** innerhalb einer Hierarchie abgeleitet. Das (Alle)-Element ist der berechnete Wert aller Elemente in einer Attributhierarchie .  
  
-   Das (Alle)-Element für alle Ländergruppen und Daten kombiniert ist $80.450.596,98  
  
-   Das (Alle)-Element für CY2008 ist $16,038.062,60  
  
-   Das (Alle)-Element für Pazifik ist $1,594,335.38  
  
 Diese Art von Aggregationen werden vorberechnet und gespeichert, was einen Teil zur schnellen Abfrageleistung von Analysis Services beiträgt.  
  
 ![PivotTable mit Alle-Element als Legende](../media/ssas-keyconcepts-pivot2-allmember.png "PivotTable mit Alle-Element als Legende")  
  
 Erweitern Sie die Hierarchie, um bis zur niedrigsten Ebene vorzudringen. Dieses Element wird als **Blattelement**bezeichnet. Ein Blattelement ist ein Element einer Hierarchie, das keine untergeordneten Elemente besitzt. In diesem Beispiel ist Australien das Blattelement.  
  
 ![PivotTable mit Blattelement als Legende](../media/ssas-keyconcepts-pivot3-leafparent.PNG "PivotTable mit Blattelement als Legende")  
  
 Alle übergeordneten Elemente nennt man einfach **übergeordnetes Element**. Pazifik ist das übergeordnete Element von Australien.  
  
 **Komponenten einer Attributhierarchie**  
  
 All diese Konzepte zusammen ergeben das Konzept einer **Attributhierarchie**. Eine Attributhierarchie ist eine Hierarchie von Attributelementenmit den folgenden Ebenen:  
  
-   Eine Blattebene, die die verschiedenen Attributelemente enthält. Die Elemente der Blattebene werden auch als **Blattelemente**bezeichnet.  
  
-   Zwischenebenen, wenn es sich bei der Attributhierarchie um eine Über-/Unterordnungshierarchie handelt (mehr dazu später).  
  
-   Ein (Alle)-Element, das die aggregierten Werte aller untergeordneten Attribute enthält. Optional können Sie die (alle)-Ebene ausblenden oder deaktivieren, wenn Sie für die Daten keinen Sinn macht. Obwohl der Produkt Code numerisch ist, wäre es nicht sinnvoll, Summen oder Mittelwerte zu addieren oder anderweitig zu aggregieren.  
  
> [!NOTE]  
>  BI-Entwickler verwenden oft Eigenschaften in der Attributhierarchie, um ein bestimmtes Verhalten in Clientanwendungen zu erreichen oder um Leistungsvorzüge umzusetzen. Beispielsweise würden Sie attributehierarchyaktivierte = false für Attribute festlegen, für die das (alle)-Element keinen Sinn macht. Alternativ können Sie das (Alle)-Element einfach ausblenden. In diesem Fall würden Sie AttributeHierarchyVisible=False setzen. Weitere Details zu Eigenschaften finden Sie unter [Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) .  
  
## <a name="navigation-hierarchies"></a>Navigationshierarchien  
 In der PivotTable (zumindest in diesem Beispiel) werden Zeilen- und Spaltenachsen erweitert, um niedrigere Ebenen von Attributen anzuzeigen. Sie können Navigationshierarchien in einem Modell erstellen, um einen erweiterbaren Baum zu erhalten.  Im AdventureWorks-Beispielmodell hat die Vertriebsgebiet-Dimension eine Hierarchie mit mehreren Ebenen von Ländergruppe über Land zu Region.  
  
 Hierarchien werden also verwendet, um einen Navigationspfad in einer PivotTable oder anderen Objekten für die Datenzusammenfassung anzugeben. Es gibt zwei grundlegende Typen von Hierarchien: ausgeglichene und unausgeglichene Hierarchien.  
  
 **Ausgeglichene Hierarchien**  
  
|||  
|-|-|  
|![PivotTable mit ausgeglichener Hierarchie als Legende](../media/ssas-keyconcepts-pivot4-balancedhierarchy.PNG "PivotTable mit ausgeglichener Hierarchie als Legende")|Eine **ausgeglichene Hierarchie** ist eine Hierarchie, in der zwischen der obersten Ebene und jedem Blattelement die gleiche Anzahl von Ebenen liegen.<br /><br /> Eine **natürliche Hierarchie** entsteht natürlich aus den zugrunde liegenden Daten. Typische Beispiele sind Land-Region-Stadt, Jahr-Monat-Tag oder Kategorie-Unterkategorie-Modell. In diesen Fällen wird jede untergeordnete Ebene auf absehbare Weise von der vorherigen Ebene abgeleitet.<br /><br /> Mehrdimensionale Modelle enthalten hauptsächlich ausgeglichene Hierarchien, von denen viele außerdem auch natürliche Hierarchien sind.<br /><br /> Ein weiterer Modellierungsbegriff ist `user-defined hierarchy`, der oft als Kontrast zu Attributhierarchien verwendet werden. Dies bezeichnet alle vom BI-Entwickler erstellten Hierarchien im Gegensatz zu den automatisch von Analysis Services bei der Defintion von Attributen erstellten Attributhierarchien.|  
  
 **Unausgeglichene Hierarchien**  
  
|||  
|-|-|  
|![PivotTable mit unregelmäßiger Hierarchie als Legende](../media/ssas-keyconcepts-pivot15-raggedhierarchy.PNG "PivotTable mit unregelmäßiger Hierarchie als Legende")|Eine **unregelmäßige Hierarchie** oder **unausgeglichene Hierarchie** ist eine Hierarchie, in der zwischen der obersten Ebene und den Blattelementen unterschiedlich viele Ebenen liegen. Auch hier handelt es sich um eine Hierarchie, die vom BI-Entwickler erstellt wird, aber in diesem Fall gibt es Lücken in den Daten.<br /><br /> Im AdventureWorks-Beispielmodell enthält das Vertriebsgebiet eine unregelmäßige Hierarchie, da in den USA eine zusätzliche Ebene existiert (Regionen), die für die anderen Länder in diesem Beispiel nicht gilt.<br /><br /> Unregelmäßige Hierarchien sind eine Herausforderung für BI-Entwickler, wenn die Clientanwendung diese nicht auf elegante Art verarbeiten kann. Im Analysis Services-Modell können Sie eine **Über-/Unterordnungshierarchie** erstellen, die eine Beziehung zwischen mehreren Datenebenen explizit definiert und somit Mehrdeutigkeiten bzgl. der Abfolge der Ebenen ausräumt. Siehe [Parent-Child Hierarchy](parent-child-dimension.md) .|  
  
## <a name="key-attributes"></a>Schlüsselattribute  
 Modelle sind Sammlungen miteinander verwandter Objekte, deren Zuordnungen mit Schlüsseln und Indizes verwaltet werden. Analysis Services-Modelle funktionieren auf dieselbe Weise. Für jede Dimension (Äquivalent zu Tabellen im relationalen Modell) existiert ein Schlüsselattribut. Das **Schlüsselattribut** wird in Fremdschlüssel-Beziehungen zur Faktentabelle (Measuregruppe) verwendet. Alle nicht-Schlüsselattribute in der Dimension werden (direkt oder indirekt) mit dem Schlüsselattribut verknüpft.  
  
 Das Schlüsselattribut ist oft, jedoch nicht immer, gleichzeitig auch das **Granularitätsattribut**. Granularität bezieht sich auf die Detail- oder Genauigkeitsebene der Daten. Ein schnelles Beispiel hilft auch hier beim besseren Verständnis. Berücksichtigen Sie Datumswerte: Für die täglichen Verkäufe brauchen Sie Datumswerte bis zum Tag. Für Kontingente reichen möglicherweise Quartalsangaben, aber wenn Ihre Analysedaten aus Rennergebnissen von Sportereignissen bestehen, benötigen Sie unter Umständen sogar Millisekunden. Die Genauigkeitsebene Ihrer Datenwerte nennt man auch die Körnung.  
  
 Währung ist ein weiteres Beispiel: eine Finanzanwendung könnte monetäre Werte an viele Dezimalstellen verfolgen, während der fragetreiser Ihrer lokalen Schule möglicherweise nur Werte für den nächstgelegenen Dollar Wert benötigt. Das Konzept der Körnung ist wichtig, um die Speicherung unnötiger Daten zu vermeiden. Indem Sie Millisekunden von einem Zeitstempel oder Cents von einem Verkaufsbetrag abschneiden, können Sie Speicherungs- und Verarbeitungszeit sparen, wenn der jeweilige Detailgrad für Ihre Analyse nicht relevant ist.  
  
 Sie können das Granularitätsattribut in der Registerkarte Dimensionsverwendung im Cube-Designer in den SQL Server Data Tools einstellen. Im AdventureWorks-Beispielmodell ist das Schlüsselattribut der Datums-Dimension der Datums-Schlüssel. Für Verkaufsaufträge ist das Granularitätsattribut gleich dem Schlüsselattribut. Für Vertriebsziele wird die Granularität vierteljährlich verwendet, und das Granularitätsattribut wird entsprechend auf Kalenderquartal gesetzt.  
  
 ![Modell zur Anzeige des Granularitätsattributs](../media/ssas-keyconcepts-granularityattrib.png "Modell zur Anzeige des Granularitätsattributs")  
  
> [!NOTE]  
>  Wenn Granularitätsattribut und Schlüsselattribut unterschiedlich sind, müssen alle Nichtschlüsselattribute direkt oder indirekt mit dem Granularitätsattribut verlinkt sein. Innerhalb eines Cubes definiert das Granularitätsattribut die Granularität einer Dimension.  
  
## <a name="query-scope-cube-space"></a>Abfragebereich (Cuberaum)  
 Der Bereich einer Abfrage gibt die Grenzen für die auszuwählenden Daten an. Der Bereich kann vom gesamten Cube (Cubes sind die größten Abfrageobjekte) zu einer einzelnen Zelle reichen.  
  
 Der **Cuberaum** ist das Produkt der Elemente der Attribut Hierarchien eines Cubes mit den Measures des Cubes.  
  
 Der **Teilcube** ist eine Teilmenge eines Cubes, der eine gefilterte Ansicht des Cubes darstellt. Teilcubes können mithilfe von SCOPE-Anweisungen in einem MDX-Berechnungsskript oder mithilfe untergeordneter SELECT-Klauseln in einer MDX-Abfrage oder als ein Sitzungscube definiert werden.  
  
 **Cell** bezieht sich auf den Raum an der Schnittmenge eines Members des Measures Dimensions Elements und eines Elements aus jeder Attribut Hierarchie in einem Cube.  
  
## <a name="other-modeling-terms"></a>Weitere Modellierungsbegriffe  
 Dieser Abschnitt stellt eine Sammlung von Konzepten und Begriffen dar, die nicht problemlos in andere Abschnitte passen, aber Sie müssen noch wissen.  
  
 **Berechnetes** Element ist ein Dimensions Element, das zum Abfrage Zeitpunkt definiert und berechnet wird. Ein berechnetes Element kann in einer Benutzerabfrage oder in einem MDX-Berechnungsskript definiert und auf dem Server gespeichert werden. Ein berechnetes Element entspricht Zeilen in der Dimensionstabelle der Dimension, in der diese definiert sind.  
  
 Die unter **schiedliche Anzahl** ist ein spezieller Typ von Measure, der für Datenelemente verwendet wird, die nur einmal gezählt werden sollen. Das AdventureWorks-Beispielmodell enthält Distinct Count Measures für Internetbestellungen, Wiederverkäuferbestellungen und Verkaufsaufträge.  
  
 Bei **Measure-Gruppen** handelt es sich um eine Sammlung von einem oder mehreren Measures. Diese Gruppen sind normalerweise benutzerdefiniert und werden zum Gruppieren verwandter Measures verwendet. Distinct Count Measures sind eine Ausnahme. Diese Measures sind immer Teil einer speziellen Measuregruppe, die nur distinct Measures enthält. Die Measure-Gruppe wird in der PivotTables-Beispiel Abbildung nicht angezeigt, Sie wird jedoch in einer PivotTables-Feldliste als benannte Auflistung von Measures angezeigt.  
  
 Die **Measures-Dimension** ist die Dimension, die alle Measures in einem Cube enthält. Sie ist nicht in einem mehrdimensionalen Modell verfügbar, das Sie in SQL Server Data Tools erstellen, aber es ist eben identisch. Da diese Dimension Measures enthält, werden alle Elemente einer Measuredimension normalerweise aggregiert (typischerweise als Summe oder Anzahl).  
  
 **Daten Bank Dimensionen und Cubedimensionen**. In Modellen können Sie eigenständige Dimensionen definieren, die anschließend in einer beliebigen Anzahl von Cubes im gleichen Modell integriert werden. Wenn Sie einem Cube eine Dimension hinzufügen, wird diese als Cubedimension bezeichnet. Allein innerhalb eines Projekts als eigenständiges Element in Objekt-Explorer wird es als Daten Bank Dimension bezeichnet. Warum die Unterscheidung? Da Sie Eigenschaften der Dimensionen unabhängig voneinander setzen können. In der Produktdokumentation werden beide Begriffe verwendet, damit Sie verstehen, was Sie bedeuten.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie kennen nun die wichtigsten Konzepte und Begriffe und können mit diesen zusätzlichen Themen fortfahren, in denen grundlegende Konzepte von Analysis Services weiter erläutert werden:  
  
-   [Die grundlegende MDX-Abfrage &#40;MDX-&#41;](mdx/mdx-query-the-basic-query.md)  
  
-   [Das grundlegende MDX-Skript &#40;MDX-&#41;](mdx/the-basic-mdx-script-mdx.md)  
  
-   [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](../multidimensional-modeling-adventure-works-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cube-Bereich](mdx/cube-space.md)   
 [Tupel](mdx/tuples.md)   
 [Autoexists](mdx/autoexists.md)   
 [Arbeiten mit Membern, Tupeln und Mengen &#40;MDX-&#41;](mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Visuelle Gesamtsummen und nicht visuelle Gesamtwerte](mdx/visual-totals-and-non-visual-totals.md)   
 [Grundlagen der MDX-Abfrage &#40;Analysis Services&#41;](mdx/mdx-query-fundamentals-analysis-services.md)   
 [Grundlagen der MDX-Skripterstellung &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [MDX-Sprachreferenz &#40;MDX-&#41;](/sql/mdx/mdx-language-reference-mdx)   
 [Mehrdimensionale Ausdrücke &#40;MDX-&#41; Referenz](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
