---
title: Assemblys (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
ms.openlocfilehash: ed494e55967bb02680f0397d3b651a59fd2d3bbc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028039"
---
# <a name="assemblies-database-engine"></a>Assemblys (Database Engine)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Themen in diesem Abschnitt enthalten Informationen, damit Sie Assemblys verstehen, entwerfen und implementieren können.  
  
 Assemblys sind dll-Dateien, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einer Instanz von verwendet werden, um Funktionen, gespeicherte Prozeduren, Trigger, benutzerdefinierte Aggregate und benutzerdefinierte Typen bereitzustellen, die in einer der verwalteten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Code Sprachen geschrieben werden, die von der Common Language Runtime [!INCLUDE[tsql](../../includes/tsql-md.md)](CLR) gehostet werden, statt in.  
  
 Eine Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist ein Objekt, das auf ein verwaltetes Anwendungsmodul (DLL-Datei) verweist, das in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-CLR erstellt wurde. Eine Assembly enthält Klassenmetadaten und verwalteten Code. Das Hochladen einer Assembly in eine Instanz von SQL Server ist der erste Schritt beim Erstellen eines der folgenden Datenbankobjekte:  
  
-   CLR-Funktionen. Weitere Informationen finden Sie unter [Erstellen von CLR-Funktionen](../../relational-databases/user-defined-functions/create-clr-functions.md).  
  
-   CLR-gespeicherte Prozeduren. Weitere Informationen finden Sie unter [gespeicherte CLR-Prozeduren](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33).  
  
-   CLR-Trigger. Weitere Informationen finden Sie unter [Erstellen von CLR-Triggern](../../relational-databases/triggers/create-clr-triggers.md).  
  
-   Benutzerdefinierte Aggregatfunktionen. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Aggregaten](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md).  
  
-   Benutzerdefinierte Typen. Weitere Informationen finden Sie unter [Verwenden von benutzerdefinierten Typen](../../relational-databases/native-client/features/using-user-defined-types.md).  
  
 Assemblys besitzen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die folgenden Funktionen:  
  
-   Aufnehmen des verwalteten Codes, der die Funktionen eines oder mehrerer der CLR-Datenbankobjekte ausführt, die oben aufgelistet wurden.  
  
-   Aufnehmen von Metadaten, die z. B. die Versionsnummer und Kultur der Assembly, einen optionalen öffentlichen Schlüssel zum eindeutigen Identifizieren der Liste der Klassen der Assembly, die in der Assembly definierten Methoden und die Prozessorarchitektur der Assembly umfassen.  
  
-   Verwalten des Grades, bis zu dem verwalteter Code auf externe Ressourcen zugreifen kann, durch Steuern der Codezugriffsberechtigungen.  
  
-   Aufnehmen von Metadaten zu Abhängigkeiten von anderen Assemblys, auf die durch die Assembly verwiesen wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Entwerfen von Assemblys](../../relational-databases/clr-integration/assemblies-designing.md)|Erläutert, was vor dem Erstellen einer Assembly berücksichtigt werden muss. Dazu zählen das Verpacken von Assemblys, Codezugriffsberechtigungen und andere Einschränkungen.|  
|[Implementieren von Assemblys](../../relational-databases/clr-integration/assemblies-implementing.md)|Beschreibt das Erstellen und Löschen von Assemblys, wie und wann Assemblys geändert werden und wie Metadaten zu Assemblys abgerufen werden.|  
|[Abrufen von Informationen zu Assemblys](../../relational-databases/clr-integration/assemblies-getting-information.md)|Stellt eine Liste der Katalogsichten und Funktionen zur Verfügung, die für Metadaten zu Assemblys abgefragt werden können.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
