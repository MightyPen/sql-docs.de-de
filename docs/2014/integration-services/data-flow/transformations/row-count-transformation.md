---
title: Transformation für Zeilenanzahl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d991ee94e04be0ea72450b8e3e4649c339d1c2a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62900210"
---
# <a name="row-count-transformation"></a>Transformation für Zeilenanzahl
  Die Transformation für Zeilenanzahl zählt die Zeilen in einem Datenfluss und speichert die endgültige Anzahl in einer Variablen.  
  
 Ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Paket kann die Zeilen Anzahl zum Aktualisieren der Variablen verwenden, die in Skripts, Ausdrücken und Eigenschafts Ausdrücken verwendet werden. (Beispielsweise kann mit der Variablen, die die Zeilenanzahl speichert, der Nachrichtentext in einer E-Mail-Nachricht aktualisiert und um die Zeilenanzahl ergänzt werden.) Die von der Transformation für Zeilenanzahl verwendete Variable muss bereits vorhanden sein, und zwar im Bereich des Datenflusstasks, zu dem der Datenfluss mit der Transformation für Zeilenanzahl gehört.  
  
 Die Transformation speichert den Zeilenanzahlwert erst dann in der Variablen, nachdem die letzte Zeile die Transformation durchlaufen hat. Daher wird der Wert der Variablen nicht rechtzeitig aktualisiert, um den aktualisierten Wert im Datenfluss zu verwenden, der die Transformation für die Zeilenanzahl enthält. Sie können die aktualisierte Variable in einem separaten Datenfluss verwenden.  
  
 Diese Transformation weist je eine Eingabe und eine Ausgabe auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Konfiguration der Transformation für Zeilenanzahl  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften dieser Komponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Variablen &#40;SSIS&#41;](../../integration-services-ssis-variables.md)   
 [Datenfluss](../data-flow.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)  
  
  
