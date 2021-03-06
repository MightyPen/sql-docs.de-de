---
title: ADO-Ereignisse | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 35169313ae487514403f62c8e6d1ba2c262cb8a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921007"
---
# <a name="ado-events"></a>ADO-Ereignisse

|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Wird nach dem **BeginTrans** -Vorgang aufgerufen.|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Wird nach dem **CommitTrans** -Vorgang aufgerufen.|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Wird aufgerufen, nachdem eine Verbindung gestartet wurde.|  
|[Verschluss](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Wird aufgerufen, nachdem eine Verbindung beendet wurde.|  
|[EndOf Recordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Wird aufgerufen, wenn versucht wird, zu einer Zeile hinter dem Ende des **Recordsets**zu wechseln.|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Wird aufgerufen, nachdem die Ausführung eines Befehls abgeschlossen wurde.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Wird aufgerufen, nachdem alle Datensätze in einem langwierigen asynchronen Vorgang in das **Recordset**abgerufen wurden.|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Wird in regelmäßigen Abständen während eines langwierigen asynchronen Vorgangs aufgerufen, um zu melden, wie viele Zeilen derzeit in das **Recordset**abgerufen wurden.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Wird aufgerufen, nachdem der Wert von einem oder mehreren **Feld** Objekten geändert wurde.|  
|[Info Message](../../../ado/reference/ado-api/infomessage-event-ado.md)|Wird aufgerufen, wenn während eines **ConnectionEvent** -Vorgangs eine Warnung auftritt.|  
|[Der Vorgang wurde beendet.](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Wird aufgerufen, nachdem die aktuelle Position im **Recordset geändert wurde** .|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Wird aufgerufen, nachdem ein oder mehrere Datensätze geändert wurden.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Wird aufgerufen, nachdem das **Recordset** geändert wurde.|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Wird nach dem **RollbackTrans** -Vorgang aufgerufen.|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Wird aufgerufen, bevor bei einem ausstehenden Vorgang der Wert von einem oder mehreren **Feld** Objekten im **Recordset**geändert wird.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Wird aufgerufen, bevor ein oder mehrere Datensätze (Zeilen) in der **recordmenge** geändert werden.|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Wird aufgerufen, bevor das **Recordset**durch einen ausstehenden Vorgang geändert wird.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Wird aufgerufen, bevor eine Verbindung gestartet wird.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Wird aufgerufen, kurz bevor ein ausstehender Befehl für diese Verbindung ausgeführt wird, und bietet dem Benutzer die Möglichkeit, die ausstehenden Ausführungs Parameter zu überprüfen und zu ändern.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Das Ereignis " **WillMove** " wird aufgerufen, *bevor* die aktuelle Position im **Recordset**durch einen ausstehenden Vorgang geändert wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Sammlungen](../../../ado/reference/ado-api/ado-collections.md)   
 [Dynamische ADO-Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO-Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Behandeln von ADO-Ereignissen](../../../ado/guide/data/handling-ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und-Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
