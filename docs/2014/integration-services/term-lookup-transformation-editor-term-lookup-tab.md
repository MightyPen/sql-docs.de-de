---
title: Transformations-Editor für die Begriffs Suche (Registerkarte Begriffs Suche) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2939d160773d60944a2e8a786e5495cea366edb1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055129"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>Transformations-Editor für Ausdruckssuche (Registerkarte Ausdruckssuche)
  Mithilfe der Registerkarte **Ausdruckssuche** des Dialogfelds **Transformations-Editor für Ausdruckssuche** können Sie eine Eingabespalte einer Suchspalte in einer Verweistabelle zuordnen und einen Alias für jede Ausgabespalte bereitstellen.  
  
 Weitere Informationen zur Transformation für Ausdruckssuche finden Sie unter [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Verfügbare Eingabespalten**  
 Wählen Sie mithilfe der Kontrollkästchen die Eingabespalten aus, die unverändert an die Ausgabe weitergegeben werden. Ziehen Sie eine Eingabespalte auf die Liste **Verfügbare Verweisspalten** , um sie einer Suchspalte in der Verweistabelle zuzuordnen. Die Eingabe- und Suchspalten müssen übereinstimmende, unterstützte Datentypen haben, entweder DT_NTEXT oder DT_WSTR. Wählen Sie eine Zuordnungszeile aus, und klicken Sie mit der rechten Maustaste darauf, um die Zuordnungen im Dialogfeld [Beziehungen erstellen](data-flow/transformations/create-relationships.md) zu bearbeiten.  
  
 **Verfügbare Verweis Spalten**  
 Zeigen Sie die verfügbaren Spalten in der Verweistabelle an. Wählen Sie die Spalte aus, die die Liste der Ausdrücke enthält, für die nach einer Übereinstimmung gesucht wird.  
  
 **Pass-Through-Spalte**  
 Wählen Sie Spalten aus der Liste der verfügbaren Eingabespalten aus. Ihre Auswahl wird entsprechend in der Auswahl der Kontrollkästchen in der **Verfügbare Eingabespalten** -Tabelle deutlich.  
  
 **Alias der Ausgabe Spalte**  
 Geben Sie einen Alias für jede Spalte ein. Standardmäßig wird der Name der Spalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
 **Konfigurieren der Fehlerausgabe**  
 Auf der Registerkarte [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) können Sie die Optionen zur Fehlerbehandlung von Zeilen angeben, die Fehler verursachen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für die Begriffs Suche &#40;Registerkarte "Verweis Tabelle"&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [Transformations-Editor für die Begriffs Suche &#40;Registerkarte "Erweitert"&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [Transformation für Ausdrucksextrahierung](data-flow/transformations/term-extraction-transformation.md)  
  
  
