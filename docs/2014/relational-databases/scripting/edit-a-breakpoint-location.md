---
title: Bearbeiten einer Breakpointposition
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2b5bb55452333014aa3ccf5a797d19667dca753
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75244888"
---
# <a name="edit-a-breakpoint-location"></a>Bearbeiten einer Breakpointposition
  Die Breakpointposition gibt die Zeile und das Zeichen an, wo sich der Breakpoint in einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei befindet. Sie können die Position des Breakpoints bearbeiten, um diesen an eine andere Position im Skript oder in ein anderes Skript zu verschieben.  
  
## <a name="editing-a-location"></a>Bearbeiten einer Position  
 Wenn Sie die Position eines Breakpoints bearbeiten, wird dieser mitsamt aller vorhandenen Eigenschaften, z. B. der Trefferanzahl oder einer Bedingung, an die neue Position verschoben.  
  
#### <a name="to-edit-a-breakpoint-location"></a>So bearbeiten Sie eine Breakpointposition  
  
1.  Klicken Sie im Editor-Fenster mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Speicherort** .  
  
     Oder  
  
     Klicken Sie im **Breakpointfenster** mit der rechten Maustaste auf das Breakpointsymbol, und klicken Sie dann im Kontextmenü auf **Speicherort**.  
  
2.  Bearbeiten Sie im Dialogfeld **Dateihaltepunkt** die Option **Datei** , um eine neue Datei anzugeben, **Zeile** , um eine neue Zeile anzugeben, oder **Zeichen** , um eine neue Position auf derselben Zeile anzugeben. Wenn die angegebene neue Datei bereits in einem Abfrage-Editor-Fenster geöffnet ist, wird der Breakpoint in dieses Editorfenster verschoben. Wenn die Datei nicht geöffnet wird, wird ein neues Editorfenster geöffnet, die Datei darin geladen und der Breakpoint an die neue Position verschoben.  
  
     Beim Debuggen von **hat die Option** Unterschiede zwischen Quellcode und Originalversion zulassen [!INCLUDE[tsql](../../includes/tsql-md.md)]keine Auswirkungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben einer Trefferanzahl](specify-a-hit-count.md)   
 [Haltepunkt Aktion angeben](specify-a-breakpoint-action.md)   
 [Angeben einer Breakpointbedingung](specify-a-breakpoint-condition.md)   
 [Angeben eines Breakpointfilters](specify-a-breakpoint-filter.md)  
