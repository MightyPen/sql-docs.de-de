---
title: Beispiele für erweiterte SQL Server Integration Services-Ausdrücke | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- operators [Integration Services]
- expressions [Integration Services], examples
- examples [Integration Services]
ms.assetid: c7794ba3-0de5-466b-ae8a-9ddd27360049
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9272a6c11ce226f385c0b1f79f965a2a0f55835e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62901121"
---
# <a name="examples-of-advanced-integration-services-expressions"></a>Beispiele für erweiterte SQL Server Integration Services-Ausdrücke
  In diesem Abschnitt werden Beispiele für erweiterte Ausdrücke bereitgestellt, die mehrere Operatoren und Funktionen kombinieren. Falls ein Ausdruck in einer Rangfolgeneinschränkung oder der Transformation für bedingtes Teilen verwendet wird, muss er zu einem booleschen Wert ausgewertet werden. Diese Einschränkung gilt jedoch nicht für Ausdrücke, die in Eigenschaftsausdrücken, Variablen, der Transformation für abgeleitete Spalten oder im For-Schleifencontainer verwendet werden.  
  
 In den folgenden Beispiele werden die Datenbanken **AdventureWorks** und [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet. Jedes Beispiel identifiziert die verwendeten Tabellen.  
  
## <a name="boolean-expressions"></a>Boolesche Ausdrücke  
  
-   In diesem Beispiel wird die **Product** -Tabelle verwendet. Der Ausdruck wertet den Monatseintrag in der **SellStartDate** -Spalte aus und gibt TRUE zurück, wenn der Monat Juni oder ein späterer Monat ist.  
  
    ```  
    DATEPART("mm",SellStartDate) > 6  
    ```  
  
-   In diesem Beispiel wird die **Product** -Tabelle verwendet. Die Ausdrucksauswertung wertet das gerundete Ergebnis aus der Division der **ListPrice** -Spalte durch die **StandardCost** -Spalte aus und gibt TRUE zurück, wenn das Ergebnis größer als 1.5 ist.  
  
    ```  
    ROUND(ListPrice / StandardCost,2) > 1.50  
    ```  
  
-   In diesem Beispiel wird die **Product** -Tabelle verwendet. Der Ausdruck gibt TRUE zurück, falls alle drei Operationen zu TRUE ausgewertet werden. Wenn die **Size** -Spalte und die **BikeSize** -Variable inkompatible Datentypen aufweisen, erfordert der Ausdruck eine explizite Umwandlung, wie im zweiten Beispiel dargestellt. Die Umwandlung in den DT_WSTR-Datentyp schließt die Länge der Zeichenfolge ein.  
  
    ```  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE && Size != @BikeSize  
    MakeFlag ==  TRUE && FinishedGoodsFlag == TRUE  && Size != (DT_WSTR,10)@BikeSize  
    ```  
  
-   In diesem Beispiel wird die **CurrencyRate** -Tabelle verwendet. Der Ausdruck vergleicht Werte in Tabellen und Variablen. Er gibt TRUE zurück, falls Einträge in den Spalten **FromCurrencyCode** oder **ToCurrencyCode** mit Variablenwerten identisch sind und falls der Wert in **AverageRate** größer als der Wert in **EndOfDayRate**ist.  
  
    ```  
    (FromCurrencyCode == @FromCur || ToCurrencyCode == @ToCur) && AverageRate > EndOfDayRate  
    ```  
  
-   In diesem Beispiel wird die **Currency** -Tabelle verwendet. Der Ausdruck gibt TRUE zurück, falls das erste Zeichen in der **Name** -Spalte nicht a oder A ist.  
  
    ```  
    SUBSTRING(UPPER(Name),1,1) != "A"  
    ```  
  
     Der folgende Ausdruck stellt die gleichen Ergebnisse bereit, ist jedoch effizienter, weil nur ein Zeichen in Großbuchstaben konvertiert wird.  
  
    ```  
    UPPER(SUBSTRING(Name,1,1)) != "A"  
    ```  
  
## <a name="non-boolean-expressions"></a>Nicht boolesche Ausdrücke  
 Nicht boolesche Ausdrücke werden in der Transformation für abgeleitete Spalten, in Eigenschaftsausdrücken und im For-Schleifencontainer verwendet.  
  
-   In diesem Beispiel wird die **Contact** -Tabelle verwendet. Der Ausdruck entfernt führende und nachfolgende Leerzeichen aus den Spalten **FirstName**, **MiddleName**und **LastName** . Er extrahiert den ersten Buchstaben der **MiddleName** -Spalte, falls sie ungleich NULL ist, verkettet den Anfangsbuchstaben des zweiten Vornamens sowie die Werte in **FirstName** und **LastName**und fügt zwischen den Werten entsprechende Leerzeichen ein.  
  
    ```  
    TRIM(FirstName) + " " + (!ISNULL(MiddleName) ? SUBSTRING(MiddleName,1,1) + " " : "") + TRIM(LastName)  
    ```  
  
-   In diesem Beispiel wird die **Contact** -Tabelle verwendet. Der Ausdruck überprüft Einträge in der **Salutation** -Spalte. Er gibt einen **Salutation** -Eintrag oder eine leere Zeichenfolge zurück.  
  
    ```  
    (Salutation == "Sr." || Salutation == "Ms." || Salutation == "Sra." || Salutation == "Mr.") ? Salutation : ""  
    ```  
  
-   In diesem Beispiel wird die **Product** -Tabelle verwendet. Der Ausdruck konvertiert das erste Zeichen in der **Color** -Spalte in Großbuchstaben und konvertiert die restlichen Zeichen in Kleinbuchstaben.  
  
    ```  
    UPPER(SUBSTRING(Color,1,1)) + LOWER(SUBSTRING(Color,2,15))  
    ```  
  
-   In diesem Beispiel wird die **Product** -Tabelle verwendet. Der Ausdruck berechnet, seit wie vielen Monaten ein Produkt verkauft wird und gibt die Zeichenfolge "Unknown" zurück, falls die **SellStartDate** -Spalte oder die **SellEndDate** -Spalte NULL enthält.  
  
    ```  
    !(ISNULL(SellStartDate)) && !(ISNULL(SellEndDate)) ? (DT_WSTR,2)DATEDIFF("mm",SellStartDate,SellEndDate) : "Unknown"  
    ```  
  
-   In diesem Beispiel wird die **Product** -Tabelle verwendet. Der Ausdruck berechnet den Aufschlag für die **StandardCost** -Spalte und rundet das Ergebnis auf eine Genauigkeit von zwei Dezimalstellen auf. Das Ergebnis wird als Prozentsatz angezeigt.  
  
    ```  
    ROUND(ListPrice / StandardCost,2) * 100  
    ```  
  
## <a name="related-tasks"></a>Related Tasks  
 [Verwenden eines Ausdrucks in einer Datenflusskomponente](../use-an-expression-in-a-data-flow-component.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), auf pragmaticworks.com  
  
  
