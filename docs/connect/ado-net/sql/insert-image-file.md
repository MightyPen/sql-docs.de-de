---
title: Einfügen eines Bilds aus einer Datei
description: In diesem Artikel wird beschrieben, wie Sie ein Bild aus einer Datei verwenden.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 613ae5b3326bc49ab25f30628ecd85e13959e2dc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247741"
---
# <a name="inserting-an-image-from-a-file"></a>Einfügen eines Bilds aus einer Datei

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Je nach Feldtyp in Ihrer Datenquelle können Sie ein Blob (Binary Large Object) entweder als Binär- oder Zeichendaten in eine Datenbank schreiben. „Blob“ ist ein allgemeiner Begriff, der sich auf die Datentypen `text`, `ntext` und `image` bezieht, die in der Regel Dokumente und Bilder enthalten.  
  
Um einen BLOB-Wert in die Datenbank zu schreiben, geben Sie die entsprechende INSERT- oder UPDATE-Anweisung aus, und übergeben Sie den BLOB-Wert als Eingabeparameter. Wenn Ihr Blob in Form von Text gespeichert wird, z. B. als `text`-Feld in SQL Server, können Sie das Blob als Zeichenfolgenparameter übergeben. Wenn das Blob im Binärformat gespeichert wird, z. B. als `image`-Feld in SQL Server, können Sie ein Array vom Typ `byte` als binären Parameter übergeben.
  
## <a name="example"></a>Beispiel  
Im folgenden Codebeispiel werden Mitarbeiterinformationen zur Tabelle „Employees“ in der Datenbank „Northwind“ hinzugefügt. Ein Foto des Mitarbeiters wird aus einer Datei gelesen und zum Feld „Photo“ in der Tabelle hinzugefügt. Dieses Feld ist ein Bildfeld.  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
