---
title: Angeben von XML-Werten als Parameter
description: Hier wird veranschaulicht, wie XML-Daten als Parameter an einen Befehl übergeben werden.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 7f9893d7ac9dd83ae5212684678fc240a8d77097
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251145"
---
# <a name="specifying-xml-values-as-parameters"></a>Angeben von XML-Werten als Parameter

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Wenn eine Abfrage einen Parameter erfordert, dessen Wert eine XML-Zeichenfolge ist, können Entwickler den Wert mithilfe einer Instanz des **SqlXml**-Datentyps bereitstellen. XML-Spalten in SQL Server akzeptieren Parameterwerte ohne zusätzlichen Aufwand genau so wie andere Datentypen.  
  
## <a name="example"></a>Beispiel  
In der folgenden Konsolenanwendung wird eine neue Tabelle in der **AdventureWorks**-Datenbank erstellt. Die neue Tabelle enthält die Spalte **SalesID** und die XML-Spalte **SalesInfo**.  
  
> [!NOTE]
>  Beim Installieren von SQL Server wird die Beispieldatenbank **AdventureWorks** in der Standardeinstellung nicht installiert. Sie kann jedoch mithilfe von SQL Server-Setup installiert werden.  
  
Im Beispiel wird ein <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt auf das Einfügen einer Zeile in einer neuen Tabelle vorbereitet. Eine gespeicherte Datei stellt die XML-Daten für die Spalte **SalesInfo** bereit.  
  
Erstellen Sie eine neue Textdatei im selben Ordner wie Ihr Projekt, um eine Datei zu erstellen, die für die Ausführung des Beispiels erforderlich ist. Benennen Sie die Datei mit MyTestStoreData.xml. Öffnen Sie die Datei im Editor, kopieren Sie folgenden Text, und fügen Sie den Text ein:  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- <xref:System.Data.SqlTypes.SqlXml>
- [XML-Daten in SQL Server](xml-data-sql-server.md)
