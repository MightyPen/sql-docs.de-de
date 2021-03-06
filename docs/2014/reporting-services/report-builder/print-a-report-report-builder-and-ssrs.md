---
title: Drucken eines Berichts (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b96936c9-c387-41a9-8c19-6eb325769ffd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 737e8ebfd96d98bff9ed144db33189e141dc0cfd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107772"
---
# <a name="print-a-report-report-builder-and-ssrs"></a>Drucken eines Berichts (Berichts-Generator und SSRS)
  Nach dem Speichern eines Berichts auf einem Berichtsserver können Sie diesen mit einem Browser, dem Berichts-Manager oder einer beliebigen Anwendung, die Sie zum Anzeigen eines exportierten Berichts verwenden, anzeigen und drucken. Vor dem Speichern eines Berichts können Sie ihn aus der Vorschau drucken.  
  
 Beim Drucken eines Berichts können Sie das zu verwendende Papierformat festlegen. Durch das Papierformat wird die Anzahl der Seiten in einem Bericht festgelegt und welche Berichtsdaten jeweils auf eine Seite passen. Das Papierformat beeinflusst nur Berichte, die mit harten Seitenumbrüchen gerendert werden: PDF, Bild und Druck. Die Festlegung des Papierformats hat keine Auswirkungen auf andere Renderer. Weitere Informationen finden Sie unter [Renderingverhalten &#40;Berichts-Generator und SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
 Auf der Berichts-Viewer-Symbolleiste im Berichts-Manager oder in der Vorschau des Berichts-Generators können Sie einen Bericht in einen Renderer mit harten Seitenumbrüchen exportieren oder auf die Schaltfläche Drucken klicken, um eine Kopie des Berichts zu drucken. Möglicherweise müssen Sie das Papierformat oder andere Seiteneinrichtungseigenschaften festlegen. Verwenden Sie das Dialogfeld **Berichtseigenschaften** , um Seiteneinrichtungseigenschaften zu ändern, z. B. das Papierformat.  
  
 Druckseitenränder können an zwei Stellen angegeben können: im Entwurfsmodus und im Ausführungsmodus.  
  
-   **Entwurfsmodus.** Wenn Sie Seitenränder im Entwurfsmodus festlegen, werden diese Einstellungen beim Speichern des Berichts in der Berichtsdefinition gespeichert.  
  
-   **Ausführungsmodus.** Wenn Sie Seitenränder im Ausführungsmodus festlegen, werden diese Informationen nicht in der Berichtsdefinition gespeichert. Wenn Sie den Bericht das nächste Mal ausdrucken, übernehmen Sie die Einstellungen aus der Berichtsdefinition, wenn Sie die Seitenränder nicht erneut angeben.  
  
    > [!NOTE]  
    >  Druckränder werden im Entwurfs- oder Ausführungsmodus nicht angezeigt. Es gibt keine Beziehung zwischen dem Entwurfsoberflächenbereich und dem Druckbereich des Berichts. Klicken Sie auf der Registerkarte **Ausführen** auf dem Menüband auf "Seitenlayout", um Druckränder im Ausführungsmodus anzuzeigen.  
  
 Weitere Informationen zur Berichtspaginierung finden Sie unter [Paginierung in Reporting Services (Berichts-Generator und SSRS)](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-print-a-report-in-report-builder"></a>So drucken Sie einen Bericht im Berichts-Generator  
  
1.  Öffnen Sie einen Bericht.  
  
2.  Klicken Sie auf der Registerkarte "Home" auf **Ausführen**.  
  
3.  (Optional) Klicken Sie auf **Seitenlayout** , um eine Druckvorschau des Berichts aufzurufen.  
  
4.  (Optional) Klicken Sie auf **Seite einrichten** , um Papier, Ausrichtung und Ränder festzulegen.  
  
    > [!NOTE]  
    >  Die Standardwerte für diese Einstellungen werden aus den Berichtseigenschaften übernommen, die in der Entwurfsansicht festgelegt werden. Die Werte, die Sie hier im Dialogfeld **Seite einrichten** festlegen, sind nur für diese Sitzung gültig. Wenn Sie diesen Bericht schließen und erneut öffnen, werden wieder die Standardwerte angezeigt.  
  
5.  Klicken Sie auf **Drucken**.  
  
6.  Im Dialogfeld **Drucken** können Sie einen Drucker auswählen und sonstige Druckoptionen angeben.  
  
### <a name="to-print-a-report-from-a-web-browser-application"></a>So drucken Sie einen Bericht von einem Webbrowser aus  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager zu dem Bericht, den Sie drucken möchten. Öffnen Sie den Bericht.  
  
3.  Klicken Sie auf der Symbolleiste oben im Bericht auf **Drucken**.  
  
    > [!NOTE]  
    >  Beim erstmaligen Drucken eines HTML-Berichts werden Sie vom Berichtsserver aufgefordert, ein ActiveX-Steuerelement zu installieren, das für das Drucken verwendet wird. Das Steuerelement muss installiert und konfiguriert werden.  
  
4.  Wählen Sie im Dialogfeld **Drucker** einen Drucker aus, und klicken Sie dann auf **Drucken**.  
  
### <a name="to-print-a-report-from-other-applications"></a>So drucken Sie einen Bericht von anderen Anwendungen aus  
  
1.  Navigieren Sie im Berichts-Manager zu dem Bericht, den Sie drucken möchten. Öffnen Sie den Bericht.  
  
2.  Wählen Sie auf der Symbolleiste oben im Bericht ein Renderingformat aus, und klicken Sie auf **Exportieren**. Der Bericht wird in einer Viewer-Anwendung geöffnet, die dem Renderingformat entspricht.  
  
     Wenn Sie z. B. PDF auswählen, wird der Bericht in Adobe Acrobat Reader geöffnet.  
  
3.  Klicken Sie in diesem Programm im Menü **Datei** auf **Drucken**.  
  
### <a name="to-change-paper-size"></a>So ändern Sie das Papierformat  
  
1.  Klicken Sie mit der rechten Maustaste außerhalb des Berichtshauptteils, und klicken Sie auf **Berichtseigenschaften**.  
  
2.  Wählen Sie in **Seite einrichten**einen Wert aus der Liste **Papierformat** aus. Jede Option füllt die Eigenschaft **Breite** und die Eigenschaft **Höhe** aus. Sie können auch ein benutzerdefiniertes Format angeben, indem Sie numerische Werte in den Feldern **Breite** und **Höhe** eingeben. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  Die Standardeinheiten der Größenwerte hängen von den Gebietsschemaeinstellungen des Benutzers ab. Geben Sie zum Festlegen einer anderen Einheit einen physischen Einheitenkennzeichner nach dem numerischen Wert ein, z. B. cm, mm, pt oder pc.  
  
### <a name="to-set-page-margins-in-design-mode"></a>So legen Sie Seitenränder im Entwurfsmodus fest  
  
-   Klicken Sie mit der rechten Maustaste auf den blauen Bereich um die Entwurfsoberfläche, klicken Sie auf **Berichtseigenschaften**und danach auf die Seite **Seite einrichten** .  
  
### <a name="to-set-page-margins-in-run-mode"></a>So legen Sie Seitenränder im Ausführungsmodus fest  
  
-   Klicken Sie auf **Seite einrichten** auf der Registerkarte **Ausführen** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drucken von Berichten &#40;Berichts-Generator und SSRS&#41;](print-reports-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Berichtseigenschaften (Dialogfeld, Seite einrichten, Berichts-Generator)](../report-properties-dialog-box-page-setup-report-builder.md)   
 [Berichtsentwurfsansicht &#40;Berichts-Generator&#41;](report-design-view-report-builder.md)  
  
  
