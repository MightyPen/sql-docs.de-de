---
title: SQL_VARIANT_PROPERTY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQL_VARIANT_PROPERTY_TSQL
- SQL_VARIANT_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SQL_VARIANT_PROPERTY function
- sql_variant data type
ms.assetid: 50e5c1d9-4e95-4ed0-9c92-435c872a399e
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 22b11ff1f9a6ed218b4c63c2f22bfb6e2d441703
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74550198"
---
# <a name="sql_variant_property-transact-sql"></a>SQL_VARIANT_PROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den Basisdatentyp und andere Informationen über einen **sql_variant**-Wert zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
SQL_VARIANT_PROPERTY ( expression , property )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein Ausdruck vom Typ **sql_variant**.  
  
 *property*  
 Enthält den Namen der **sql_variant**-Eigenschaft, für die Informationen bereitgestellt werden sollen. *property* ist vom Datentyp **varchar(** 128 **)** . Die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|Zurückgegebener Basistyp von sql_variant|  
|-----------|-----------------|----------------------------------------|  
|**BaseType**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp, beispielsweise:<br /><br /> **bigint**<br /><br /> **binary**<br /><br /> **char**<br /><br /> **date**<br /><br /> **datetime**<br /><br /> **datetime2**<br /><br /> **datetimeoffset**<br /><br /> **decimal**<br /><br /> **float**<br /><br /> **int**<br /><br /> **money**<br /><br /> **nchar**<br /><br /> **numeric**<br /><br /> **nvarchar**<br /><br /> **real**<br /><br /> **smalldatetime**<br /><br /> **smallint**<br /><br /> **smallmoney**<br /><br /> **time**<br /><br /> **tinyint**<br /><br /> **uniqueidentifier**<br /><br /> **varbinary**<br /><br /> **varchar**|**sysname**<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**Genauigkeit**|Anzahl der Stellen des numerischen Basisdatentyps:<br /><br /> **datetime** = 23<br /><br />**datetime2** = 27<br /><br /> **smalldatetime** = 16<br /><br /> **float** = 53<br /><br /> **real** = 24<br /><br /> **decimal** (p,s) und **numeric** (p,s) = p<br /><br /> **money** = 19<br /><br /> **smallmoney** = 10<br /><br /> **bigint** = 19<br /><br /> **int** = 10<br /><br /> **smallint** = 5<br /><br /> **tinyint** = 3<br /><br /> **bit** = 1<br /><br /> Alle sonstigen Typen = 0|**int**<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**Skalieren**|Anzahl der Stellen hinter dem Dezimalkomma des numerischen Basisdatentyps:<br /><br /> **decimal** (p,s) und **numeric** (p,s) = s<br /><br /> **money** und **smallmoney** = 4<br /><br /> **datetime** = 3<br /><br />**datetime2** = 7<br /><br /> Alle sonstigen Typen = 0|**int**<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**TotalBytes**|Anzahl der Byte, die zum Speichern der Metadaten und der Daten des Werts erforderlich sind. Diese Informationen sind nützlich zum Überprüfen der maximalen Größe einer Datenseite in einer **sql_variant**-Spalte. Wenn der Wert größer als 900 ist, schlägt die Indexerstellung fehl.|**int**<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**Sortierung**|Stellt die Sortierung des entsprechenden **sql_variant**-Werts dar.|**sysname**<br /><br /> NULL = Eingabe ist nicht gültig.|  
|**MaxLength**|Maximale Länge des Datentyps in Byte. Beispielsweise entspricht **MaxLength** von **nvarchar(** 50 **)** dem Wert 100, während **MaxLength** von **int** dem Wert 4 entspricht.|**int**<br /><br /> NULL = Eingabe ist nicht gültig.|  
  
## <a name="return-types"></a>Rückgabetypen  
 **sql_variant**  
  
## <a name="examples"></a>Beispiele  
### <a name="a-using-a-sql_variant-in-a-table"></a>A. Verwenden von „sql_variant“ in einer Tabelle  
 Dann werden im folgenden Beispiel `SQL_VARIANT_PROPERTY`-Informationen über den `colA`-Wert `46279.1` abgerufen, wobei `colB` =`1689` und `tableA` über `colA` vom Typ `sql_variant` und `colB` verfügt.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]Beachten Sie, dass jeder dieser drei Werte vom Datentyp **sql_variant** ist.  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sql_variant-as-a-variable"></a>B. Verwenden von „sql_variant“ als Variable   
 Im folgenden Beispiel werden `SQL_VARIANT_PROPERTY`-Informationen über eine Variable namens @v1 abgerufen.  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
  
  

