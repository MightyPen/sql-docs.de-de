---
title: Erstellen eines benutzerdefinierten Protokollanbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: db5ec327ab7f7672a55fbaa0d2cd086bbcfc67cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62896302"
---
# <a name="creating-a-custom-log-provider"></a>Erstellen eines benutzerdefinierten Protokollanbieters
  Die [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Laufzeitumgebung verfügt über umfangreiche Protokollierungsmöglichkeiten. In einem Protokoll können Sie Ereignisse aufzeichnen, die während der Paketausführung auftreten. 
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] beinhaltet eine Palette von Protokollanbietern, über die Protokolle erstellt und in verschiedenen Formaten wie XML, in Textform, in Datenbanken oder im Windows-Ereignisprotokoll gespeichert werden können. Wenn einer dieser Anbieter oder eines der Ausgabeformate nicht Ihren Bedürfnissen entspricht, können Sie einen benutzerdefinierten Protokollanbieter erstellen.  
  
 Die Schritte zum Erstellen eines benutzerdefinierten Protokollanbieters ähneln denen zum Erstellen jedes anderen benutzerdefinierten Objekts für [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Erstellen Sie eine neue Klasse, die von der Basisklasse erbt. Bei einem Protokollanbieter ist die Basisklasse <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.  
  
-   Weisen Sie das Attribut zu, das den Typ des Objekts für die Klasse identifiziert. Bei einem Protokollanbieter ist das Attribut <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.  
  
-   Überschreiben Sie die Implementierung der Methoden und Eigenschaften der Basisklasse. Bei einem Protokollanbieter gehören dazu die <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A>-Eigenschaft und die Methoden <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> und <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.  
  
-   Benutzerdefinierte Benutzeroberflächen für benutzerdefinierte Protokoll Anbieter sind in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]nicht implementiert.  
  
## <a name="getting-started-with-a-custom-log-provider"></a>Erste Schritte mit einem benutzerdefinierten Protokollanbieter  
  
### <a name="creating-projects-and-classes"></a>Erstellen von Projekten und Klassen  
 Da alle verwalteten Protokollanbieter von der <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>-Basisklasse abgeleitet sind, besteht der erste Schritt beim Erstellen eines benutzerdefinierten Protokollanbieters darin, in Ihrer bevorzugten verwalteten Programmiersprache ein Klassenbibliotheksprojekt anzulegen und dann eine Klasse zu generieren, die von der Basisklasse erbt. In dieser abgeleiteten Klasse überschreiben Sie die Methoden und Eigenschaften der Basisklasse, um die benutzerdefinierten Funktionen zu implementieren.  
  
 Konfigurieren Sie das Projekt für das Signieren der Assembly, die mit einer Schlüsseldatei mit starkem Namen erzeugt wird.  
  
> [!NOTE]  
>  Viele [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Protokollanbieter verfügen über eine benutzerdefinierte Benutzeroberfläche, die <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> implementiert und das Textfeld **Konfiguration** im Dialogfeld **SSIS-Protokolle konfigurieren** durch eine gefilterte Dropdownliste der verfügbaren Verbindungs-Manager ersetzt. Individuelle Benutzeroberflächen für benutzerdefinierte Protokollanbieter werden in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] jedoch nicht implementiert.  
  
### <a name="applying-the-dtslogprovider-attribute"></a>Zuweisen des 'DtsLogProvider'-Attributs  
 Weisen Sie das <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>-Attribut der Klasse zu, die Sie erstellt haben, um sie als Protokollanbieter zu kennzeichnen. Dieses Attribut stellt Entwurfszeitinformationen bereit, z. B. Name und Beschreibung des Protokollanbieters. Die `DisplayName` - `Description` Eigenschaft und die-Eigenschaft des-Attributs `Description` entsprechen dem **Namen** und den Spalten, die im Konfigurations-Editor für **SSIS** angezeigt werden, der beim [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]Konfigurieren der Protokollierung für ein Paket in angezeigt wird.  
  
> [!IMPORTANT]  
>  Die <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A>-Eigenschaft des Attributs wird nicht verwendet. Sie müssen jedoch einen Wert dafür eingeben, damit der benutzerdefinierte Protokollanbieter in der Liste der verfügbaren Protokollanbieter mit angezeigt wird.  
  
> [!NOTE]  
>  Da individuelle Benutzeroberflächen für benutzerdefinierte Protokollanbieter nicht in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] implementiert werden, hat das Angeben eines Werts für die <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A>-Eigenschaft von <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> keinerlei Auswirkungen.  
  
```vb  
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _  
Public Class MyLogProvider  
     Inherits LogProviderBase  
    ' TODO: Override the base class methods.  
End Class  
```  
  
```csharp  
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]  
public class MyLogProvider : LogProviderBase  
{  
    // TODO: Override the base class methods.  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>Erstellen, Bereitstellen und Debuggen eines benutzerdefinierten Protokollanbieters  
 Die Schritte zum Erstellen, Bereitstellen und Debuggen eines benutzerdefinierten Protokollanbieters in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ähneln denen für andere Arten benutzerdefinierter Objekte stark. Weitere Informationen finden Sie unter [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md) (Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten).  
  
![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Codieren eines benutzerdefinierten Protokoll Anbieters](coding-a-custom-log-provider.md)   
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten Protokollanbieter](developing-a-user-interface-for-a-custom-log-provider.md)  
  
  
