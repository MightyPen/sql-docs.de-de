---
title: MSSQLSERVER_611 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 634c86066508aae367f90ff6e00b452a81939967
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62867324"
---
# <a name="mssqlserver_611"></a>MSSQLSERVER_611
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|611|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|VAR_SIZE_TOO_BIG|  
|Meldungstext|Es kann keine Zeile eingefügt oder aktualisiert werden, da die Gesamtgröße der Variablenspalte, einschließlich Verwaltungsbytes, die maximal zulässige Größe um %d Bytes überschreitet.|  
  
## <a name="explanation"></a>Erklärung  
 Die Maximalgröße der Variablenspalte übersteigt die vom Schema zugelassene Größe. Fehler 611 wird zurückgegeben, wenn die Variablenspalte die maximal zulässige Größe überschreitet, sofern das vardecimal-Speicherformat aktiviert ist, oder wenn die Größe der Variablenspalte die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für komprimierte Datensätze maximal zulässige Größe überschreitet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Reduzieren Sie die Größe des Datensatzes.  
  
  
