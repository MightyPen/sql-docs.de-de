---
title: ProtocolName-Eigenschaft (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolName Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolName property
ms.assetid: f8527121-fbcd-4d30-9b4a-1461149cb5a8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: beb51ea7270fdbeb96dc858c2ef4e65c386726ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660243"
---
# <a name="protocolname-property-clientnetworkprotocol-class"></a>ProtocolName-Eigenschaft (ClientNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Namen des aktuellen Netzwerkprotokolls ab, das in [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ProtocolName [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [ClientNetworkProtocol-Klassen](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) Objekt, das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgenwert, der den Namen des aktuellen Clientnetzwerkprotokolls angibt, auf das in der [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](https://technet.microsoft.com/library/ms179295.aspx)verwiesen wird.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
