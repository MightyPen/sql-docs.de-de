---
title: Zugriff auf den Integration Services-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e3654be0afe51be6566a09897a2656dd53c77696
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062237"
---
# <a name="access-to-the-integration-services-service"></a>Zugriff auf den Integration Services-Dienst
  Über Paketschutzebenen kann gesteuert werden, wer ein Paket bearbeiten und ausführen darf. Zusätzlicher Schutz ist erforderlich, um die Anzahl der Personen einzuschränken, die die Liste der derzeit auf einem Server ausgeführten Pakete anzeigen und die Paketausführung in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]beenden dürfen.  
  
 
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienst zum Auflisten der ausgeführten Pakete verwendet. Mitglieder der Gruppe der Windows-Administratoren können alle aktuell ausgeführten Pakete anzeigen und ihre Ausführung beenden. Benutzer, die nicht zur Administratoren-Gruppe gehören, können nur solche ausgeführten Pakete anzeigen und deren Ausführung beenden, wenn sie selbst die Ausführung gestartet haben.  
  
 Es ist wichtig, den Zugriff auf Computer einzuschränken, auf denen ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienst ausgeführt wird. Dies gilt besonders für einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienst, der Remoteordner auflisten kann. Jeder authentifizierte Benutzer kann die Auflistung von Paketen anfordern. Auch wenn der Dienst den Dienst nicht findet, listet der Dienst Ordner auf. Diese Ordnernamen können für böswillige Benutzer von Nutzen sein. Wenn ein Administrator den Dienst so konfiguriert hat, dass Ordner auf einem Remotecomputer aufgelistet werden, können die Benutzer auch Ordnernamen anzeigen, die sie normalerweise nicht anzeigen könnten.  
  
  
