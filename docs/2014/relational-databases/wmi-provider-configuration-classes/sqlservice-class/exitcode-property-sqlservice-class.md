---
title: ExitCode-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ExitCode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7a74c48cf512f33862f41484a5fb667918e81787
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63062488"
---
# <a name="exitcode-property-sqlservice-class"></a>ExitCode-Eigenschaft (SqlService-Klasse)
  Ruft den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32-Fehlercode ab, der beim Starten und Beenden des Diensts aufgetretene Probleme definiert, oder legt diesen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ExitCode [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [SqlService-Klassen](sqlservice-class.md) Objekt, das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der den Exitcode angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft wird auf ERROR_SERVICE_SPECIFIC_ERROR (1066) festgelegt, wenn der Fehler eindeutig in Bezug auf den Dienst ist, der durch diese Klasse dargestellt wird. Vom Dienst wird dieser Wert bei der Ausführung und erneut bei normaler Beendigung auf NO_ERROR festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
