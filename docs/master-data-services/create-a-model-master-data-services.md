---
title: Modellerstellung
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 730e18fca866891d62b68d321ec13e4be5da59bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728485"
---
# <a name="create-a-model-master-data-services"></a>Erstellen eines Modells (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein Modell, das Modellobjekte enthalten soll.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model"></a>So erstellen Sie ein Modul  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Modelle**.  
  
3.  Klicken Sie auf der Seite **Modelle verwalten** auf **Hinzufügen**. Auf der rechten Seite wird ein Panel angezeigt.  
  
4.  Geben Sie im Feld **Name** den Namen des Modells ein.  
  
5.  (Optional) Geben Sie im Feld **Beschreibung** die Modellbeschreibung ein.  
  
6.  Wählen Sie im Feld **Tage für Protokollbeibehaltung** eine der Optionen für die Aufbewahrung von Protokolldaten aus. Der Standardwert ist **Systemeinstellung**, was bedeutet, dass der Wert der Systemeinstellungen in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]übernommen wird. Weitere Informationen finden Sie unter [Systemeinstellungen &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
     Wählen Sie **NEIN**aus, um die Systemeinstellung zu überschreiben und Transaktionsprotokolldaten nicht zu entfernen. Wählen Sie **JA** aus, und legen Sie das Feld **Tage** auf „0“ fest, um die Protokolldaten aller vorherigen Tage zu entfernen und nur die Protokolldaten des aktuellen Tags aufzubewahren. Wählen Sie **JA** aus, und legen Sie das Feld **Tage** auf eine bestimmte Anzahl von Tagen fest, um die Protokolldaten für die angegebene Anzahl von Tagen aufzubewahren.  
  
7.  Optional können Sie **Entität mit demselben Namen wie das Modell erstellen** auswählen, um eine Entität mit dem gleichen Namen wie das Modell zu erstellen.  
  
8.  Klicken Sie auf **Modell speichern**.  
  
 Für jedes erstellte Modell wird dem Raster eine Zeile mit acht Spalten hinzugefügt. Die acht Spalten lauten:  
  
-   **Status**: der Status des Modells. Wenn Sie auf die Schaltfläche **Modell speichern** klicken, wird das ![Aktualisier](../master-data-services/media/mds-model-status-updating.png "Wird aktualisiert") Bare Bild angezeigt, das angibt, dass das Modell aktualisiert wird. Wenn beim Erstellen oder Bearbeiten eines Modells Fehler auftreten, wird das ![Fehler](../master-data-services/media/mds-model-status-error.png "Fehler") Bild angezeigt. Andernfalls ist der Status OK, und das Bild ![OK](../master-data-services/media/mds-model-status-ok.png "OK") angezeigt.  
  
-   **Name**: der Modellname.  
  
-   **Beschreibung**: die Modellbeschreibung.  
  
-   **Tage für Protokoll Beibehaltung**: die Anzahl der Tage, die das Protokoll für das Modell aufbewahrt wird.  
  
-   **Erstellt von**: der Benutzername des Benutzers, der das Modell erstellt hat.  
  
-   **Erstellungsdatum und-Uhrzeit**: das Datum und die Uhrzeit der Erstellung des Modells.  
  
-   **Aktualisiert von**: der Benutzername des Benutzers, der das Modell zuletzt aktualisiert hat.  
  
-   **Aktualisiertes Datum und Uhrzeit**: Datum und Uhrzeit der letzten Aktualisierung des Modells.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Erstellen Sie eine Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Modelle &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Entitäten &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)   
 [&#40;Master Data Services eines Modells löschen&#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [Modell &#40;Master Data Services bearbeiten&#41;](../master-data-services/edit-model-master-data-services.md)   
 [Transaktionen &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)  
  
  
