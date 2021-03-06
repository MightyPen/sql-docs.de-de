---
title: Sicherstellen des ausreichenden tempdb-Speicherplatzes | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- TempDB space in RDS [ADO]
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe377cd15f2b95577a561e6784f78113b2843d07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922659"
---
# <a name="ensuring-sufficient-tempdb-space"></a>Sicherstellen, dass ausreichend TempDB-Speicherplatz vorhanden ist
Wenn bei der Verarbeitung von [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekten, für die ein Speicherplatz auf Microsoft SQL Server 6,5 erforderlich ist, Fehler auftreten, müssen Sie möglicherweise die Größe von tempdb erhöhen. (Für einige Abfragen ist ein temporärer Verarbeitungsbereich erforderlich, z. b. eine Abfrage mit einer ORDER BY-Klausel **, die einen**temporären Speicherplatz erfordert.)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
> [!IMPORTANT]
>  Lesen Sie dieses Verfahren, bevor Sie die Aktionen ausführen, da es nicht so einfach ist, ein Gerät zu verkleinern, sobald es erweitert wurde.  
  
> [!NOTE]
>  Standardmäßig ist inMicrosoft SQL Server 7,0 und höher für tempdb so festgelegt, dass es bei Bedarf automatisch vergrößert wird. Daher ist dieses Verfahren möglicherweise nur auf Servern erforderlich, auf denen frühere Versionen als 7,0 ausgeführt werden.  
  
### <a name="to-increase-the-tempdb-space-on-sql-server-65"></a>So vergrößern Sie den tempdb-Speicherplatz auf SQL Server 6,5  
  
1.  Starten Sie Microsoft SQL Server Enterprise-Manager, öffnen Sie die Struktur für den Server, und öffnen Sie dann die Struktur der Daten Bank Geräte.  
  
2.  Wählen Sie ein (physisches) Gerät zum Erweitern aus, z. b. Master, und doppelklicken Sie auf das Gerät, um das Dialogfeld **Daten Bank Gerät bearbeiten** zu öffnen.  
  
     In diesem Dialogfeld wird angezeigt, wie viel Speicherplatz die aktuellen Datenbanken verwenden.  
  
3.  Vergrößern Sie das Gerät im Feld **Größe** auf den gewünschten Betrag (z. b. 50 Megabyte (MB) Festplattenspeicher).  
  
4.  Klicken Sie auf **jetzt ändern** , um den Speicherplatz zu vergrößern, auf den die (logische) tempdb erweitert werden kann.  
  
5.  Öffnen Sie die Strukturdaten Banken auf dem Server, und doppelklicken Sie dann auf **tempdb** , um das Dialogfeld **Datenbank bearbeiten** zu öffnen. Auf der Registerkarte **Datenbank** wird der Speicherplatz aufgelistet, der derzeit tempdb zugewiesen ist (**Datengröße**). Der Standardwert ist 2 MB.  
  
6.  Klicken Sie unter der Gruppe **Größe** auf **erweitern**. In den Diagrammen wird der verfügbare und zugewiesene Speicherplatz auf den einzelnen physischen Geräten angezeigt. Die Balken in der kastanienbraun-Farbe stellen den verfügbaren Platz dar.  
  
7.  Wählen Sie ein **Protokoll Gerät**, z. b. Master, aus, um die verfügbare Größe im Feld **Größe (MB)** anzuzeigen.  
  
8.  Klicken Sie auf **jetzt erweitern** , um diesen Speicherplatz der tempdb-Datenbank zuzuordnen.  
  
     Im Dialogfeld **Datenbank bearbeiten** wird die neue zugeordnete Größe für tempdb angezeigt.  
  
 Weitere Informationen zu diesem Thema finden Sie in der Hilfedatei für den Microsoft SQL Server Enterprise-Manager, um das Dialogfeld "Datenbank erweitern" zu suchen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


