---
title: Verbindungsbibliotheken für Microsoft SQL-Datenbanken | Microsoft-Dokumentation
description: Dieser Artikel bietet Links zum Download von Modulen, die eine Verbindung mit Microsoft SQL Server und Azure SQL-Datenbank mit verschiedenen Clientprogrammiersprachen ermöglichen.
author: MightyPen
ms.prod: sql
ms.technology: ''
ms.custom: ''
ms.topic: article
ms.date: 06/18/2018
ms.author: genemi
ms.openlocfilehash: 71254b937c4c0173af9e1549efb98a0b42f65e02
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73632818"
---
# <a name="connection-modules-for-microsoft-sql-databases"></a>Verbindungsmodule für Microsoft SQL-Datenbanken

Dieser Artikel bietet Links zum Download von Verbindungsmodulen oder *Treibern*, die Ihre Clientprogramme für die Interaktion mit der Plattform [Microsoft SQL Server](../relational-databases/database-features.md) und ihrem Pendant in der Cloud, [Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/), verwenden können. Treiber sind für verschiedene Programmiersprachen verfügbar und können unter folgenden Betriebssystemen ausgeführt werden:

- Linux
- MacOS
- Windows

#### <a name="oop-to-relational-mismatch"></a>Konflikt zwischen objektorientierter Programmierung und relationalem Datenbankformat

*Relationales Format*: Clientprogramme, die in einer objektorientierten Programmiersprache (Object-Oriented Programming, OOP) geschrieben sind, verwenden häufig SQL-Treiber, die die abgefragten Daten in einem Format zurückgeben, das eher relational als objektorientiert ist. C# mit ADO.NET ist ein Beispiel hierfür. Der Konflikt zwischen OOP und relationalem Format führt zuweilen dazu, dass OOP-Code schwieriger zu schreiben und zu verstehen ist.

*ORM*: Andere Treiber oder Frameworks geben die abgefragten Daten im OOP-Format zurück, um diesen Konflikt zu vermeiden. Diese Treiber erwarten, dass Klassen so definiert wurden, dass sie den Datenspalten bestimmter SQL-Tabellen entsprechen. Diese Treiber führen dann eine *objektrelationale Zuordnung* (Object-Relational Mapping, ORM) aus, um die abgefragten Daten als Instanz einer Klasse zurückzugeben. Das Microsoft Entity Framework (EF) für C# und Hibernate für Java sind zwei Beispiele hierfür.

Im vorliegenden Artikel sind diesen beiden Arten von Verbindungstreibern zwei separate Abschnitte gewidmet.

<a name="anchor-20-drivers-relational-access" />

## <a name="drivers-for-relational-access"></a>Treiber für den relationalen Zugriff


<!--
Each given Microsoft Download Center page should be enhanced
with a link to the next NEWER version page, on the day that the
original page is no longer the latest because the newer page is being added.
But this policy is not agreed on or observed,
putting the links in the following table at risk for being outdated.

PHP driver in Github.com also uses this FWLink:  https://go.microsoft.com/fwlink/?LinkID=518036 ,
although the FWLink is less precise than is https://github.com/Microsoft/msphpsql/tree/dev#install-unix .
-->

| Sprache | Download des SQL-Treibers |
| :------- | :---------------------- |
| C# | [ADO.NET](https://www.microsoft.com/net/download/)<br />[Microsoft.Data.SqlClient](https://www.nuget.org/packages/Microsoft.Data.SqlClient/)<br /><br />[.NET Core für Linux-Ubuntu](https://www.microsoft.com/net/core#Ubuntu)<br />[.NET Core für macOS](https://www.microsoft.com/net/core#macos)<br />[.NET Core für Windows](https://www.microsoft.com/net/core) |
| C++ | [ODBC](./odbc/download-odbc-driver-for-sql-server.md)<br /><br />[OLE DB](./oledb/download-oledb-driver-for-sql-server.md) |
| Java | [JDBC](./jdbc/download-microsoft-jdbc-driver-for-sql-server.md) |
| Node.js | [Node.js-Treiber, Installationsanweisungen](./node-js/step-1-configure-development-environment-for-node-js-development.md) |
| PHP | [PHP](./php/download-drivers-php-sql-server.md) |
| Python | [pyodbc, Installationsanweisungen](./python/pyodbc/step-1-configure-development-environment-for-pyodbc-python-development.md)<br />[Herunterladen des ODBC-Treibers](./odbc/download-odbc-driver-for-sql-server.md) |
| Ruby | [Ruby-Treiber, Installationsanweisungen](./ruby/step-1-configure-development-environment-for-ruby-development.md)<br />[Ruby-Downloadseite](https://rubyinstaller.org/downloads/) |
| &nbsp; | <br /> |

<a name="anchor-40-drivers-orm-access" />

## <a name="drivers-for-orm-access"></a>Treiber für den ORM-Zugriff


In der folgenden Tabelle sind Beispiele für ORM-Frameworks aufgelistet, die Clientanwendungen zum Herstellen einer Verbindung mit Microsoft SQL-Datenbanken verwenden können.


| Sprache | Download des ORM-Treibers |
| :------- | :------------------ |
| C# | [Entity Framework Core](https://docs.microsoft.com/ef/core/)<br />[Entity Framework (6.x oder höher)](https://docs.microsoft.com/ef/) |
| Java | [Hibernate ORM](https://hibernate.org/orm)|
| PHP | [Eloquent ORM, enthalten in der Laravel-Installation](https://laravel.com/docs/) |
| Node.js | [Sequelize ORM](https://docs.sequelizejs.com) |
| Python | [Django](https://www.djangoproject.com/) |
| Ruby | [Ruby on Rails](https://rubyonrails.org/) |


<a name="anchor-60-build-an-app-webpages" />

## <a name="build-an-app-webpages"></a>Webseiten zum Erstellen einer App
Über [https://aka.ms/sqldev](https://aka.ms/sqldev) gelangen Sie zu einer Reihe von Webseiten zum *Erstellen einer App*. Diese Webseiten enthalten Informationen zu zahlreichen Kombinationen aus Programmiersprache, Betriebssystem und SQL-Verbindungstreiber. Webseiten zum Erstellen einer App bieten u. a. die folgenden Informationen:

- Ausführliche Informationen zum Einstieg für jede Kombination aus Sprache, Betriebssystem und Treiber.
    - Anweisungen zum Installieren der neuesten SQL-Verbindungstreiber.
- Codebeispiele für jedes der folgenden Elemente:
    - Objektrelationale Codebeispiele.
    - ORM-Codebeispiele
    - Columnstore-Index-Demonstrationen zum Erzielen einer wesentlich schnelleren Leistung.

#### <a name="first-page-of-build-an-app-webpages"></a>Erster Bildschirm einer Webseite zum Erstellen einer App
![Screenshot des ersten Bildschirms einer Webseite zum Erstellen einer App][image-ref-163-buildanapp-webpages-first-page]

#### <a name="menu-for-java---ubuntu-of-build-an-app-webpages"></a>Menü für Java > Ubuntu auf einer Webseite zum Erstellen einer App
![Webseite zum Erstellen einer App, Menü für Java > Ubuntu][image-ref-167-buildanapp-webpages-menu-java-ubuntu]

&nbsp;

## <a name="related-links"></a>Verwandte Links
- [Codebeispiele zum Herstellen einer Verbindung mit Azure SQL-Datenbank in der Cloud mit Java und anderen Sprachen](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)

<!-- Image references -->

[image-ref-163-buildanapp-webpages-first-page]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-choose-language-g21.png
[image-ref-167-buildanapp-webpages-menu-java-ubuntu]: ./media/homepage-sql-connection-drivers/gm-aka-ms-sqldev-java-ubuntu-c31.png
