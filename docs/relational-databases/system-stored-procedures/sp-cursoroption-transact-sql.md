---
title: sp_cursoroption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
author: stevestein
ms.author: sstein
ms.openlocfilehash: dce66e74f7415a8ff5ac6de4505d8a1f0632391b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108447"
---
# <a name="sp_cursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt Cursor Optionen fest oder gibt Cursor Informationen zurück, die von der gespeicherten Prozedur sp_cursoropen erstellt wurden. sp_cursoroption wird aufgerufen, indem ID = 8 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Argumente  
 *Hand*  
 Ein *handle* -Wert, der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der gespeicherten Prozedur sp_cursoropen generiert und zurückgegeben wird. für den *Cursor* ist ein **int** -Eingabe Wert für die Ausführung erforderlich.  
  
 *Ordnung*  
 Wird verwendet, um verschiedene Faktoren der Cursorrückgabewerte festzulegen. *Code* erfordert einen der folgenden **int** -Eingabewerte:  
  
|value|Name|BESCHREIBUNG|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Gibt für bestimmte angegebene Text- oder Bildspalten den Textzeiger, nicht aber die tatsächlichen Daten zurück.<br /><br /> TEXTPTR_ONLY ermöglicht das Verwenden von Text Zeigern als *Handles* für BLOB-Objekte, die später selektiv mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)] von oder DBLIB-Funktionen (z. [!INCLUDE[tsql](../../includes/tsql-md.md)] b. "Read Text" oder "DBLIB dbwrite-Text") selektiv abgerufen oder aktualisiert werden können.<br /><br /> Wenn der Wert "0" zugewiesen wird, geben alle Text- und Bildspalten in der Auswahlliste Textzeiger anstelle von Daten zurück.|  
|0x0002|CURSOR_NAME|Weist dem Cursor den in *value* angegebenen Namen zu. Dies ermöglicht ODBC wiederum, positionierte UPDATE/ [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE-Anweisungen für Cursor zu verwenden, die über sp_cursoropen geöffnet wurden.<br /><br /> Die Zeichenfolge kann als beliebiges Zeichen oder Unicode-Datentyp angegeben werden.<br /><br /> Da [!INCLUDE[tsql](../../includes/tsql-md.md)] positionierte UPDATE/DELETE-Anweisungen standardmäßig in der ersten Zeile eines FAT-Cursors ausgeführt werden, sollte sp_cursor SetPosition zum Positionieren des Cursors verwendet werden, bevor die positionierte UPDATE/DELETE-Anweisung ausgegeben wird.|  
|0x0003|TEXTDATA|Gibt für bestimmte Text- oder Bildspalten in nachfolgenden Abrufvorgängen die tatsächlichen Daten und nicht den Textzeiger zurück (d. h., der Effekt von TEXTPTR_ONLY wird aufgehoben).<br /><br /> Wenn TEXTDATA für eine bestimmte Spalte aktiviert ist, wird die Zeile erneut abgerufen oder aktualisiert und kann dann auf TEXTPTR_ONLY zurückgesetzt werden. Wie bei TEXTPTR_ONLY ist der Wertparameter eine ganze Zahl, die die Spaltennummer angibt; beim Wert 0 (null) werden alle Text- oder Bildspalten zurückgegeben.|  
|0x0004|SCROLLOPT|Option für den Bildlauf. Weitere Informationen finden Sie weiter unten in diesem Thema unter "Rückgabecodewerte".|  
|0x0005|CCOPT|Option für die Parallelitätssteuerung. Weitere Informationen finden Sie weiter unten in diesem Thema unter "Rückgabecodewerte".|  
|0x0006|ROWCOUNT|Die Anzahl der aktuell im Resultset enthaltenen Zeilen.<br /><br /> Hinweis: die Zeilen Anzahl wurde möglicherweise geändert, da der von sp_cursoropen zurückgegebene Wert, wenn die asynchrone Auffüllung verwendet wird. Der Wert-1 wird zurückgegeben, wenn die Anzahl der Zeilen unbekannt ist.|  
  
 *Wert*  
 Legt den von *Code*zurückgegebenen Wert fest. *value* ist ein erforderlicher Parameter, der einen *Code* Eingabe Wert 0x0001, 0x0002 oder 0x0003 erfordert aufruft.  
  
> [!NOTE]  
>  Der *Codewert* 2 ist ein String-Datentyp. Alle anderen *Code* Wert Eingaben oder Rückgabe *Werte* sind eine ganze Zahl.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Der *value* -Parameter kann einen der folgenden *Codewerte* zurückgeben.  
  
|Rückgabewert|BESCHREIBUNG|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 Der *value* -Parameter gibt einen der folgenden scrollopt-Werte zurück.  
  
|Rückgabewert|BESCHREIBUNG|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 Der *value* -Parameter gibt einen der folgenden ccopt-Werte zurück.  
  
|Rückgabewert|BESCHREIBUNG|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 oder 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cursor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
