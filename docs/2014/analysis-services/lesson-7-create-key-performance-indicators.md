---
title: 'Lektion 8: Erstellen von Key Performance-Indikatoren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d9d3145583670fb849321bac5b57928caacfbc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078368"
---
# <a name="lesson-8-create-key-performance-indicators"></a>Lektion 8: Erstellen von Leistungskennzahlen
  In dieser Lektion erstellen Sie Leistungskennzahlen (Key Performance Indicators, KPIs). KPIs dienen zum Messen der Leistung eines Werts, der durch ein *basismeasure* definiert wird, anhand eines *Zielwerts* , der ebenfalls durch ein Measure oder einen absoluten Wert definiert wird. Mit KPIs können Geschäftsleuten in Berichterstellungsclientanwendungen Zusammenfassungen von Geschäftserfolgen schnell und einfach verstehen bzw. Trends erkennen. Weitere Informationen finden Sie unter [KPIs &#40;SSAS – tabellarisch&#41;](tabular-models/kpis-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der vorgegebenen Reihenfolge durchgeführt werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 7: Erstellen von Measures](lesson-6-create-measures.md).  
  
## <a name="create-key-performance-indicators"></a>Erstellen von Key Performance Indicators  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a>So erstellen Sie einen KPI zur Internetverkaufsleistung des aktuellen Quartals  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Internet Sales**.  
  
2.  Klicken Sie im Measureraster auf eine leere Zelle.  
  
3.  Geben Sie in der Bearbeitungsleiste über der Tabelle folgende Formel ein:  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
     Dieses Measure fungiert als Base-Measure für den KPI.  
  
4.  Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure **Internet Current Quarter Sales Performance** und anschließend auf **KPI erstellen**.  
  
     Das Dialogfeld **Key Performance Indicator** wird geöffnet.  
  
5.  Wählen Sie im Dialogfeld **Key Performance Indicator** unter **Zielwert definieren** die Option **Absoluter Wert** aus.  
  
6.  Geben `1.1`Sie im Feld **absoluter Wert den Wert** ein, und drücken Sie dann die EINGABETASTE.  
  
7.  Geben `1`Sie in `1.07` **Status Schwellenwerte definieren**im linken (unteren) schiebereglerfeld ein, und geben Sie dann im rechten (hohen) Schieberegler ein.  
  
8.  Wählen Sie unter **Symbolart auswählen** die Raute (rot), das Dreieck, (gelb) und den Kreis (grün) aus.  
  
    > [!TIP]  
    >  Achten Sie auf das erweiterbare Feld **Beschreibungen** unterhalb der verfügbaren Symbolarten. Sie können Typbeschreibungen eingeben, damit sich die verschiedenen KPI-Elemente in Clientanwendungen leichter identifizieren lassen.  
  
9. Klicken Sie auf **OK**, um den KPI fertigzustellen.  
  
     Achten Sie im Measureraster auf das Symbol neben dem Measure **Internet Current Quarter Sales Performance**. Dieses Symbol gibt an, dass dieses Measure der Basewert für einen KPI ist.  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a>So erstellen Sie einen KPI zur Internetumsatzleistung des aktuellen Quartals  
  
1.  Klicken Sie im Measureraster für die Tabelle **Internet Sales** auf eine leere Zelle.  
  
2.  Geben Sie in der Bearbeitungsleiste über der Tabelle folgende Formel ein:  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
3.  Klicken Sie im Measureraster mit der rechten Maustaste auf das Measure **Internet Current Quarter Margin Performance** und anschließend auf **KPI erstellen**.  
  
4.  Wählen Sie im Dialogfeld **Key Performance Indicator** unter **Zielwert definieren** die Option **Absoluter Wert** aus.  
  
5.  Geben `1.25`Sie im Feld **absoluter Wert den Wert** ein.  
  
6.  Verschieben Sie unter **Statusschwellenwerte definieren**den linken (unteren) Schieberegler, bis im Feld der Wert **0,8**angezeigt wird. Verschieben Sie anschließend den rechten (oberen) Schieberegler, bis im Feld **1,03**angezeigt wird.  
  
7.  Wählen Sie unter **Symbolart auswählen** die Raute (rot), das Dreieck, (gelb) und den Kreis (grün) aus, und klicken Sie anschließend auf **OK**.  
  
## <a name="next-step"></a>Nächster Schritt  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 9: Erstellen von Perspektiven](lesson-8-create-perspectives.md).  
  
  
