---
title: Modellberechtigungen
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5e42e54689b5b6a576a24fe57f2f9f4dcaccd1b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728973"
---
# <a name="model-permissions-master-data-services"></a>Modellberechtigungen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Modellberechtigungen gelten für alle Entitäten, Attribute, abgeleiteten Hierarchien, expliziten Hierarchien und Auflistungen innerhalb des Modells. Dem Modell zugewiesene Berechtigungen können für beliebige einzelne Objekte überschrieben werden.  
  
> [!NOTE]  
>  Wenn ein Benutzer ein Modelladministrator ist, wird das Modell in allen Funktionsbereichen der Benutzeroberfläche angezeigt. Andernfalls wird das Modell nur im Funktionsbereich **Explorer** angezeigt. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Lesen**|Der Benutzer kann Elemente, Attribute, Hierarchiemitgliedschaften oder Sammlungszugehörigkeiten anzeigen.|  
|**Stelle**|Der Benutzer kann Elemente erstellen und während der Erstellung Attributwerte zuweisen.|  
|**Alisierungs**|Der Benutzer kann Elemente, Attribute, Hierarchiemitgliedschaften oder Sammlungszugehörigkeiten aktualisieren.|  
|**Löschen**|Der Benutzer kann Elemente löschen.|  
|**Deny**|Der Zugriff auf das Modell wird vollständig verweigert.|  
|**Administrator**|Administratorberechtigung für das Modell. Die Administratorberechtigung ist nur auf Modellebene verfügbar.|  
  
 Die Berechtigungen zum Lesen, Erstellen, Aktualisieren und Löschen können miteinander kombiniert werden. Wenn Berechtigungen zum Erstellen, Aktualisieren und Löschen zugewiesen werden, wird die Leseberechtigung automatisch zugewiesen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modell Objekt Berechtigungen &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entitäts Berechtigungen &#40;Master Data Services&#41;](../master-data-services/entity-permissions-master-data-services.md)   
 [Sammlungs Berechtigungen &#40;Master Data Services&#41;](../master-data-services/collection-permissions-master-data-services.md)  
  
  
