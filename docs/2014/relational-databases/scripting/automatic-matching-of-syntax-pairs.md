---
title: Automatischer Vergleich von Syntaxpaaren
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], delimiter highlighting
- IntelliSense [SQL Server], syntax pair matching
ms.assetid: bfc54cda-bfd6-4545-a5b9-f9db2ae13769
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49b121f776ec6a9d363236fab03a1da2228311a6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75244797"
---
# <a name="automatic-matching-of-syntax-pairs"></a>Automatischer Vergleich von Syntaxpaaren
  Durch den automatischen Vergleich von Syntaxpaaren erhalten Sie unmittelbar Aufschluss darüber, ob Syntaxelemente, die paarweise codiert werden müssen, ordnungsgemäß miteinander kombiniert sind. Im Abfrage-Editor von [!INCLUDE[ssDE](../../includes/ssde-md.md)] wird dieser Vorgang als Trennzeichenvergleich, im XMLA-Abfrage-Editor von Analysis Services als Klammernvergleich und im MDX- sowie im DMX-Editor als Klammernvergleich bezeichnet.  
  
## <a name="database-engine-query-editor-delimiter-matching"></a>Trennzeichenvergleich im Datenbank-Engine-Abfrage-Editor  
 Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor vergleicht die Trennzeichen, die die Begrenzungen von Codeblöcken angeben. Der Vergleich erfolgt auf zwei verschiedene Weisen:  
  
-   Der Editor hebt beide Trennzeichen in einem Paar hervor, sobald Sie das zweite Trennzeichen des Paars eingegeben haben.  
  
-   Immer, wenn sich der Cursor auf einem der Trennzeichen eines Paars befindet, können Sie mithilfe der Tastenkombination STRG+] zum entsprechenden Trennzeichen springen.  
  
### <a name="delimiter-pairs"></a>Trennzeichenpaare  
 Beim automatischen Trennzeichenvergleich werden die folgenden Trennzeichen erkannt:  
  
|Vorangestelltes Trennzeichen|Schließendes Trennzeichen|  
|--------------------|-----------------------|  
|**(**|**)**|  
|**BEGIN**|**END**|  
|**BEGIN TRY**|**END TRY**|  
|**BEGIN CATCH**|**END CATCH**|  
  
 Beim automatischen Trennzeichenvergleich werden die Trennzeichen für Bezeichner in Klammern ([ObjectName]) oder Bezeichner in Anführungszeichen ("ObjectName") nicht erkannt. Beim Paarvergleich werden die einzelnen Anführungszeichen als Trennzeichen für Zeichenfolgenliterale ('string') nicht verglichen, weil die Farbcodierung bereits erkennen lässt, ob die Zeichenfolge ein Trennzeichen aufweist.  
  
### <a name="delimiter-highlighting"></a>Hervorhebung von Trennzeichen  
 Beim Vergleich werden sowohl das vorangestellte als auch das schließende Element eines Paars von Trennzeichen hervorgehoben. Auf diese Weise können Sie Codeblöcke visuell identifizieren und überprüfen, ob nicht übereinstimmende Paare von Trennzeichen vorhanden sind.  
  
 Trennzeichen werden hervorgehoben, wenn Sie den letzten Buchstaben des Paars eingeben. Wenn Sie z. B. bei einem BEGIN…END-Paar zuerst BEGIN und dann END eingeben, wird die Hervorhebung aktiviert, sobald Sie den letzten Buchstaben von END eingeben. Es ist nicht erforderlich, zuerst das vorangestellte und dann das schließende Trennzeichen einzugeben, um die Hervorhebung zu aktivieren. Wenn Sie zuerst END eingeben und dann im Skript einen Bildlauf nach oben ausführen und BEGIN eingeben, wird die Hervorhebung aktiviert, sobald Sie den letzten Buchstaben von BEGIN eingeben. Der letzte eingegebene Buchstabe muss nicht der Buchstabe sein, mit dem das Trennzeichen endet. Wenn Sie z. B. BEGIN zuerst falsch schreiben und BEIN eingeben, wird das BEGIN…END-Paar hervorgehoben, sobald Sie das fehlende G eingeben.  
  
 Das Trennzeichenpaar bleibt so lange hervorgehoben, bis Sie den Cursor verschieben. Die Hervorhebung wird auch dann beim Verschieben des Cursors deaktiviert, wenn der Cursor an eine Position im gleichen Trennzeichen verschoben wird. Sie können die Hervorhebung wieder aktivieren, indem Sie einen beliebigen Buchstaben in einem Element des Paars löschen und erneut eingeben.  
  
## <a name="analysis-services-xmla-query-editor-brace-matching"></a>Klammernvergleich im XMLA-Abfrage-Editor von Analysis Services  
 Beim Klammernvergleich im XMLA-Abfrage-Editor können Sie erkennen, ob Sie die Elemente geschlossen haben, da öffnende und schließende Klammern hervorgehoben werden. Sie können auch mithilfe der Tastenkombination STRG+] von einer Klammer zur jeweils entsprechenden Klammer springen.  
  
 Im XMLA-Abfrage-Editor wird der Klammernvergleich für die folgenden Ausdrücke ausgeführt:  
  
-   Übereinstimmende Start- und Endtags  
  
-   Ein beliebiges Paar von spitzen Klammern („\<“ und „>“).  
  
-   Beginn und Ende von Kommentaren  
  
-   Beginn und Ende von Verarbeitungsanweisungen  
  
-   Beginn und Ende von CDATA-Blöcken  
  
-   Beginn und Ende von DTD-Deklarationen  
  
-   Öffnende und schließende Anführungszeichen bei Attributen  
  
## <a name="mdx-and-dmx-editor-parenthesis-matching"></a>Klammernvergleich im MDX- und im DMX-Editor  
 Der MDX-Editor (Multidimensional Expressions) und der DMX-Editor (Data Mining Expressions) gleichen automatisch Klammernpaare in Funktionen ab.  
  
  
