---
title: Aktivieren der Option „Sperren von Seiten im Speicher“ (Windows) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0f6e938e3212e519ab51be1faf3f18e28957ef3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782278"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Aktivieren der Option Sperren von Seiten im Speicher (Windows)
  Mit dieser Windows-Richtlinie werden die Konten bestimmt, die einen Prozess zum Speichern von Daten im physischen Speicher verwenden können, um das systemgesteuerte Auslagern der Daten in den virtuellen Arbeitsspeicher zu vermeiden.  
  
> [!NOTE]  
>  Durch Sperren von Seiten im Arbeitsspeicher kann die Leistung bei der Auslagerung von Arbeitsspeicherdaten auf die Festplatte gesteigert werden.  
  
 Verwenden Sie das Windows-Tool für Gruppenrichtlinien (gpedit.msc), um diese Richtlinie für das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendete Konto zu aktivieren. Diese Richtlinie können Sie nur ändern, wenn Sie als Systemadministrator angemeldet sind.  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>So aktivieren Sie die Option "Sperren von Seiten im Speicher"  
  
1.  Klicken Sie im Menü **Start** auf **Ausführen**. Geben `gpedit.msc`Sie im Feld **Öffnen** den Text ein.  
  
2.  Erweitern Sie in der Konsole **Editor für lokale Gruppenrichtlinien** die Option **Computerkonfiguration**und dann **Windows-Einstellungen**.  
  
3.  Erweitern Sie **Sicherheitseinstellungen**und dann **Lokale Richtlinien**.  
  
4.  Wählen Sie den Ordner **Zuweisen von Benutzerrechten** aus.  
  
     Die Richtlinien werden im Detailbereich angezeigt.  
  
5.  Doppelklicken Sie im Detailbereich auf **Sperren von Seiten im Speicher**.  
  
6.  Klicken Sie im Dialogfeld **Lokale Sicherheitseinstellung > Sperren von Seiten im Speicher** auf **Benutzer oder Gruppe hinzufügen**.  
  
7.  Fügen Sie im Dialogfeld zum Auswählen von Benutzern, Dienstkonten oder Gruppen ein Konto mit Privilegien zum Ausführen von **sqlservr.exe** hinzu.  
  
8.  Melden Sie sich ab und anschließend erneut an, damit die Änderung wirksam wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](server-memory-server-configuration-options.md)  
  
  
