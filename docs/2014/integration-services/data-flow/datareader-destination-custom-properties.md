---
title: Benutzerdefinierte Eigenschaften des DataReader-Ziels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f151c3e8-3811-457d-a3d3-6158ca65a646
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 948ebbc696048915662caaa24b791e6258c459be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62827608"
---
# <a name="datareader-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des DataReader-Ziels
  Das DataReader-Ziel verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des DataReader-Ziels. Alle Eigenschaften außer `DataReader` weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaftenname|Datentyp|BESCHREIBUNG|  
|-------------------|---------------|-----------------|  
|DataReader|String|Der Klassenname des DataReader-Ziels.|  
|FailOnTimeout|Boolean|Gibt an, ob ein Fehler ausgegeben wird, wenn ein `ReadTimeout` auftritt. Der Standardwert dieser Eigenschaft ist **False**.|  
|ReadTimeout|Integer|Die Anzahl von Millisekunden, bevor ein Timeout auftritt. Der Standardwert dieser Eigenschaft beträgt 30000 (30 Sekunden).|  
  
 Die Eingabe und die Eingabespalten des DataReader-Ziels verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [DataReader Destination](datareader-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](../common-properties.md)  
  
  
