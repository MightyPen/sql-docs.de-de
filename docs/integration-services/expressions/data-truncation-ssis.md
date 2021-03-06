---
title: Abschneiden von Daten (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03b521f06925ad21847cf588b27c211167dbd425
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71297645"
---
# <a name="data-truncation-ssis"></a>Abschneiden von Daten (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Bei der Konvertierung von Werten in andere Datentypen kann es passieren, dass Werte abgeschnitten werden.  
  
 Abschneiden kann auftreten beim:  
  
-   Übersetzen von Daten einer *DT_WSTR* -Zeichenfolge in eine *DT_STR* -Zeichenfolge mit der gleichen Länge, wenn die ursprüngliche Zeichenfolge Doppelbytezeichen enthält.  
  
-   Umwandeln einer ganzen Zahl aus einem *DT_I4* - in einen *DT_I2* -Wert. Dabei können signifikante Ziffern verloren gehen.  
  
-   Umwandeln einer ganzen Zahl ohne Vorzeichen in eine ganze Zahl mit Vorzeichen; dabei können signifikante Ziffern verloren gehen.  
  
-   Umwandeln einer reellen Zahl aus einem *DT_R8* - in einen *DT_R4* -Wert. Dabei können nicht signifikante Ziffern verloren gehen.  
  
-   Umwandeln einer ganzen Zahl aus einem *DT_I4* - in einen *DT_R4* -Wert. Dabei können nicht signifikante Ziffern verloren gehen.  
  
 Die Ausdrucksauswertung identifiziert explizite Umwandlungen, durch die Daten abgeschnitten werden könnten und gibt eine Warnung aus, wenn der Ausdruck analysiert wird. Beispielsweise werden Sie von der Ausdrucksauswertung gewarnt, falls eine Zeichenfolge mit 30 Zeichen in eine Zeichenfolge mit 20 Zeichen umgewandelt wird.  
  
 Ob Daten abgeschnitten werden, wird jedoch zur Laufzeit nicht überprüft. Sie erhalten in diesem Fall also zur Laufzeit keine Warnung. Die meisten Datenadapter und Transformationen unterstützen Fehlerausgaben, die mit der Disposition von Fehlerzeilen umgehen können.  
  
 Weitere Informationen zum Behandeln des Abschneidens von Daten finden Sie unter [Fehlerbehandlung in Daten](../../integration-services/data-flow/error-handling-in-data.md)  
  
  
