---
title: Parameter Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.openlocfilehash: 5140c69184332b1760859421b7e802a5163a0f09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100604"
---
# <a name="parameter-data-types"></a>Parameterdatentypen
Obwohl jeder Parameter, der mit **SQLBindParameter** angegeben wird, mit einem SQL-Datentyp definiert wird, haben die Parameter in einer SQL-Anweisung keinen systeminternen Datentyp. Daher können Parameter Markierungen nur in eine SQL-Anweisung eingeschlossen werden, wenn Ihre Datentypen von einem anderen Operanden in der Anweisung abgeleitet werden können. Beispielsweise in einem arithmetischen Ausdruck wie? + COLUMN1, der Datentyp des Parameters kann aus dem Datentyp der benannten Spalte abgeleitet werden, die durch COLUMN1 dargestellt wird. Eine Anwendung kann keine Parameter Markierung verwenden, wenn der Datentyp nicht bestimmt werden kann.  
  
 In der folgenden Tabelle wird beschrieben, wie ein-Datentyp in Übereinstimmung mit SQL-92 für verschiedene Typen von Parametern bestimmt wird. Eine umfassendere Spezifikation zum Ableiten des Parameter Typs, wenn andere SQL-Klauseln verwendet werden, finden Sie in der SQL-92-Spezifikation.  
  
|Speicherort des Parameters|Übernommene Datentyp|  
|---------------------------|-----------------------|  
|Ein Operand eines binären arithmetischen oder Vergleichs Operators|Identisch mit dem anderen Operanden|  
|Der erste Operand in einer **between** -Klausel.|Identisch mit dem zweiten Operanden|  
|Der zweite oder dritte Operand in einer **between** -Klausel.|Identisch mit dem ersten Operanden|  
|Ein Ausdruck, **der mit in** verwendet wird|Identisch mit dem ersten Wert oder der Ergebnisspalte der Unterabfrage.|  
|Ein mit **in** verwendeter Wert.|Identisch mit dem Ausdruck oder dem ersten Wert, wenn ein Parametermarker im Ausdruck vorhanden ist.|  
|Ein mit **like** verwendeter Musterwert|VARCHAR|  
|Ein Update Wert, der mit **Update** verwendet wird.|Identisch mit der Update-Spalte|
