---
title: Empty-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- empty function
- fn:empty function
ms.assetid: 46da89a8-0cd9-4913-8521-4087589a04ba
author: rothja
ms.author: jroth
ms.openlocfilehash: 888739807a79163a8188f3b2f27b7f7860032bc4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68004671"
---
# <a name="functions-on-sequences---empty"></a>Funktionen für Sequenzen – empty
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt true zurück, wenn der Wert *$arg* eine leere Sequenz ist. Andernfalls gibt die Funktion False zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:empty($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Eine Sequenz aus Elementen. Falls die Sequenz leer ist, gibt die Funktion True zurück. Andernfalls gibt die Funktion False zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **FN: vorhanden ()** -Funktion wird nicht unterstützt. Als Alternative kann die **Not ()** -Funktion verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-using-the-empty-xquery-function-to-determine-if-an-attribute-is-present"></a>A. Verwenden der empty() XQuery-Funktion zum Bestimmen, ob ein Attribut vorhanden ist  
 Beim Herstellungsprozess für das Produktmodell 7 gibt diese Abfrage alle Arbeitsplatz Standorte zurück, die kein **MachineHours** -Attribut aufweisen.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /AWMI:root/AWMI:Location[empty(@MachineHours)]  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
              $i/@MachineHours  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID      Result          
-------------- ------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
 Die folgende, etwas geänderte Abfrage gibt "NotFound" zurück, wenn das **MachineHour** -Attribut nicht vorhanden ist:  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace p14="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /p14:root/p14:Location  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
                 if (empty($i/@MachineHours)) then  
                    attribute MachineHours { "NotFound" }  
                 else  
                    attribute MachineHours { data($i/@MachineHours) }  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID Result                         
-------------- -----------------------------------  
7                
  <Location LocationID="10" LaborHrs="2.5" MachineHours="3"/>  
  <Location LocationID="20" LaborHrs="1.75" MachineHours="2"/>  
  <Location LocationID="30" LaborHrs="1" MachineHours="NotFound"/>  
  <Location LocationID="45" LaborHrs="0.5" MachineHours="0.65"/>  
  <Location LocationID="50" LaborHrs="3" MachineHours="NotFound"/>  
  <Location LocationID="60" LaborHrs="4" MachineHours="NotFound"/>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [XQuery-Funktionen für den XML-Datentyp](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [exist&#40; &#41;-Methode &#40;xml-Datentyp&#41;](../t-sql/xml/exist-method-xml-data-type.md)  
  
  
