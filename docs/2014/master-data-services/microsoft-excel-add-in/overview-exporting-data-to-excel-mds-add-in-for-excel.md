---
title: Laden von Daten (MDS-Add-in für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b628548b-982b-4e45-abf4-c8e83e3ab1c2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 3bbd3ac1bf97530d64760d1434b9e7e8f6a81d34
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482803"
---
# <a name="loading-data-mds-add-in-for-excel"></a>Laden von Daten (MDS-Add-In für Excel)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]In müssen Sie Daten aus dem MDS-Repository in ein aktives Excel-Arbeitsblatt laden, bevor Sie damit arbeiten können. Wenn Sie mit der Arbeit an den Daten fertig sind, veröffentlichen Sie sie im MDS-Repository, sodass andere Benutzer sie freigeben können.  
  
 Die Daten, die Sie laden können, sind auf die Daten beschränkt, für die Sie über eine Zugriffsberechtigung verfügen. Die Berechtigung, auf Daten zuzugreifen, wird in der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung oder programmgesteuert festgelegt.  
  
 Wenn Sie große Datenmengen laden, können Sie Warnungen festlegen, die angezeigt werden, wenn das Laden der Daten lange dauert. Klicken Sie hierzu in der Gruppe **Optionen** auf **Einstellungen**. Wählen Sie auf der Registerkarte **Daten** die Option **Filterwarnung für große Datasets anzeigen**aus.  
  
> [!WARNING]  
>  Eine MDS-aktivierte Arbeitsmappe darf nur in Excel mit dem MDS-Add-In für Excel geöffnet und aktualisiert werden. Das Öffnen der MDS-aktivierten Arbeitsmappe in Excel auf einem Computer, auf dem das MDS-Excel-Add-In nicht installiert ist, wird nicht unterstützt. Außerdem könnte dies die Arbeitsmappendatei beschädigen. Wenn Sie Daten für andere Personen freigeben möchten, empfiehlt es sich, ihnen eine Shortcutabfragedatei per E-Mail zu senden. Demgegenüber ist es nicht empfehlenswert die Arbeitsmappe nur zu speichern und sie per E-Mail zu versenden. Weitere Informationen über die Abfrage finden Sie unter [Senden einer Shortcutabfragedatei &#40;MDS-Add-In für Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md).  
  
## <a name="filtering-data"></a>Filtern von Daten  
 Sie können Daten vor dem Laden filtern, um die Datenmenge einzuschränken, die Sie herunterladen werden. Dies schließt die Auswahl der zu ladenden Attribute (Spalten) ein, die Reihenfolge, in der die Attribute angezeigt werden sollen, und die Elemente (Datenzeilen), mit denen Sie arbeiten möchten. Weitere Informationen finden Sie unter [Filtern von Daten vor dem Laden &#40;MDS-Add-in für Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Herstellen einer automatischen Verbindung und Laden von häufig verwendeten Daten  
 Wenn Sie immer eine Verbindung mit dem gleichen Server herstellen und den gleichen Satz Daten laden möchten, können Sie Shortcutabfragedateien erstellen, die Verbindungs- und Filterinformationen enthalten. Weitere Informationen zu Abfragedateien finden Sie unter [Shortcutabfragedateien &#40;MDS-Add-In für Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="refreshing-data"></a>Aktualisieren von Daten  
 Daten im MDS-Repository werden möglicherweise von anderen Benutzern aktualisiert, nachdem Sie sie geladen haben. Sie können diese Daten ohne Verlust von Änderungen, die Sie an nicht-MDS-Daten vorgenommen haben, abrufen. Weitere Informationen finden Sie unter [Aktualisieren von Daten &#40;MDS-Add-In für Excel&#41;](refreshing-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Filtern Sie MDS-Daten, bevor Sie sie in Excel laden.|[Daten vor dem Laden &#40;MDS-Add-in für Excel Filtern&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)|  
|Laden Sie MDS-Daten in Excel.|[Laden von Daten aus MDS in Excel](export-data-to-excel-from-master-data-services.md)|  
|Ändern Sie die Reihenfolge der Spalten, bevor Sie Daten herunterladen.|[Spalten &#40;MDS-Add-in für Excel neu anordnen&#41;](reorder-columns-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Verbindungen &#40;MDS-Add-in für Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Die shortcutabfragedateien &#40;MDS-Add-in für Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Master Data Services-Add-In für Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Sicherheits &#40;Master Data Services&#41;](../security-master-data-services.md)  
  
  
