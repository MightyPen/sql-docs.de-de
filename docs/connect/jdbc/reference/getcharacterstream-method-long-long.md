---
title: getCharacterStream-Methode (long, long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a47b7ea56873b0b502ba39a91e4d1ba30044e993
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67953256"
---
# <a name="getcharacterstream-method-long-long"></a>getCharacterStream-Methode (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die **CLOB**-Daten als Readerobjekt oder als Zeichendatenstrom mit der angegebenen Position und Länge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>Parameter  
 *pos*  
  
 Ein Wert vom Typ **long**, mit dem das Offset zum ersten Zeichen des abzurufenden Teilwerts angegeben wird.  
  
 *length*  
  
 Ein Wert vom Typ **long**, mit dem die Länge (in Zeichen) des abzurufenden Teilwerts angegeben wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Reader-Objekt, das die **Clob**-Daten enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCharacterStream-Methode wird von der getCharacterStream-Methode in der java.sql.Clob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getCharacterStream-Methode &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [SQLServerClob-Methoden](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob-Elemente](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
