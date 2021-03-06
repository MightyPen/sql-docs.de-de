---
title: Mining Struktur Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], columns
- data sources [Analysis Services], mining structure columns
- columns [data mining], mining structure columns
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c843a74b831315c98deda9a9d6fb0c3a463bc5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083404"
---
# <a name="mining-structure-columns"></a>Miningstrukturspalten
  Sie definieren die Spalten in einer Miningstruktur, wenn Sie die Miningstruktur erstellen. Wählen Sie hierzu die Spalten mit externen Daten aus, und geben Sie dann an, wie die Daten für die Modellierung verwendet werden sollen. Daher sind Miningstrukturspalten mehr als nur Kopien der Daten aus einer Datenquelle. Sie definieren, wie die Daten aus der Quelle vom Miningmodell verwendet werden. Sie können Eigenschaften zuweisen, die bestimmen, wie die Daten diskretisiert werden, und die beschreiben, wie die Datenwerte verteilt sind.  
  
 Miningstrukturspalten sind so entworfen, dass sie flexibel und erweiterbar sind, da jeder Algorithmus, den Sie zum Erstellen eines Miningmodells verwenden, verschiedene Spalten aus der Struktur verwenden kann, um die Daten zu interpretieren. Anstatt einen Satz Daten für jedes Modell zu nutzen, können Sie eine einzelne Miningstruktur und die darin enthaltenen Spalten verwenden, um die Daten für jedes Modell anzupassen.  
  
## <a name="defining-mining-structure-columns"></a>Definieren von Miningstrukturspalten  
 Die grundlegenden Daten- und Inhaltstypen, die Strukturspalten definieren, werden aus der Datenquelle abgeleitet, mit der Sie die Struktur erstellen. Sie können diese Einstellungen innerhalb der Miningstruktur ändern und darüber hinaus auch Modellierungsflags und die Verteilung für kontinuierliche Spalten festlegen.  
  
 Die Definition einer Miningstrukturspalte muss die folgenden Informationen enthalten:  
  
-   **ID**: der eindeutige Name der Spalte, der häufig dem Namen entspricht. Dies kann nicht geändert werden, nachdem Sie die Miningstruktur erstellt haben, wohingegen der Name geändert werden kann.  
  
-   **Name**: ein Name oder Alias für die Spalte.  
  
-   **Content**: eine Enumeration, die beschreibt, ob die Daten diskret oder kontinuierlich sind.  
  
-   **Type**: eine Enumeration, die den allgemeinen Datentyp angibt.  
  
-   **Distribution**: eine Enumeration, die die erwartete Verteilung der Werte beschreibt. Eine Verteilung liegt vor, wenn die Spalte kontinuierlich ist.  
  
-   **Modellierungsflags**: eine Enumeration, die angibt, wie fehlende Werte behandelt werden usw. Modellierungsflags können auch im Miningmodell definiert werden, aber die Modellflags unterscheiden sich von den für Strukturspalten verwendeten Flags.  
  
-   **Bindungen**: Eigenschaften, die die Quelldaten angeben.  
  
 Algorithmen von Drittanbietern können möglicherweise benutzerdefinierte Eigenschaften enthalten, die für die Miningstrukturspalte definiert werden können.  
  
 Weitere Informationen zur Data Mining-Struktur und zum Data Mining-Modell finden Sie unter [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md).  
  
## <a name="related-content"></a>Verwandte Inhalte  
 In den folgenden Themen finden Sie weitere Informationen zur Definition und Verwendung von Miningstrukturspalten.  
  
|Thema|Links|  
|-----------|-----------|  
|Beschreibt die Datentypen, mit der Sie eine Miningstrukturspalte definieren können.|[Datentypen &#40;Data Mining-&#41;](data-types-data-mining.md)|  
|Beschreibt die Inhaltstypen, die für jeden Datentyp in einer Miningstrukturspalte verfügbar sind. Inhaltstypen sind vom Datentyp abhängig. Der Inhaltstyp wird auf Modellebene zugewiesen und bestimmt, wie die Spaltendaten vom Modell verwendet werden.|[Inhaltstypen &#40;Data Mining-&#41;](content-types-data-mining.md)|  
|Führt das Konzept geschachtelter Tabellen ein und erklärt, wie geschachtelte Tabellen der Datenquelle als Miningstrukturspalten hinzugefügt werden können.|[Klassifizierte Spalten &#40;Data Mining-&#41;](classified-columns-data-mining.md)|  
|Nennt und erklärt die Verteilungseigenschaften, die Sie für eine Miningstrukturspalte festlegen können, um die erwartete Verteilung der Werte in der Spalte anzugeben.|[Spalten Verteilungen &#40;Data Mining-&#41;](column-distributions-data-mining.md)|  
|Erklärt das Konzept der Diskretisierung (manchmal auch als *Klasseneinteilung* bezeichnet) und beschreibt die Methoden, die Analysis Services zum Diskretisieren von kontinuierlichen numerischen Daten bereitstellt.|[Diskretisierungsmethoden &#40;Data Mining-&#41;](discretization-methods-data-mining.md)|  
|Beschreibt die Modellierungsflags, mit denen Sie für eine Miningstrukturspalte festlegen können.|[Modellierungsflags &#40;Data Mining-&#41;](modeling-flags-data-mining.md)|  
|Beschreibt klassifizierte Spalten, bei denen es sich um einen speziellen Spaltentyp handelt, mit dem Sie eine Miningstrukturspalte mit einer anderen verbinden können.|[Klassifizierte Spalten &#40;Data Mining-&#41;](classified-columns-data-mining.md)|  
|Erfahren Sie, wie Sie Miningstrukturspalten hinzufügen und ändern.|[Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mining Strukturen &#40;Analysis Services Data Mining-&#41;](mining-structures-analysis-services-data-mining.md)   
 [Miningmodellspalten](mining-model-columns.md)  
  
  
