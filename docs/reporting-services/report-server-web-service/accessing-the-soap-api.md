---
title: Zugriff auf die SOAP-API | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c78f160e51265e4ce87a191aa3076dc4464c31d2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "63026171"
---
# <a name="accessing-the-soap-api"></a>Accessing the SOAP API
  Der Berichtsserver-Webdienst verwendet SOAP (Simple Object Access Protocol) über HTTP und agiert als Kommunikationsschnittstelle zwischen den Clientprogrammen und dem Berichtsserver. Der Webdienst verfügt über zwei Endpunkte (einen für die Berichtsausführung und einen für die Berichtsverwaltung) und besteht aus Methoden und einer Reihe komplexer Typenobjekte, anhand derer Sie auf die kompletten Funktionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zugreifen können. Um den Dienst aufzurufen, müssen Sie auf die Reporting Services-WSDL (Web Services Description Language) verweisen.  
  
## <a name="referencing-the-reporting-services-wsdl"></a>Verweisen auf die Reporting Services-WSDL  
 Um einen Webdienst erfolgreich aufzurufen, müssen Sie wissen, wie auf den Dienst zugegriffen wird, welche Vorgänge der Dienst unterstützt, welche Parameter der Dienst benötigt und was der Dienst zurückgibt. WSDL stellt diese Informationen in einem XML-Dokument bereit, das von einem Computer gelesen oder verarbeitet werden kann.  
  
 Die Berichtsserver-Webdienste werden an drei unterschiedlichen Endpunkten verfügbar gemacht. Der Name der WSDL-Datei ist für jeden Endpunkt anders. Der <xref:ReportService2010>-Endpunkt enthält Methoden zum Verwalten von Objekten auf einem Berichtsserver im einheitlichen Modus oder integrierten SharePoint-Modus. Auf die WSDL für diesen Endpunkt wird über `ReportService2010.asmx?wsdl.` zugegriffen.  
  
> [!NOTE]  
>  Der <xref:ReportService2005>-Endpunkt und der <xref:ReportService2006>-Endpunkt sind in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] als veraltet markiert. Der <xref:ReportService2010>-Endpunkt schließt die Funktionen beider Endpunkte ein und beinhaltet zusätzliche Verwaltungsfunktionen.  
  
-   Der <xref:ReportExecution2005>-Endpunkt ermöglicht es Entwicklern, Berichte programmgesteuert auf einem Berichtsserver zu verarbeiten und zu rendern. Sie können über `ReportExecution2005.asmx?wsdl` auf die WSDL dieses Endpunkts zugreifen.  
  
 Die WSDL kann von Development Kits verwendet werden, die SOAP- und Webdienste wie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK unterstützen.  
  
 Das folgende Beispiel zeigt das Format der URL zur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Verwaltungs-WSDL-Datei:  
  
```  
https://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 In der folgenden Tabelle werden die einzelnen Elemente in der URL beschrieben.  
  
|URL-Element|BESCHREIBUNG|  
|-----------------|-----------------|  
|*server*|Der Name des Servers, auf dem der Berichtsserver eingesetzt wird.|  
|*berichtsserver*|Der Name des Ordners, der den XML-Webdienst enthält. Dieser wird während des Setups konfiguriert.|  
|*\<endpunktname>.asmx*|Der Name des Webdienst-Endpunkts.|  
  
 Weitere Informationen über das WSDL-Format finden Sie in der WSDL-Spezifikation von W3C (World Wide Web Consortium) unter http://www.w3.org/TR/wsdl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Report Server Web Service (Report Server-Webdienst)](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
