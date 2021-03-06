---
title: Reporting Services in SQL Server Data Tools (SSDT) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence Development Studio, Reporting Services in
ms.assetid: 0903c7b2-ac59-45f1-b7d0-922ecd9d76f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f9c9719f3e73326c2b86117b3a78a8ede927198d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68888938"
---
# <a name="reporting-services-in-sql-server-data-tools-ssdt"></a>Reporting Services in SQL Server-Datentools (SSDT)
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]ist eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] -Umgebung mit Erweiterungen, die für Business Intelligence-Lösungen spezifisch sind. 
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] ist in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthalten.  
  
 Verwenden Sie [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] zum Erstellen und Verwalten von Lösungen und Projekten für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Berichte und berichtsbezogene Elemente. 
  [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] stellt die Erstellungsumgebung des Berichts-Designers bereit. Im Bericht-Designer können Sie Berichtsdefinitionen, freigegebene Datenquellen, freigegebene Datasets und Berichtsteile öffnen, bearbeiten, speichern, bereitstellen und in der Vorschau anzeigen.  
  
 In diesem Thema werden die [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] -Lösungen, -Projekte, -Projektvorlagen und -Konfigurationen beschrieben, die für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]verwendet werden, sowie die Ansichten, Menüs, Symbolleisten und Tastenkombinationen, die Sie im Berichts-Designer verwenden können.  
  
 Eine Einführung in das Entwerfen von Berichten finden Sie unter [Entwerfen von Berichten mithilfe des Berichts-Designers &#40;SSRS&#41;](design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
##  <a name="bkmk_SolutionsandProjects"></a>Projektmappen und Projekte  
 Ein Berichtsprojekt dient als Container für Berichtsdefinitionen und Ressourcen. Jede Datei im Berichtsprojekt wird bei der Bereitstellung des Projekts auf dem Berichtsserver veröffentlicht. Wenn Sie zum ersten Mal ein Projekt erstellen, wird zusätzlich eine Projektmappe als Container für das Projekt erstellt. Sie können mehrere Projekte zu einer Projektmappe hinzufügen.  

##  <a name="bkmk_Configurations"></a>Fehl  
 Wenn Sie mehrere Sätze von Projekteigenschaften für unterschiedliche Bereitstellungsvarianten (etwa Test- und Produktionsberichtsserver im Unternehmen) erstellen möchten, verwenden Sie den Konfigurations-Manager. Weitere Informationen finden Sie unter [Bereitstellung und Versionsunterstützung in SQL Server Data Tools &#40;SSRS&#41;](deployment-and-version-support-in-sql-server-data-tools-ssrs.md)enthalten.  
  
##  <a name="bkmk_ReportServerProjects"></a>Berichts Server Projekte  
 Bei der Installation von [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]werden die folgenden Projektvorlagen in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]verfügbar gemacht:  
  
-   **Berichts Server Projekt.** Wenn Sie ein Berichtsserverprojekt auswählen, wird der Berichts-Designer geöffnet. Bei einem Berichtsserverprojekt handelt es sich um eine von [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] installierte Business Intelligence-Projektvorlage, die über das Dialogfeld **Neues Projekt** aufgerufen werden kann. Weitere Informationen finden Sie unter [Hinzufügen eines neuen oder vorhandenen Berichts zu einem Berichtsprojekt (SSRS)](add-a-new-or-existing-report-to-a-report-project-ssrs.md). Eigenschaften von Berichtsserverprojekten gelten für alle Berichte und alle freigegebenen Datenquellen in einem [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]-Projekt. Zu diesen Eigenschaften zählen die URL für den Berichtsserver sowie die Ordnernamen für Berichte und freigegebene Datenquellen. Verwenden Sie das Dialogfeld **Eigenschaftenseiten für Projekt** , um die aktuellen Eigenschaftenwerte anzuzeigen. Um dieses Dialogfeld zu öffnen, klicken **** Sie **** _ \<_ im Menü Projekt auf Projektname>Eigenschaften.  
  
-   **Berichts Server Projekt-Assistent.** Wenn Sie ein Berichtsserver-Assistenten-Projekt auswählen, wird automatisch ein Berichtsserverprojekt erstellt und der Berichts-Assistent geöffnet. Mithilfe des Assistenten können Sie einen Bericht erstellen. Befolgen Sie hierzu die Anweisungen auf den einzelnen Seiten, um eine Verbindungszeichenfolge für eine Datenquelle zu erstellen, Datenquellen-Anmeldeinformationen festzulegen, eine Abfrage zu entwerfen, einen Tabellen- oder Matrixdatenbereich hinzuzufügen, Berichtsdaten und -gruppen anzugeben, Schriftart und Farbe auszuwählen, den Bericht auf einem Berichtsserver zu veröffentlichen und den Bericht lokal in der Vorschau anzuzeigen. Nachdem Sie mithilfe des Assistenten einen Bericht erstellt haben, können Sie die Berichtsdaten und den Berichts-Designer ändern, und zwar mithilfe des Berichts-Designers im Berichtsserverprojekt.  
  
 ![Neue Projektvorlagen in SSDT](https://docs.microsoft.com/analysis-services/analysis-services/media/ssdt-biprojects.png "Neue Projektvorlagen in SSDT")  

##  <a name="bkmk_ReportDesignerWindowsandPanes"></a>Fenster und Bereiche Berichts-Designer  
 Im Berichts-Designer werden zwei Ansichten unterstützt: **Entwurf** zum Definieren der Berichtsdaten und des Berichtslayouts sowie **Vorschau** zum Anzeigen einer gerenderten Ansicht des Berichts. In jeder Ansicht können Sie mehrere Fenster anzeigen, die Sie beim Entwerfen unterstützen. Außerdem können Sie einen gerenderten Bericht anzeigen.  
  
###  <a name="bkmk_ReportDataPane"></a>Berichtsdaten Bereich  
 im Berichtsdatenbereich werden integrierte Felder, Datenquellen, Datasets, Feldauflistungen, Berichtsparameter und Bilder angezeigt.  
  
 Verwenden Sie den Berichtsdatenbereich, um Folgendes anzuzeigen:  
  
-   **Integrierte Felder** Vordefinierte Berichts Informationen, z. b. der Berichts Name oder der Zeitpunkt, zu dem der Bericht verarbeitet wurde.  
  
-   **Datenquellen** Eine Datenquelle stellt einen Namen und eine Verbindung mit einer Datenquelle dar.  
  
-   **DataSets** Jedes Dataset enthält eine Abfrage, die angibt, welche Daten aus der Datenquelle abgerufen werden sollen. Erweitern Sie das Dataset, um die von der Datasetabfrage angegebene Feldauflistung anzuzeigen.  
  
     In einigen Abfrage-Designern für mehrdimensionale Datenquellen können Sie im Filterbereich Filter angeben und auswählen, ob Berichtsparameter erstellt werden sollen. Wenn Sie die Berichtsparameteroption angeben, wird automatisch ein spezielles Dataset erstellt, um die Liste mit den gültigen Werten des Parameters aufzufüllen.  Standardmäßig wird dieses Dataset nicht im Berichtsdatenbereich angezeigt. Weitere Informationen finden Sie unter [Anzeigen von ausgeblendeten Datasets für Parameterwerte für mehrdimensionale Daten &#40;Berichts-Generator und SSRS&#41;](../report-data/show-hidden-datasets-for-parameter-values-multidimensional-data.md).  
  
-   **Berichts Parameter** Die Liste der Berichts Parameter. Parameter können manuell oder automatisch erstellt werden, wenn eine Datasetabfrage Abfrageparameter einschließt.  
  
-   **Bilder** Die Liste der Bilder, die als Bild Berichts Element in einen Bericht eingeschlossen werden können.  
  
 Datenquellen und Datasets im Berichtsdatenbereich stellen die Elemente in der Berichtsdefinition dar. Der Berichtsdatenbereich ist eine Funktion, die von mehreren Berichtserstellungsumgebungen unterstützt wird. Im Berichts-Generator ist dies der einzige Bereich der zum Verwalten von Datenquellen und Datasets verfügbar ist. In Berichts-Designer kann der Berichtsdatenbereich mit dem Projektmappen-Explorer verwendet werden, der freigegebene Datenquellen und freigegebene Datasets als Dateien auflistet. Freigegebene Datenquellen und freigegebene Datasets im Berichtsdatenbereich müssen auf ihre entsprechenden freigegebenen Datenquellen und freigegebenen Datasets im Projektmappen-Explorer zeigen. Die Elemente des Berichtsdatenbereichs enthalten dann einen Verweis auf die Datendateien im Projektmappen-Explorer. Die Projekteigenschaften bestimmen, ob die freigegebenen Datenquellen und freigegebenen Datasets auf der Berichtsserver- oder SharePoint-Website bereitgestellt werden. Weitere Informationen finden Sie unter [Konvertieren einer Datenquelle aus Embedded in freigegebene &#40;Berichts-Generator und SSRS&#41;](../report-data/convert-data-sources-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Wenn der Berichtsdaten Bereich nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Berichtsdaten**. Wenn der Berichtsdatenbereich unverankert ist, können Sie ihn verankern. Weitere Informationen finden Sie unter [Andocken des Berichtsdatenbereichs im Berichts-Designer &#40;SSRS&#41;](dock-the-report-data-pane-in-report-designer-ssrs.md).  

###  <a name="bkmk_GroupingPane"></a>Gruppierungs Bereich  
 Verwenden Sie den Gruppierungsbereich, um Gruppen für einen Tablix-Datenbereich zu definieren. Sie können Zeilengruppen und Detailgruppen für Tabellen sowie Zeilen- und Spaltengruppen für Matrizen definieren. Sie können den Gruppierungsbereich nicht verwenden, um Gruppen für Diagramme und andere Datenbereiche zu definieren. Weitere Informationen finden Sie unter [Grundlegendes zu Gruppen &#40;Berichts-Generator und SSRS&#41;](../report-design/understanding-groups-report-builder-and-ssrs.md).  
  
 Der Gruppierungsbereich unterstützt zwei Modi:  
  
-   **Vorgegebene.** Verwenden Sie das Dialogfeld **Standard** , um alle Zeilen- und Spaltengruppen in einem hierarchischen Format anzuzeigen, das die Beziehung zwischen übergeordneten Gruppen, untergeordneten Gruppen, angrenzenden Gruppen und Detailgruppen aufzeigt. Eine untergeordnete Gruppe wird im Vergleich zu ihrer übergeordneten Gruppe unter und auf der nächsten Einzugsebene angezeigt. Eine angrenzende Gruppe wird auf der gleichen Einzugsebene wie ihre Peergruppen oder gleichgeordneten Gruppen angezeigt.  
  
     Verwenden Sie den Standardmodus, um Gruppen hinzuzufügen, zu bearbeiten oder zu löschen. Für Gruppen, die auf einem einzelnen Datasetfeld basieren, ziehen Sie das Feld in die Bereiche für Zeilengruppen und Spaltengruppen. Sie können die Gruppe über oder unter einer vorhandenen Gruppe einfügen. Zum Hinzufügen einer angrenzenden Gruppe klicken Sie mit der rechten Maustaste auf die gleichgeordnete Gruppe, und verwenden Sie dann das Kontextmenü. Um anzuzeigen, welche Tablixzellen zu einer Gruppe gehören, wählen Sie die Gruppe im Gruppierungsbereich aus.  
  
-   **Führende.** Verwenden Sie das Dialogfeld **Erweitert** , um statische und dynamische Zeilen- und Gruppenelemente des ausgewählten Tablix-Datenbereichs anzuzeigen.  Sie müssen Gruppenelemente verwenden, um Eigenschaften zur Steuerung der Sichtbarkeit der Zeilen und Spalten für eine Gruppe oder ein Gruppenmitglied oder die Regeln festzulegen, die von Renderern verwendet werden, um Gruppen auf einer Seite zusammenzuhalten. Gruppenelemente werden in der Entwurfsoberfläche als Zellen in den Zeilen- und Spaltengruppenbereichen angezeigt.  
  
> [!NOTE]  
>  Klicken Sie mit der rechten Maustaste auf den Pfeil nach unten, der sich rechts neben dem Symbol **Spaltengruppen** befindet, um zwischen den Modi **Standard** und **Erweitert** umzuschalten.  
  
 Weitere Informationen finden Sie unter [Grouping Pane](grouping-pane.md).  

###  <a name="bkmk_Toolbox"></a>Stens  
 Die Toolbox enthält Berichtselemente, die Sie auf die Entwurfsoberfläche ziehen können. Datenbereiche sind Berichtselemente, die Sie verwenden, um die Daten im Bericht zu organisieren. Tabelle, Matrix, Liste, Diagramm, Messgerät, Datenleiste, Sparkline und Indikator sind Datenbereiche. Andere Berichtselemente schließen Karte, Textfeld, Rechteck, Linie, Bild und Unterbericht ein. Diese Liste kann auch benutzerdefinierte Berichtselemente enthalten, wenn diese vom Systemadministrator installiert und registriert wurden.  
  
###  <a name="bkmk_PropertiesPane"></a>Eigenschaften Bereich  
 Der Eigenschaftenbereich ist ein Standardfenster von [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , in dem die Eigenschaftsnamen und Werte für das aktuell auf der Entwurfsoberfläche ausgewählte Berichtselement angezeigt werden. In den meisten Fällen entsprechen Eigenschaftsnamen den Elementen und Attributen in der RDL-Datei (Report Definition Language, Berichtsdefinitionssprache). Die am häufigsten verwendeten Eigenschaften können im Dialogfeld Eigenschaften für das ausgewählte Element festgelegt werden. Zum Öffnen des entsprechenden Dialogfelds klicken Sie auf die Schaltfläche **Eigenschaftenseiten** auf der Eigenschaftenbereichssymbolleiste. Erfahrene Benutzer können die Eigenschaftenwerte im Eigenschaftenbereich festlegen.  
  
 Verwenden Sie den Eigenschaftenbereich, um Folgendes durchzuführen:  
  
-   Festlegen von Eigenschaften für das aktuell ausgewählte Element auf der Entwurfsoberfläche. Einige Eigenschaften stellen eine Dropdownliste mit Werten bereit. Sie können den Wert auch direkt in die Zelle eingeben. Einige Eigenschaften enthalten eine Sammlung von Werten, die durch den Wert **(Auflistung)** angegeben wird. Die meisten Eigenschaften können einen Ausdruck akzeptieren. komplexe Ausdrücke werden durch den Wert ** \<Ausdruck>** angegeben. Klicken Sie ** \<auf Ausdrucks>** , um das Dialogfeld **Ausdruck** zu öffnen. Weitere Informationen finden Sie unter [Expression Dialog Box](../expression-dialog-box.md).  
  
-   Verwenden Sie die Schaltflächen in der Symbolleiste des Eigenschaftenbereichs, um das Raster von Kategoriesicht in alphabetische Sicht zu ändern. In der Kategoriesicht müssen Sie möglicherweise eine Kategorie erweitern, um alle Eigenschaften darunter zu sehen. Zum Öffnen des Dialogfelds „Eigenschaften“ für ein Element klicken Sie in der Symbolleiste auf die Schaltfläche **Eigenschaftenseiten** , oder klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Eigenschaften**.  
  
-   Legen Sie Eigenschaften für das aktuell ausgewählte Gruppenmitglied im Gruppierungsbereich fest. Mit Gruppenmitgliedseigenschaften können Sie steuern, wie statische Gruppenkopf- und -fußzeilen für die einzelnen Gruppeninstanzen wiederholt werden. Weitere Informationen finden Sie unter [Anzeigen von Kopf- und Fußzeilen einer Gruppe (Berichts-Generator und SSRS)](../report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md).  
  
 Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**, um das Eigenschaftenfenster anzuzeigen. Sie können die Verankerung dieses Bereichs aufheben und ihn an eine andere Stelle im [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]-Fenster verschieben oder auf der Entwurfsoberfläche als Ansicht im Registerkartenformat anzeigen.  

###  <a name="bkmk_SolutionExplorer"></a>Projektmappen-Explorer  
 Der Projektmappen-Explorer ist eine Standardkomponente von [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , die alle Elemente im Projekt anzeigt. Für ein Berichtsserverprojekt umfasst er Ordner zum Organisieren von freigegebenen Datenquellen, freigegebenen Datasets, Berichten und Ressourcen. Berichtselemente werden automatisch alphabetisch sortiert, wenn Sie die Projektmappendatei für ein Projekt öffnen. Um Elementeigenschaften im Eigenschaftenbereich anzuzeigen, wählen Sie das Element aus.  
  
###  <a name="bkmk_Output"></a>Ausgeben  
 Im Ausgabefenster werden Verarbeitungsfehler angezeigt, wenn Sie einen Bericht in der Vorschau anzeigen, und Veröffentlichungsfehler, wenn Sie einen Bericht oder eine freigegebene Datenquelle bereitstellen.  
  
 Verwenden Sie die Ausgabe- und Dokumentgliederungsfenster, um Fehler in Ausdrücken zu debuggen.  

###  <a name="bkmk_DocumentOutline"></a>Dokument Gliederung  
 Im Dokumentgliederungsfenster wird eine hierarchische Liste aller Berichtselemente angezeigt, die Teil der Berichtsdefinition sind. Zum Öffnen des Dokumentgliederungsbereichs zeigen Sie im Menü **Ansicht** auf **Weitere Fenster** , und klicken Sie dann auf **Dokumentfenster**.  
  
 Verwenden Sie den Dokumentgliederungsbereich, um Textfelder und andere Berichtselemente nach dem Namen zu identifizieren. Wenn Sie ein Element in der Dokumentgliederung auswählen, wird das Element auch auf der Entwurfsoberfläche ausgewählt.  
  
###  <a name="bkmk_TaskList"></a>Aufgabenliste  
 Im Fenster Aufgabenliste [!INCLUDE[msCoName](../../../includes/msconame-md.md)] werden Erstellungsfehler für nicht unterstützte Funktionen angezeigt, wenn Sie einen Bericht aus einer anderen Anwendung wie  Access importieren.  

##  <a name="bkmk_ReportDesignerDesignView"></a>Berichts-Designer Entwurfs Ansicht  
 Wenn Sie ein Berichtsserverprojekt erstellen, wird der Berichts-Designer standardmäßig in der Entwurfsansicht geöffnet und die Entwurfsoberfläche angezeigt. Die Entwurfsoberfläche enthält standardmäßig den Berichtstext sowie den Berichtshintergrund.  
  
 Das Hintergrund-Kontextmenü enthält Optionen zum Hinzufügen einer Kopf- und Fußzeile. Im Ansicht-Menü finden Sie ein Lineal und den Bereich für die Gruppierung.  
  
 Verwenden Sie das Zoomsteuerelement, um die Berichtsanzeige zu vergrößern oder zu verkleinern.  
  
 Um einen Bericht zu entwerfen, können Sie Berichtselemente aus der Toolbox auf die Entwurfsoberfläche ziehen. Im Anschluss können Sie ihre Eigenschaften konfigurieren und ihre Anordnung im Bericht ändern.  

##  <a name="bkmk_ReportDesignerPreview"></a>Berichts-Designer Vorschau  
 Verwenden Sie die Vorschau, um einen Bericht auszuführen und den gerenderten Bericht im Berichts-Viewer anzuzeigen. Mit Vorschau werden Berichtsdaten lokal zwischengespeichert. Sie können auch Konfigurationseigenschaften festlegen, um den Bericht in der Debugansicht auszuführen (über einen Browser).  
  
 Wenn Sie einen Bericht in der Vorschau anzeigen, wird vom Berichts-Designer eine Verbindung mit den Berichtsdatenquellen hergestellt und dann werden die Datasetabfragen ausgeführt, die Daten im Cache des lokalen Computers gespeichert, der Bericht verarbeitet, um Daten und Layout zu kombinieren, und der Bericht schließlich gerendert. Sie können den Bericht auf der Registerkarte Vorschau anzeigen oder Projekteigenschaften festlegen, um den Bericht im Debugmodus direkt in einem Browser anzuzeigen.  
  
-   **Anzeigen einer Vorschau für parametrisierte Berichte.** Wenn Sie eine Vorschau eines Berichts anzeigen, wird der Bericht automatisch verarbeitet, wenn alle Berichtsparameter über gültige Standardwerte verfügen. Wenn ein oder mehrere Berichtsparameter über keinen gültigen Standardwert verfügen, müssen Sie für jeden nicht zugewiesenen Parameter einen Wert auswählen und dann in der Symbolleiste des Berichts auf **Bericht anzeigen**klicken.  
  
-   Grundlegendes **zum lokalen Daten Cache** Wenn Sie einen Bericht in der Vorschau anzeigen, werden vom Berichts Prozessor alle Abfragen für Datasets im Bericht mithilfe der aktuellen Parameter Standardwerte ausgeführt, und die Ergebnisse werden als lokale Daten Cachedatei (. RDL. Data) gespeichert. Wenn Sie keine Änderungen an den Datasetabfragen des Berichts oder an den Berichtsparametern vornehmen, können Sie mit dem Entwerfen Ihres Berichts fortfahren, ohne diese Daten erneut abzurufen.  
  
-   **Anzeigen einer Vorschau des Berichts mithilfe von Configuration Manager und Debuggen.** In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]definieren Sie über Projekteigenschaften, wie Sie die Berichte bereitstellen und debuggen möchten. Diese Eigenschaften gelten für alle Berichte und freigegebenen Datenquellen im Projekt. Klicken Sie zum Festlegen der Projekteigenschaften im Menü **Projekt** auf **Eigenschaften**. Verwenden Sie diese Einstellungen, um Ihre Berichte zu testen und sie auf dem Berichtsserver zu veröffentlichen.  
  
-   **Überwachen des Ausgabe Bereichs für Fehlermeldungen.** Wenn Sie eine Vorschau für einen Bericht anzeigen und vom Berichtsprozessor ein Problem entdeckt wird, werden Fehlermeldungen in den Ausgabebereich geschrieben.  

##  <a name="bkmk_ReportDesignerMenus"></a>Berichts-Designer Menüs  
 Wenn in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]ein Berichts-Designer-Projekt aktiviert ist, werden der Hauptsymbolleiste die folgenden Symbolleisten hinzugefügt. Die Berichts-Designer-Menüs sind nur in der Entwurfsansicht sichtbar.  
  
###  <a name="FormatMenu"></a>Menü "Format"  
 Wenn Sie auf der Entwurfsoberfläche ein Element auswählen, enthält das Menü **Format** die folgenden Optionen:  
  
-   **Vordergrundfarbe** Wählen Sie eine Textfarbe aus. Die Standardtextfarbe ist Schwarz.  
  
-   **Hintergrundfarbe** Wählen Sie eine Hintergrundfarbe für die Textfelder und Datenbereiche aus.  
  
-   **Schriftart** Geben Sie an, ob der Text fett, kursiv oder unterstrichen ist.  
  
-   **Rechtfertigen** Geben Sie an, ob der Text rechtsbündig, zentriert oder linksbündig ausgerichtet ist.  
  
-   **Ausrichten** Geben Sie an, wie die ausgewählten Objekte innerhalb des Berichts zueinander ausgerichtet werden.  
  
-   **Größe angleichen** Passen Sie die Größe der ausgewählten Objekte innerhalb des Berichts an.  
  
-   **Horizontaler Abstand** Passen Sie den horizontalen Abstand zwischen den ausgewählten Objekten innerhalb des Berichts an.  
  
-   **Vertikaler Abstand** Passen Sie den vertikalen Abstand zwischen den ausgewählten Objekten innerhalb des Berichts an.  
  
-   **In Form zentrieren** Zentrieren Sie das ausgewählte Objekt vertikal und horizontal im Verhältnis zum Berichts-Designer Fenster.  
  
-   **Reihenfolge** Verschieben Sie ausgewählte Objekte in den Hintergrund oder den Vordergrund.  
  
###  <a name="ReportMenu"></a>Menü "Bericht"  
 Wenn sich der Fokus auf der Berichtsentwurfsoberfläche befindet, enthält das Menü **Bericht** die folgenden Optionen:  
  
-   **Berichts Eigenschaften** Wählen Sie diese Option, um das Dialogfeld **Berichts Eigenschaften** zu öffnen. In diesem Dialogfeld können Sie die allgemeinen Berichtseigenschaften, wie den Namen des Autors und den Rasterabstand zuweisen, und Sie können Eigenschaften für das Berichtslayout, wie die Anzahl der Spalten und die Seitengröße angeben. Sie können darüber hinaus benutzerdefinierten Code, Verweise auf Assemblys und Klassen sowie die Namen der Datenausgabeelemente, Datentransformationen und Datenschemas einschließen.  
  
-   **Anzeigen** Wechseln Sie zwischen den beiden Registerkarten Berichts-Designer: Entwurf und Vorschau.  
  
-   **Seiten Kopfzeile** Fügen Sie dem Bericht einen Seitenkopf hinzu, oder löschen Sie ihn. Wenn Sie einen Seitenkopf löschen, werden alle Elemente im Seitenkopf gelöscht.  
  
-   **Seitenfuß** Fügen Sie dem Bericht einen Seitenfuß hinzu, oder löschen Sie ihn. Wenn Sie einen Seitenfuß löschen, werden alle Elemente im Seitenfuß gelöscht.  
  
-   **Gruppierungs** Bereich Ein-oder Ausblenden des Gruppierungs Bereichs.  
  
###  <a name="ViewMenu"></a>Menü "Ansicht"  
 Verwenden Sie das Menü **Ansicht** , um die Berichts-Designer-Fenster und Symbolleisten anzuzeigen.  
  
-   **Fehlerliste** Verwenden Sie diese Option, um Fehler anzuzeigen, die beim Veröffentlichen oder Anzeigen eines Berichts in der Vorschau erkannt wurden.  
  
-   **Ausgabe** Verwenden Sie diese Option, um Fehler anzuzeigen, die bei der Veröffentlichung oder Verarbeitung eines Berichts erkannt wurden, oder um weitere Informationen zu Ausdrucks Fehlern anzuzeigen, wenn ein Bericht den Text "#Error" anzeigt.  
  
-   **Eigenschaften Fenster** Verwenden Sie diese Option, um die Eigenschaftswerte für das aktuell ausgewählte Berichts Element auf der Entwurfs Oberfläche anzuzeigen. Zum Anzeigen von Eigenschaften für geschachtelte Berichtselemente müssen Sie mehrfach auf ein Berichtselement klicken, um durch die Hierarchie des Berichtselements und seiner geschachtelten Elemente zu blättern. Überprüfen Sie den Namen des Elements, das im Eigenschaftenbereich ganz oben angezeigt wird, um festzustellen, für welches Element des Berichts die Eigenschaften angezeigt werden.  
  
-   **Toolbox** Verwenden Sie diese Option, um die Toolbox anzuzeigen.  
  
-   **Weitere Fenster** Verwenden Sie diese Option, um den folgenden Bereich anzuzeigen:  
  
    -   **Dokument** Gliederung Verwenden Sie diese Option, um eine hierarchische Ansicht der Berichts Elemente und deren Auflistungen von Textfeldern in einem Bericht anzuzeigen.  
  
-   **Symbolleisten** Verwenden Sie diese Option, um Symbolleisten anzuzeigen, die Berichts-Designer Funktionen unterstützen, einschließlich **Berichts** Rahmen und **Berichts Formatierung**. Weitere Informationen zum finden Sie unter [Berichts-Designer-Symbolleisten](#bkmk_ReportDesignerToolbars).  
  
-   **Berichtsdaten** Verwenden Sie diese Option, um den Berichtsdaten Bereich anzuzeigen, in dem Sie Berichts Parameter, Datenquellen, Datasets und Bilder hinzufügen können.  
  
###  <a name="ProjectMenu"></a>Menü "Projekt"  
 Verwenden Sie das Menü **Projekt** , um freigegebene Datenquellen und Berichte in einem Projekt zu verwalten. Wenn Sie dem Projekt Elemente hinzufügen oder Elemente daraus entfernen, wird die hierarchische Anzeige der Projektelemente im Projektmappen-Explorer automatisch aktualisiert.  
  
-   **Neues Element hinzufügen** Fügen Sie dem Projekt eine neue freigegebene Datenquelle oder einen neuen Bericht hinzu.  
  
-   **Vorhandenes Element hinzufügen** Fügen Sie dem Projekt eine vorhandene freigegebene Datenquelle oder einen vorhandenen Bericht hinzu.  
  
-   **Importieren von Berichten** Importieren Sie Berichte aus einer anderen Anwendung, z. b. Microsoft Access.  
  
-   **Aus Projekt ausschließen** Schließt Elemente aus dem Projekt aus. Diese Option löscht das Element nicht aus dem Dateisystem.  
  
-   **Alle Dateien anzeigen** Alle Dateien in einem Projekt anzeigen.  
  
-   **Projekt-Toolbox Elemente aktualisieren** Aktualisieren Sie den Toolbox Cache, wenn Sie neue benutzerdefinierte Berichts Elemente im Projekt installieren.  
  
-   **Eigenschaften** Öffnen Sie das Dialogfeld **Eigenschaften Seiten** für dieses Projekt. Weitere Informationen finden Sie auf den [Eigenschaftsseiten für Projekt (Dialogfeld)](project-property-pages-dialog-box.md).  

##  <a name="bkmk_ReportDesignerToolbars"></a>Berichts-Designer Symbolleisten  
 Beim Entwerfen von Berichten stellt Berichts-Designer die folgenden spezialisierten Symbolleisten bereit:  
  
-   **Bericht** Fügen Sie einen Seitenkopf oder einen Seitenfuß hinzu, legen Sie Berichts Eigenschaften fest, schalten Sie das Lineal oder den Gruppierungs Bereich um, oder verwenden Sie Zoom, um die Ansicht des Berichts zu ändern.  
  
-   **Berichts** Rahmen Legen Sie die Farbe, den Stil und die Breite für alle ausgewählten Zeilen und die Rahmen für alle ausgewählten Berichts Elemente fest.  
  
-   **Berichts Formatierung** Legen Sie das Format ausgewählter Berichts Elemente fest. Über diese Symbolleiste können die folgenden Formatierungen für Textfelder geändert werden: Schrifteigenschaften und Textfarbe, Hintergrundfarbe und Textausrichtung.  
  
-   **Layout** Festlegen der Zeichnungsreihenfolge von Berichts Elementen und Zusammenführen von Zellen in einem Datenbereich.  
  
-   **Standard** Öffnen oder speichern Sie Projekte, zeigen Sie Fenster an, und wählen Sie die Debugkonfiguration aus.  
  
 Steuern Sie über das Menü **Ansicht** , ob diese Symbolleisten angezeigt werden. Andere [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] -Symbolleisten werden möglicherweise deaktiviert, wenn ihre Funktionalität nicht für Berichts-Designer-Funktionen gilt.  

##  <a name="bkmk_SourceControl"></a>Quell Code Verwaltung  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]kann in Quell-Plug-ins integriert werden. verwenden Sie die Seiten Projekte und Projektmappen im Dialogfeld **Optionen** , um das Plug-in anzugeben und die Eigenschaften zu konfigurieren.  
  
##  <a name="bkmk_CustomReportTemplates"></a>Benutzerdefinierte Berichtsvorlagen  
 Wenn Sie benutzerdefinierte Berichte als Vorlagen für neue Berichte verwenden möchten, kopieren Sie diese einfach in den Ordner ReportProject auf dem Computer mit [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] . Standardmäßig befindet sich dieser Ordner im \<Laufwerk>: \Programme\Microsoft Visual Studio 10.0 \ Common7\IDE\Private Assemblies\ProjectItems\ReportProject. Wenn Sie dem Berichtsprojekt ein neues Element hinzufügen, wird der benutzerdefinierte Bericht im Vorlagenbereich angezeigt.  
  
 Zudem können Sie dem Berichts-Assistenten benutzerdefinierte Stile hinzufügen.  

##  <a name="bkmk_CommandLineSupportForssdt"></a>Befehlszeilen Unterstützung für SQL Server Data Tools  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]basiert auf [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 10,0 und der zugrunde liegenden Anwendung "wevenv. exe". Bevor Sie diese Optionen verwenden können, müssen Sie für beide folgenden Elemente gültige Werte festlegen:  
  
-   Projekteigenschaften für OverwriteDataSources, TargetDataSourceFolder, TargetReportFolder und TargetServerURL.  
  
-   Mindestens ein Satz von Konfigurationseigenschaften, z. B. Debug oder Release.  
  
 Weitere Informationen finden Sie unter [Publishing Data Sources and Reports](../reports/publishing-data-sources-and-reports.md).  
  
 Für ein Berichtsserverprojekt können Sie an der Befehlszeile die folgenden Optionen angeben:  
  
-   **/Deploy** Stellen Sie mithilfe der in einer Konfigurationsdatei angegebenen Projekteigenschaften Berichte bereit. Beispielsweise werden mit dem folgenden Befehl die in der Projektmappendatei Reports.sln angegebenen Berichte bereitgestellt, wobei die in den Projekteigenschaften angegebenen Einstellungen für die Releasekonfiguration verwendet werden:  
  
    ```  
    devenv.exe "C:\Users\MyUser\Documents\Visual Studio 2010\Projects\Reports\Reports.sln" /deploy "Release"  
    ```  
  
-   **/Build** Erstellen Sie die Projektmappendatei, aber stellen Sie Sie nicht bereit. Beispielsweise werden mit dem folgenden Befehl die in der Projektmappendatei Reports.sln angegebenen Berichte erstellt, wobei die in den Projekteigenschaften angegebenen Einstellungen für die Debugkonfiguration verwendet werden:  
  
    ```  
    devenv.exe "C:\Users\MyUser\Documents\Visual Studio 2010\Projects\Reports\Reports.sln" /build "Debug"  
    ```  
  
-   **/out** Leiten Sie die Ausgabe, die durch das Projekt erstellt wurde, in die angegebene Datei um. Beispielsweise wird mit dem folgenden Befehl die Ausgabe des Builds im vorherigen Beispiel in die Datei mybuildlog.txt umgeleitet.  
  
    ```  
    devenv.exe "C:\Users\MyUser\Documents\Visual Studio 2010\Projects\Reports\Reports.sln" /build "Debug" /out mybuildlog.txt  
    ```  

##  <a name="bkmk_KeyboardShortcuts"></a>Tastenkombinationen in Reporting Services  
 Verwenden Sie Tastenkombinationen für folgende Aktionen:  
  
-   Steuern von Fenstern und Modi in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]:  
  
    |BESCHREIBUNG|Tastenkombination|  
    |-----------------|---------------------|  
    |Erstellen des ausgewählten Projekts|CTRL+UMSCHALT+B|  
    |Anzeigen des Eigenschaftenfensters|F4|  
    |Anzeigen des Datenfensters|STRG+ALT+D|  
    |Starten des Debugvorgangs|F5|  
    |Verschieben von einem geöffnetem Fenster zum nächsten|F6,|  
  
-   Steuern von Elementen auf der Berichtsentwurfsoberfläche:  
  
    |BESCHREIBUNG|Tastenkombination|  
    |-----------------|---------------------|  
    |Fokus von einem Berichtselement zum nächsten Berichtselement verschieben|TAB|  
    |Ausgewähltes Berichtselement verschieben|Pfeiltasten|  
    |Ausgewähltes Berichtselement bewegen|STRG+Pfeiltasten|  
    |Größe des ausgewählten Berichtselements vergrößern oder verkleinern|STRG+UMSCHALT+Pfeiltasten|  
    |In einem Textfeld den Cursor an den Anfang des sichtbaren Anzeigetexts verschieben|STRG+POS1|  
    |In einem Textfeld den Cursor an das Ende des sichtbaren Anzeigetexts verschieben|STRG+ENDE|  
    |In einem Textfeld Text von der aktuellen Cursorposition bis zum Beginn des sichtbaren Anzeigetexts auswählen|UMSCHALT+POS1|  
    |In einem Textfeld Text von der aktuellen Cursorposition bis zum Ende des sichtbaren Anzeigetexts auswählen|UMSCHALT+ENDE|  
    |In einem Textfeld Text von der aktuellen Cursorposition bis zum Beginn des Ausdrucks auswählen|STRG+UMSCHALT+POS1|  
    |In einem Textfeld Text von der aktuellen Cursorposition bis zum Ende des Ausdrucks auswählen|STRG+UMSCHALT+ENDE|  
    |Das Kontextmenü für das ausgewählte Element öffnen|SHIFT+F10+Eigenschaftentaste auf neueren Tastaturen|  

## <a name="see-also"></a>Weitere Informationen  
 [Projektmappen-Explorer](../../ssms/solution/solution-explorer.md)   
 [Reporting Services Berichte &#40;SSRS&#41;](../reports/reporting-services-reports-ssrs.md)   
 [Berichtsdefinitionssprache (SSRS)](../reports/report-definition-language-ssrs.md)   
 [Bereitstellung und Versions Unterstützung in SQL Server Data Tools &#40;SSRS&#41;](deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
  
