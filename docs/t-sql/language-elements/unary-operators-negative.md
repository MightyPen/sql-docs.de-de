---
title: '- (Negative) (Transact-SQL) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- negative
dev_langs:
- TSQL
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
- negative values
ms.assetid: d6c14d14-d379-403b-82db-c197ad58c896
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 992d0b8d0a2b3781af732aaa83983882a9938112
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68072143"
---
# <a name="unary-operators---negative"></a>Unäre Operatoren - Negative
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt den negativen Wert eines numerischen Ausdrucks zurück (einen unären Operator). Unäre Operatoren führen eine Operation mit nur einem Ausdruck eines beliebigen Datentyps der numerischen Datentypkategorie aus.   
  
|Operator|Bedeutung|  
|--------------|-------------|  
|[+ (Positive) (+ (Positiv))](../../t-sql/language-elements/unary-operators-positive.md)|Numerischer Wert ist positiv.|  
|[- (Negativ)](../../t-sql/language-elements/unary-operators-negative.md)|Numerischer Wert ist negativ.|  
|[~ (Bitweises NOT)](../../t-sql/language-elements/bitwise-not-transact-sql.md)|Gibt das Einerkomplement der Zahl zurück.|  
  
 Die Operatoren + (Positiv) und - (Negativ) können für einen beliebigen Ausdruck eines jeden Datentyps der numerischen Datentypkategorie verwendet werden. Der Operator ~ (Bitweises NOT) kann nur für Ausdrücke eines Datentyps der ganzzahligen Datentypkategorie verwendet werden. 
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
- numeric_expression  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md) eines der Datentypen aus der Kategorie numerischer Datentypen, mit Ausnahme der Datentypen für Datum und Uhrzeit.  
  
## <a name="result-types"></a>Ergebnistypen  
 Gibt einen Wert vom Datentyp *numeric_expression* zurück, wobei jedoch ein **tinyint**-Ausdruck ohne Vorzeichen zu einem **smallint**-Ergebnis mit Vorzeichen heraufgestuft wird.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-setting-a-variable-to-a-negative-value"></a>A. Festlegen einer Variablen auf einen negativen Wert  
 Im folgenden Beispiel wird eine Variable auf einen negativen Wert festgelegt.  
  
```  
USE tempdb;  
GO  
DECLARE @MyNumber decimal(10,2);  
SET @MyNumber = -123.45;  
SELECT @MyNumber AS NegativeValue;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
NegativeValue  
---------------------------------------  
-123.45  
  
(1 row(s) affected)  
  
```  
  
### <a name="b-changing-a-variable-to-a-negative-value"></a>B. Ändern einer Variablen in einen negativen Wert  
 Im folgenden Beispiel wird eine Variable in einen negativen Wert geändert.  
  
```  
USE tempdb;  
GO  
DECLARE @Num1 int;  
SET @Num1 = 5;  
SELECT @Num1 AS VariableValue, -@Num1 AS NegativeValue;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
VariableValue NegativeValue  
------------- -------------  
5             -5  
  
(1 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-negative-of-a-positive-constant"></a>C. Zurückgeben des negativen Werts einer positiven Konstante  
 Im folgenden Beispiel wird der negative Wert einer positiven Konstante zurückgegeben.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - 17 FROM DimEmployee;  
```  
  
 Rückgabe  
  
```  
-17  
```  
  
### <a name="d-returning-the-positive-of-a-negative-constant"></a>D: Zurückgeben des positiven Werts einer negativen Konstante  
 Im folgenden Beispiel wird der positive Wert einer negativen Konstante zurückgegeben.  
  
```  
USE ssawPDW;  
  
SELECT TOP (1) - ( - 17) FROM DimEmployee;  
```  
  
 Rückgabe  
  
```  
17  
```  
  
### <a name="e-returning-the-negative-of-a-column"></a>E. Zurückgeben des negativen Werts einer Spalte  
 Im folgenden Beispiel wird der negative Wert des `BaseRate`-Werts für jeden Mitarbeiter in der `dimEmployee`-Tabelle zurückgegeben.  
  
```  
USE ssawPDW;  
  
SELECT - BaseRate FROM DimEmployee;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Ausdrücke &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatoren &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  

