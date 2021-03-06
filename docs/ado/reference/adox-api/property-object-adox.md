---
title: Property-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b7911608970e9860d7eddcf3e83156ac99645c3f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965396"
---
# <a name="property-object-adox"></a>Property-Objekt (ADOX)
Stellt ein Merkmal eines ADOX-Objekts dar.  
  
## <a name="remarks"></a>Bemerkungen  
 ADOX-Objekte verfügen über zwei Arten von Eigenschaften: integrierte und dynamische Eigenschaften.  
  
 Integrierte Eigenschaften sind die Eigenschaften, die für jedes neue Objekt sofort verfügbar sind. dabei wird die Syntax MyObject. Property verwendet. Sie werden nicht als Eigenschafts Objekte in der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md)-Auflistung eines Objekts angezeigt, sodass Sie Ihre Werte ändern können, wenn Sie Ihre Werte ändern können.  
  
 Dynamische Eigenschaften werden vom zugrunde liegenden Datenanbieter definiert und in der Properties-Auflistung für das entsprechende ADOX-Objekt angezeigt.  Auf dynamische Eigenschaften kann nur über die Auflistung verwiesen werden, wobei die Syntax MyObject. Properties (0) oder MyObject. Properties ("Name") verwendet wird.  
  
 Beide Arten von Eigenschaften können nicht gelöscht werden.  
  
 Ein dynamisches Eigenschafts Objekt verfügt über vier eigenständig integrierte Eigenschaften:  
  
 Die [Name](../../../ado/reference/ado-api/name-property-ado.md) -Eigenschaft ist eine Zeichenfolge, die die-Eigenschaft bezeichnet.  
  
 Die [Type](../../../ado/reference/ado-api/type-property-ado.md) -Eigenschaft ist eine ganze Zahl, die den Eigenschafts Datentyp angibt.  
  
 Die [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft ist eine Variante, die die Eigenschafts Einstellung enthält. Value ist die Standard Eigenschaft für ein Property-Objekt.  
  
 Die [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) -Eigenschaft ist ein langer Wert, der die Merkmale der Eigenschaft angibt, die für den Anbieter spezifisch sind.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [ADOX-Property-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
