---
title: Dienst Prinzipal Namen (SPNs) im ODBC-Client
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 1d60cb30-4c46-49b2-89ab-701e77a330a2
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6eb3887586a7c0398b196ba042c44381c2d900f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75247379"
---
# <a name="service-principal-names-spns-in-client-connections-odbc"></a>Dienstprinzipalnamen (SPN) in Clientverbindungen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema werden ODBC-Attribute und Funktionen beschrieben, die Dienstprinzipalnamen (SPN) in Clientanwendungen unterstützen. Weitere Informationen zu Dienst Prinzipal Namen in Client Anwendungen finden Sie [unter Dienst Prinzipal Name &#40;SPN&#41; Unterstützung in Clientverbindungen](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md) und [erhalten gegenseitige Kerberos-Authentifizierung](../../../relational-databases/native-client-odbc-how-to/get-mutual-kerberos-authentication.md).  
  
## <a name="connection-string-keywords"></a>Schlüsselwörter für Verbindungszeichenfolgen  
 Die folgenden Schlüsselwörter für Verbindungszeichenfolgen ermöglichen Clientanwendungen, einen SPN anzugeben.  
  
|Schlüsselwort|value|  
|-------------|-----------|  
|**ServerSPN**|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge und bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
|**FailoverPartnerSPN**|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge und bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
  
## <a name="connection-attributes"></a>Verbindungsattribute  
 Die folgenden Verbindungsattribute ermöglichen es Clientanwendungen, einen SPN anzugeben und eine Authentifizierungsmethode abzufragen.  
  
|Name|type|Verwendung|  
|----------|----------|-----------|  
|SQL_COPT_SS_SERVER_SPN<br /><br /> SQL_COPT_SS_FAILOVER_PARTNER_SPN|SQLTCHAR, read/write|Gibt den SPN für den Server an. Der Standardwert ist eine leere Zeichenfolge und bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.<br /><br /> Dieses Attribut kann nur abgefragt werden, nachdem es programmgesteuert festgelegt wurde oder nachdem eine Verbindung geöffnet wurde. Wenn versucht wird, dieses Attribut für eine Verbindung abzufragen, die nicht geöffnet ist, und wenn dieses nicht programmgesteuert festgelegt wurde, dann wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState 08003 und der Meldung "Verbindung nicht geöffnet" protokolliert.<br /><br /> Wenn versucht wird, dieses Attribut festzulegen, wenn eine Verbindung geöffnet ist, dann wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState HY011 und der Meldung "Der Vorgang ist zu diesem Zeitpunkt nicht gültig" protokolliert.|  
|SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD|SQLTCHAR, read-only|Gibt die für die aktuelle Verbindung verwendete Authentifizierungsmethode zurück. An die Anwendung wird der Wert zurückgegeben, den Windows an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zurückgibt. Die folgenden Werte sind möglich:<br /><br /> "NTLM" wird zurückgegeben, wenn eine Verbindung mit der NTLM-Authentifizierung geöffnet wird.<br /><br /> "Kerberos" wird zurückgegeben, wenn eine Verbindung mit der Kerberos-Authentifizierung geöffnet wird.<br /><br /> <br /><br /> Dieses Attribut kann nur für eine geöffnete Verbindung gelesen werden, von der die Windows-Authentifizierung verwendet wurde. Wenn versucht wird, dieses Attribut zu lesen, bevor eine Verbindung geöffnet wurde, dann wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState 08003 und der Meldung "Verbindung nicht geöffnet" protokolliert.<br /><br /> Wenn dieses Attribut für eine Verbindung abgefragt wird, für die nicht die Windows-Authentifizierung verwendet wurde, wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState HY092 und der Meldung "Attribut/Optionsbezeichner ungültig (SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD ist nur für vertrauenswürdige Verbindungen verfügbar)" protokolliert.<br /><br /> Wenn die Authentifizierungsmethode nicht ermittelt werden kann,dann wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState HY000 und der Meldung "Allgemeiner Fehler" protokolliert.|  
|SQL_COPT_SS_MUTUALLY_AUTHENTICATED|SQLSMALLINT, read-only|Gibt SQL_TRUE zurück, wenn der Server in der Verbindung gegenseitig authentifiziert wurde; andernfalls wird SQL_FALSE zurückgegeben.<br /><br /> Dieses Attribut kann nur für eine geöffnete Verbindung gelesen werden. Wenn versucht wird, dieses Attribut zu lesen, bevor eine Verbindung geöffnet wurde, dann wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState 08003 und der Meldung "Verbindung nicht geöffnet" protokolliert.<br /><br /> Wenn dieses Attribut für eine Verbindung abgefragt wird, für die keine Windows-Authentifizierung verwendet wurde, wird SQL_FALSE zurückgegeben.|  
  
## <a name="odbc-function-support-for-specifying-spns"></a>ODBC-Funktionsunterstützung zum Angeben von SPN  
 Die folgenden ODBC-Funktionen unterstützen Clientanwendungen und SPN:  
  
-   [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
-   [SQLConnect](../../../relational-databases/native-client-odbc-api/sqlconnect.md)  
  
-   [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)  
  
-   [SQLGetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md)  
  
-   [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
