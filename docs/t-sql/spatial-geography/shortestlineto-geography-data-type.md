---
title: ShortestLineTo (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7844f1d38f5d2e6f36f971eb83d8961596483142
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68042609"
---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt eine **LineString** -Instanz mit zwei Punkten zurück, die den kürzesten Abstand zwischen den zwei **geography** -Instanzen darstellen. Die Länge der **LineString** -Instanz, die zurückgegeben wurde, entspricht dem Abstand zwischen den beiden **geography** -Instanzen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>Argumente  
 *geography_other*  
 Gibt die zweite **geography** -Instanz an, für die von der aufrufenden **geography** -Instanz versucht wird, den kürzesten Abstand zu bestimmen.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Die Methode gibt eine **LineString** -Instanz mit Endpunkten zurück, die auf den Rändern der beiden Instanzen von **geography** liegen, die verglichen werden und sich nicht überschneiden. Die Länge der **LineString** -Instanz, die zurückgegeben wurde, entspricht dem geringsten Abstand zwischen den beiden **geography** -Instanzen. Wenn sich die beiden Instanzen von **LineString** überschneiden, wird eine leere Instanz von **geography** zurückgegeben.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Aufrufen von ShortestLineTo() für sich nicht überschneidende Instanzen  
 In diesem Beispiel wird der geringste Abstand zwischen einer Instanz von `CircularString` und einer Instanz von `LineString` ermittelt, und die Instanz von `LineString` wird zurückgegeben, die die beiden Punkte verbindet:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. Aufrufen von ShortestLineTo() für sich überschneidende Instanzen  
 In diesem Beispiel wird eine leere Instanz von `LineString` zurückgegeben, da die sich die Instanz von `LineString` und die Instanz von `CircularString` überschneiden:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
``` 
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
