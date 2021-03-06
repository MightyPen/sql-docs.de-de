---
title: Informationen zum SQL Server Datenbank-Engine | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6373f67d40b9da97f652f3bcb05b3414deab5c8d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779361"
---
# <a name="about-the-sql-server-database-engine"></a>Informationen zur SQL Server-Datenbank-Engine
  Bei der Komponente [!INCLUDE[ssDE](../../includes/ssde-md.md)] von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] handelt es sich um den zentralen Dienst zum Speichern, Verarbeiten und Sichern von Daten. Das [!INCLUDE[ssDE](../../includes/ssde-md.md)] bietet gesteuerten Zugriff und eine zügige Transaktionsverarbeitung und erfüllt damit die Anforderungen selbst der anspruchsvollsten datenlastigen Anwendungen des Unternehmens.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt bis zu 50 Instanzen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] auf einem einzelnen Computer. Informationen zum Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] typischen-Installation finden Sie unter [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).  
  
 **Wichtig** Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.  
  
 Die folgenden Funktionen werden installiert, wenn Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations-Assistenten auf der Seite zu installierenden Komponenten ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine** auswählen:  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Replikation – optionale Komponente  
  
-   Volltextsuche – optionale Komponente  
  
-   Data Quality Services: optionale Komponente  
  
    > [!NOTE]  
    >  In dieser Version wird durch Aktivieren des Kontrollkästchens **Data Quality Services** während des Setups DQS (Data Quality Services)-Server nicht installiert. Sie müssen nach der Installation weitere Schritte ausführen, um DQS-Server zu installieren. Weitere Informationen finden Sie unter [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 In vielen typischen Benutzerszenarien sind die folgenden zusätzlichen Funktionen als Optionen verfügbar:  
  
-   Data Quality Client  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Konnektivitätskomponenten  
  
-   Programmmodelle  
  
-   Verwaltungstools  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Dokumentationskomponenten  
  
> [!NOTE]  
>  Standardmäßig werden Beispieldatenbanken und Beispielcode nicht als Teil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups installiert. Informationen zur Installation von Beispieldatenbanken und Beispielcode finden Sie auf der [CodePlex-Website](https://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von den-Editionen unterstützte Funktionen SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Editionen und Komponenten von SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Planen einer SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Hoch Verfügbarkeits Lösungen &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Upgrade auf SQL Server 2014 mithilfe des Installations-Assistenten &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
