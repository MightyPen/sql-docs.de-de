---
title: Verwenden von Tupelfunktionen | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9a329c8786ce580469e4601709509ca8a2de73f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037979"
---
# <a name="using-tuple-functions"></a>Verwenden von Tupelfunktionen


  Eine Tupelfunktion ruft ein Tupel aus einer Menge oder dadurch ab, dass sie die Zeichenfolgendarstellung eines Tupels auflöst.  
  
 Tupelfunktionen sind, wie Elementfunktionen und Mengenfunktionen, wesentlich für das Aushandeln mehrdimensionaler Strukturen, die in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zu finden sind.  
  
 Es gibt drei Tupelfunktionen in MDX, [aktuelle &#40;MDX-&#41;](../mdx/current-mdx.md), [Element &#40;Tupel&#41; &#40;MDX-&#41;](../mdx/item-tuple-mdx.md) und-&#40;[MDX ](../mdx/strtotuple-mdx.md)-&#41;. Die folgende Beispielabfrage veranschaulicht, wie sie verwendet werden:  
  
 `WITH`  
  
 `//Creates a set of tuples consisting of Years and Countries`  
  
 `SET MyTuples AS  [Date].[Calendar Year].[Calendar Year].MEMBERS * [Customer].[Country].[Country].MEMBERS`  
  
 `//Returns a string representation of that set using the Current and Generate functions`  
  
 `MEMBER MEASURES.CURRENTDEMO AS GENERATE(MyTuples, TUPLETOSTR(MyTuples.CURRENT), ", ")`  
  
 `//Retrieves the fourth tuple from that set and displays it as a string`  
  
 `MEMBER MEASURES.ITEMDEMO AS TUPLETOSTR(MyTuples.ITEM(3))`  
  
 `//Creates a tuple consisting of the measure Internet Sales Amount and the country Australia from a string`  
  
 `MEMBER MEASURES.STRTOTUPLEDEMO AS STRTOTUPLE("([Measures].[Internet Sales Amount]" + ", [Customer].[Country].&[Australia])")`  
  
 `SELECT{MEASURES.CURRENTDEMO,MEASURES.ITEMDEMO,MEASURES.STRTOTUPLEDEMO} ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)   
 [Verwenden von Element Funktionen](../mdx/using-member-functions.md)   
 [Verwenden von Mengenfunktionen](../mdx/using-set-functions.md)  
  
  
