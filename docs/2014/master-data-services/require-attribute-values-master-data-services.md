---
title: Erfordern von Attributwerten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 03f868d679f1d51dbb672cfdab5dbeaa2b4fc8a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65478863"
---
# <a name="require-attribute-values-master-data-services"></a>Erfordern von Attributwerten (Master Data Services)
  Erfordern Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Attributwerte, wenn Sie sicherstellen möchten, dass die Masterdaten vollständig sind.  
  
> [!NOTE]  
>  Elemente, denen domänenbasierte Attributwerte fehlen, werden nicht in abgeleiteten Hierarchien angezeigt, die auf diesen Beziehungen basieren.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-require-attribute-values"></a>So erfordern Sie Attributwerte  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Wählen Sie aus der Liste **Elementtyp** einen Typ des Elements aus, auf das die Geschäftsregel angewendet werden soll.  
  
6.  Wählen Sie aus der Liste **Attribut** ein Attribut aus, oder behalten Sie die Standardeinstellung **Alle**bei.  
  
7.  Klicken Sie auf **Geschäftsregel hinzufügen**.  
  
8.  Klicken Sie auf **Ausgewählte Geschäftsregel bearbeiten**.  
  
9. Erweitern Sie im Bereich **Komponenten** den Knoten **Aktionen** .  
  
10. Klicken Sie auf **ist erforderlich** , und ziehen Sie Sie auf die Bezeichnung **Aktion** des Bereichs **Then** .  
  
11. Klicken Sie im Bereich **Attribute** auf ein Attribut, und ziehen Sie es im Bereich **Aktion bearbeiten** auf die Bezeichnung **Attribut auswählen** .  
  
12. Klicken Sie im Bereich **Aktion bearbeiten** auf **Element speichern**.  
  
13. Klicken Sie auf **Zurück**.  
  
14. Optional können Sie auf der Seite **Verwaltung von Geschäftsregeln** für die Zeile, die die Geschäftsregel enthält, auf eine Zelle in den Spalten **Name**, **Beschreibung**oder **Benachrichtigung** doppelklicken, um den Wert zu aktualisieren.  
  
15. Klicken Sie auf **Geschäftsregeln veröffentlichen**.  
  
16. Klicken Sie im Bestätigungsdialogfeld auf **OK**. Der Status der Regel ändert sich zu **Aktiv**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Führen Sie zum Anwenden von Geschäftsregeln auf Daten eine der folgenden Prozeduren aus:  
  
    -   [Überprüfen bestimmter Mitglieder anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Master Data Services von Geschäftsregeln &#40;&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Abgeleitete Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
