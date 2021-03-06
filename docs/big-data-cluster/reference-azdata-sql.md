---
title: 'azdata sql: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata sql-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f8fa1ca8df7f4d72c6df9b252d639f8771dee30c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74908739"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata sql shell](#azdata-sql-shell) | Die SQL-Datenbank-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server zu interagieren.
[azdata sql query](#azdata-sql-query) | Der query-Befehl ermöglicht das Ausführen einer T-SQL-Abfrage.
## <a name="azdata-sql-shell"></a>azdata sql shell
Die SQL-Datenbank-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server zu interagieren.
```bash
azdata sql shell 
```
### <a name="examples"></a>Beispiele
Beispielbefehlszeile, um die interaktive Umgebung zu starten.
```bash
azdata sql shell
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-sql-query"></a>azdata sql query
Der query-Befehl ermöglicht das Ausführen einer T-SQL-Abfrage.
```bash
azdata sql query -q --database -d
```
### <a name="examples"></a>Beispiele
Wählen Sie die Liste der Tabellennamen aus.  In der Datenbank wird standardmäßig „master“ verwendet.
```bash
azdata sql query -q 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--database -d`
Die Datenbank, in der die Abfrage ausgeführt werden soll.  Der Standard ist „master“.
#### `-q`
Die T-SQL-Abfrage, die ausgeführt werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](deploy-install-azdata.md).
