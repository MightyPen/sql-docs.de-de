---
title: 'ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3184d9dff106628e09491852690da9f667570ff0
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579885"
---
# <a name="configurationsetting-method---listsslcertificatebindings"></a>ConfigurationSetting-Methode: ListSSLCertificateBindings
  Gibt eine Liste von auf dem Computer installierten SSL-Zertifikaten zurück  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *LCID*  
 Das Gebietsschema, das für die zurückgegebenen Fehlermeldungen verwendet werden soll  
  
 *Application[]*  
 [out] Die Anwendungen, die Zertifikatsbindungen aufweisen  
  
 *CertificateHash[]*  
 [out] Die Hashes für die Zertifikate  
  
 *IPAddress[]*  
 [out] Die IP-Adresse für die Anwendungen  
  
 *Port[]*  
 [out] Die in der Bindung in rsreportserver.config gespeicherte Portnummer.  
  
 *Errors[]*  
 [out] Die Beschreibungen für Fehler, die aufgetreten sind  
  
 *Länge*  
 [out] Die Länge des von der Methode zurückgegebenen Arrays  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
