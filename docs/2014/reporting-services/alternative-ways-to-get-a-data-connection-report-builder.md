---
title: Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 6b0b08a1435a007c38511d4e93db1c2783dfa956
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296330"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a>Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator)
  Eine Datenverbindung enthält die Informationen zum Herstellen einer Verbindung mit einer externen Datenquelle, z. B. einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank. Normalerweise erhalten Sie die Verbindungsinformationen und den zu verwendenden Anmeldeinformationstyp vom Datenquellenbesitzer.  
  
 Sie können zum Angeben einer Datenverbindung eine freigegebene Datenquelle vom Berichtsserver verwenden oder eine eingebettete Datenquelle erstellen, die nur in einem bestimmten Bericht verwendet wird.  
  
 In den meisten Lernprogrammen werden eingebettete Datenquellen verwendet. Wenn Sie jedoch über Zugriff auf freigegebene Datenquellen verfügen, können stattdessen diese verwendet werden.  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a>Abrufen einer Datenverbindung von einer freigegebenen Datenquelle  
 Wenn der Berichtsserver verfügbare freigegebene Datenquellen enthält, zu deren Verwendung Sie berechtigt sind, können Sie diese Datenquellen anstelle einer eingebetteten Datenquelle verwenden. In den folgenden Verfahren wird gezeigt, wie Sie nach den freigegebenen Datenquellen suchen und die für die Verwendung erforderlichen Anmeldeinformationen angeben.  
  
 Sie müssen zu einem Berichtsserver navigieren und eine freigegebene Datenquelle auswählen. Normalerweise erhalten Sie die Berichtsserver-URL vom Berichtsserveradministrator.  
  
#### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a>So geben Sie eine Datenverbindung aus einer Liste freigegebener Datenquellen an  
  
1.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**. Die Seite **Verbindung mit einer Datenquelle auswählen** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Datenquellen eine Datenquelle aus, für Sie Zugriffsberechtigungen besitzen.  
  
3.  Klicken Sie auf **Verbindung testen**, um sicherzustellen, dass die Verbindung mit der Datenquelle hergestellt werden kann. Die Meldung "Die Verbindung wurde erfolgreich hergestellt" wird angezeigt. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  Klicken Sie auf **Weiter**.  
  
     Geben Sie ggf. die Anmeldeinformationen ein. Aktivieren Sie **Kennwort mit Verbindung speichern**, wenn Sie die Anmeldeinformationen lokal speichern möchten. Falls Sie diese Option nicht aktivieren, werden Sie jedes Mal, wenn Sie den Bericht ausführen, zur Eingabe von Anmeldeinformationen aufgefordert.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a>So geben Sie eine Datenverbindung an, indem Sie zu einer freigegebenen Datenquelle auf einem Berichtsserver navigieren  
  
1.  Klicken Sie auf der Seite **Dataset auswählen** auf **Dataset erstellen**und anschließend auf **Weiter**. Die Seite **Verbindung mit einer Datenquelle auswählen** wird geöffnet.  
  
2.  Klicken Sie auf **Durchsuchen**. Das Dialogfeld **Datenquelle auswählen** wird geöffnet.  
  
3.  Wählen Sie in der Dropdownliste **Suchen in** die Option **Letzte Sites und Server**aus. Klicken Sie im Datenquellenbereich auf die URL für den Server, und klicken Sie dann auf **Öffnen**.  
  
     Die Liste der Datenquellen oder Modelle wird angezeigt.  
  
4.  Alternativ können Sie die URL zum Berichtsserver im Feld **Name**eingeben. Klicken Sie auf **Öffnen**.  
  
     Der Berichts-Generator stellt eine Verbindung mit dem Berichtsserver her und lädt die im Stammordner verfügbaren Datenquellen.  
  
5.  Navigieren Sie zu einem Ordner mit einer Datenquelle, für die Sie ausreichende Berechtigungen besitzen, wählen Sie die Datenquelle aus, und klicken Sie dann auf **Öffnen**.  
  
     Nun wird wieder die Seite **Verbindung mit einer Datenquelle auswählen** angezeigt.  
  
6.  Klicken Sie auf **Verbindung testen**, um sicherzustellen, dass die Verbindung mit der Datenquelle hergestellt werden kann.  
  
     Die Meldung "Die Verbindung wurde erfolgreich hergestellt" wird angezeigt. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Geben Sie die Anmeldeinformationen ein, wenn Sie zur Eingabe eines Benutzernamens und Kennworts aufgefordert werden. Aktivieren Sie **Kennwort mit Verbindung speichern**, wenn Sie die Anmeldeinformationen lokal speichern möchten.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)  
  
  