---
title: Polygon | Microsoft-Dokumentation
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 15a9ea69771699cf2b845d8018dfad1d1af511d5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014083"
---
# <a name="polygon"></a>Polygon
  Ein `Polygon` ist eine zweidimensionale Fläche, die als Sequenz von Punkten gespeichert wird, die einen äußeren Begrenzungsring und null oder mehrere innere Ringe definieren.  
  
## <a name="polygon-instances"></a>Polygon-Instanzen  
 Eine `Polygon`-Instanz kann aus einem Ring gebildet werden, der wenigstens drei unterschiedliche Punkte besitzt. Eine `Polygon`-Instanz kann auch leer sein.  
  
 Der äußere und eventuelle innere Ring einer `Polygon`-Instanz definieren die Begrenzung. Der Raum innerhalb der Ringe definiert das Innere des `Polygon`s.  
  
 Die nachfolgende Abbildung enthält Beispiele für `Polygon`-Instanzen.  
  
 ![Beispiele für Polygon-geometry-Instanzen](../../database-engine/media/polygon.gif "Beispiele von Polygon-Geometrieinstanzen")  
  
 Folgendes wird dargestellt:  
  
1.  Abbildung 1 zeigt eine `Polygon`-Instanz, deren Begrenzung von einem äußeren Ring definiert wird.  
  
2.  Abbildung 2 zeigt eine `Polygon`-Instanz, deren Begrenzung von einem äußeren Ring und zwei inneren Ringen definiert wird. Der Bereich zwischen den inneren Ringen ist Teil des äußeren Rings der `Polygon`-Instanz.  
  
3.  Abbildung 3 ist eine gültige `Polygon`-Instanz, da sich seine inneren Ringe an einem einzelnen Tangentialpunkt schneiden.  
  
### <a name="accepted-instances"></a>Akzeptierte Instanzen  
 Akzeptierte `Polygon`-Instanzen sind Instanzen, die in einer `geometry`-Variablen oder einer `geography`-Variablen gespeichert werden können, ohne dass eine Ausnahme ausgelöst wird. Bei den folgenden `Polygon`-Instanzen handelt es sich um akzeptierte Instanzen:  
  
-   Eine leere `Polygon`-Instanz  
  
-   Eine `Polygon`-Instanz, die einen akzeptablen äußeren Ring und null oder mehr akzeptable innere Ringe aufweist  
  
 Die folgenden Kriterien müssen erfüllt sein, damit ein Ring akzeptabel ist.  
  
-   Die `LineString`-Instanz muss akzeptiert sein.  
  
-   Die `LineString`-Instanz muss über mindestens vier Punkte verfügen.  
  
-   Der Anfangspunkt und der Endpunkt der `LineString`-Instanz müssen identisch sein.  
  
 Im folgenden Beispiel werden akzeptierte `Polygon`-Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'POLYGON EMPTY';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';  
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';  
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';  
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
```  
  
 Wie `@g4` und `@g5` zeigen, ist es möglich, dass eine akzeptierte `Polygon`-Instanz keine gültige `Polygon`-Instanz ist. 
  `@g5` zeigt auch, dass eine Polygon-Instanz nur einen Ring mit vier beliebigen Punkten enthalten muss, um akzeptiert zu werden.  
  
 In den folgenden Beispielen wird eine `System.FormatException` ausgelöst, da die `Polygon`-Instanzen nicht akzeptiert werden.  
  
```  
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';  
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';  
```  
  
 
  `@g1` wird nicht akzeptiert, da die `LineString`-Instanz für den äußeren Ring nicht genug Punkte enthält. 
  `@g2` wird nicht akzeptiert, da die `LineString`-Instanz des Ausgangspunkts des äußeren Rings nicht dem Endpunkt entspricht. Im folgenden Beispiel ist ein akzeptabler äußerer Ring enthalten, der innere Ring hingegen ist nicht akzeptabel. Dadurch wird auch eine `System.FormatException`ausgelöst.  
  
```  
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';  
```  
  
### <a name="valid-instances"></a>Gültige Instanzen  
 Die inneren Ringe eines `Polygon`s können sich selbst und einander an einzelnen Tangentialpunkten berühren; überkreuzen sich die inneren Ringe eines `Polygon`s jedoch, ist die Instanz ungültig.  
  
 Im folgenden Beispiel werden gültige `Polygon`-Instanzen veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 
  `@g3` ist gültig, da die zwei inneren Ringe einen einzigen Punkt berühren und einander nicht schneiden. Im folgenden Beispiel werden `Polygon` -Instanzen veranschaulicht, die nicht gültig sind.  
  
```  
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';  
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';  
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';  
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';  
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';  
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();  
```  
  
 
  `@g1` ist ungültig, da der innere Ring den äußeren Ring an zwei Stellen berührt. 
  `@g2` ist ungültig, da der zweite innere Ring im Inneren des ersten inneren Rings liegt. 
  `@g3` ist ungültig, da sich die zwei inneren Ringe an mehreren aufeinander folgenden Punkten berühren. 
  `@g4` ist ungültig, da sich das Innere der zwei inneren Ringe überlappt. 
  `@g5` ist ungültig, da der äußere Ring nicht der erste Ring ist. 
  `@g6` ist ungültig, da der Ring nicht mindestens drei unterschiedliche Punkte aufweist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine einfache `geometry``Polygon` mit einem Loch und dem SRID 10 erstellt.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);  
```  
  
 Eine Instanz, die nicht gültig ist, kann eingegeben und in eine gültige `geometry` -Instanz konvertiert werden. Im folgenden Beispiel für ein `Polygon`überlappen die inneren Ringe und der äußere Ring, weshalb die Instanz ungültig ist.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');  
```  
  
 Im folgenden Beispiel wird die ungültige Instanz mit `MakeValid()`in eine gültige konvertiert.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.ToString();  
```  
  
 Die vom oben erwähnten Beispiel zurückgegebene `geometry` -Instanz ist ein `MultiPolygon`.  
  
```  
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))  
```  
  
 Es folgt ein weiteres Beispiel zum Konvertieren einer ungültigen Instanz in eine gültige geometry-Instanz. Im folgenden Beispiel wurde die `Polygon` -Instanz mit drei Punkten erstellt, die identisch sind:  
  
```sql  
DECLARE @g geometry  
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');  
SET @g = @g.MakeValid();  
SELECT @g.ToString()  
```  
  
 Die oben zurückgegebene geometry-Instanz ist ein `Point(1 3)`.  Wenn das angegebene `Polygon` gleich `POLYGON((1 3, 1 5, 1 3, 1 3))` ist, gibt `MakeValid()``LINESTRING(1 3, 1 5)`zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [STArea &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STExteriorRing &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)   
 [STNumInteriorRing &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)   
 [STInteriorRingN &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)   
 [STCentroid &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [MultiPolygon](../spatial/polygon.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)   
 [STIsValid &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STIsValid &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
  
