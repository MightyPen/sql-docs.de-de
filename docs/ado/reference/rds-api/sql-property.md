---
title: SQL-Eigenschaft | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f70eba6b5f53be7068708fdd8b139f0add10be90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963343"
---
# <a name="sql-property"></a>SQL-Eigenschaft
Gibt die Abfrage [Zeichenfolge](../../../ado/reference/ado-api/recordset-object-ado.md)an, mit der das Recordset abgerufen wird.  
  
 Sie können die **SQL** -Eigenschaft zur Entwurfszeit im [RDS festlegen. Objekt Tags des DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekts oder zur Laufzeit im Skriptcode.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Parameter  
 *QueryString*  
 Ein **Zeichen** folgen Wert, der eine gültige SQL-Daten Anforderung enthält.  
  
 *DataControl*  
 Eine Objekt Variable, die einen **RDS darstellt. DataControl** -Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Im Allgemeinen handelt es sich hierbei um eine SQL-Anweisung (mit dem Dialekt des Datenbankservers) `"Select * from NewTitles"`, z. b.. Um sicherzustellen, dass Datensätze korrekt abgeglichen und aktualisiert werden, muss eine aktualisierbare Abfrage ein anderes Feld als ein langes binäres Feld oder ein berechnetes Feld enthalten.  
  
 Die **SQL** -Eigenschaft ist optional, wenn ein benutzerdefiniertes serverseitiges Geschäftsobjekt die Daten für den Client abruft.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL-Eigenschafts Beispiel (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Connect-Eigenschaft (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Query-Methode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Refresh-Methode (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [SubmitChanges-Methode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


