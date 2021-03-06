---
title: Hybrider Pufferpool | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/31/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: briancarrig
ms.author: brcarrig
manager: amitban
ms.openlocfilehash: c7919232bcd2c84ea58ac2e8b9d23b48cc58ee60
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76831704"
---
# <a name="hybrid-buffer-pool"></a>Hybrider Pufferpool
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In einem hybriden Pufferpool können Pufferpoolobjekte auf Datenseiten in Datenbankdateien verweisen, die sich auf persistenten Speichergeräten (persistent memory, PMEM) befinden, anstatt nur auf Kopien der Datenseiten, die im flüchtigen DRAM zwischengespeichert sind. Dieses Feature wird in [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] eingeführt.

![Hybrider Pufferpool](./media/hybrid-buffer-pool.png)

Persistente Speichergeräte sind byteadressierbar. Wenn ein PMEM-fähiges Dateisystem mit Direktzugriff (Direct Access, DAX) (z. B. XFS, EXT4 oder NTFS) verwendet wird, kann mithilfe der üblichen Dateisystem-APIs des Betriebssystems auf die Dateien im Dateisystem zugegriffen werden. Alternativ können sogenannte Lade- und Speichervorgänge für die Speicherzuordnungen der Dateien auf dem Gerät ausgeführt werden. Dies ermöglicht den PMEM-fähigen Anwendungen wie SQL Server, auf Dateien auf dem Gerät zuzugreifen, ohne den herkömmlichen Speicherstapel durchlaufen zu müssen.

Der hybride Pufferpool verwendet diese Lade- und Speichervorgänge für im Speicher abgebildete Dateien, um das PMEM-Gerät als Cache für den Pufferpool und zum Speichern von Datenbankdateien zu nutzen. Dadurch ergibt sich die außergewöhnliche Situation, dass logische und physische Lesevorgänge im Grunde genommen dasselbe sind. Persistente Speichergeräte können über den Speicherbus aufgerufen werden, genauso wie reguläres flüchtiges DRAM.

Nur nicht bearbeitete Datenseiten werden auf dem Gerät für den hybriden Pufferpool zwischengespeichert. Wenn eine Seite als geändert markiert ist, wird sie in den DRAM-Pufferpool kopiert, bevor sie schließlich zurück auf das PMEM-Gerät geschrieben und als nicht modifiziert markiert wird. Dies erfolgt bei regulären Prüfpunktvorgängen, ähnlich wie bei einem Standardblockgerät.

Die Funktion für hybriden Pufferpool ist für Windows und Linux verfügbar. Das PMEM-Gerät muss mit einem Dateisystem formatiert sein, das DAX (DirectAccess) unterstützt. Die Dateisysteme XFS, EXT4 und NTFS bieten Unterstützung für DAX. SQL Server erkennt automatisch, ob sich Datendateien auf einem entsprechend formatierten PMEM-Gerät befinden, und führt die Speicherzuordnung von Datenbankdateien beim Start aus, wenn eine neue Datenbank angefügt, wiederhergestellt oder erstellt wird.

Weitere Informationen finden Sie unter

* [Verstehen und Bereitstellen von persistentem Speicher](/windows-server/storage/storage-spaces/deploy-pmem/)
* [Konfigurieren von persistentem Speicher (PMEM) für SQL Server für Linux](../../linux/sql-server-linux-configure-pmem.md)


## <a name="enable-hybrid-buffer-pool"></a>Aktivieren des hybriden Pufferpools

Mit [!INCLUDE[sqlv15](../../includes/sssqlv15-md.md)] wird DDL (Dynamic Data Language) zum Steuern des hybriden Pufferpools eingeführt.

Im folgenden Beispiel wird der hybride Pufferpool für eine Instanz von SQL Server aktiviert:

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = ON;
```

Standardmäßig ist der hybride Pufferpool für die gesamte Instanz deaktiviert. Beachten Sie, dass die SQL Server-Instanz neu gestartet werden muss, damit die Einstellungsänderung in Kraft tritt. Ein Neustart ist erforderlich, um eine Zuordnung ausreichender Hashseiten entsprechend der PMEM-Gesamtkapazität auf dem Server zu ermöglichen.

Im folgenden Beispiel wird der hybride Pufferpool für eine bestimmte Datenbank aktiviert.

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = ON;
```

Standardmäßig ist der hybride Pufferpool für die gesamte Datenbank aktiviert.

## <a name="disable-hybrid-buffer-pool"></a>Deaktivieren des hybriden Pufferpools

Im folgenden Beispiel wird der hybride Pufferpool auf Instanzebene deaktiviert.

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED HYBRID_BUFFER_POOL = OFF;
```

Standardmäßig wird der hybride Pufferpool auf Instanzebene deaktiviert. Damit diese Änderung wirksam wird, muss die Instanz neu gestartet werden. Dadurch wird sichergestellt, dass dem Pufferpool genügend Hashseiten zugewiesen sind, da die PMEM-Kapazität auf dem Server jetzt berücksichtigt werden muss.

Im folgenden Beispiel wird der hybride Pufferpool für eine bestimmte Datenbank deaktiviert.

```sql
ALTER DATABASE <databaseName> SET MEMORY_OPTIMIZED = OFF;
```

Standardmäßig ist der hybride Pufferpool für die gesamte Datenbank aktiviert.

## <a name="view-hybrid-buffer-pool-configuration"></a>Anzeigen der Konfiguration des hybriden Pufferpools

Im folgenden Beispiel wird der aktuelle Konfigurationsstatus des hybriden Pufferpools der Instanz zurückgegeben.

```sql
SELECT * FROM
sys.server_memory_optimized_hybrid_buffer_pool_configuration;
```

Das folgende Beispiel gibt zwei Tabellen zurück:

- Die erste Tabelle zeigt den aktuellen Status der Systemkonfiguration des hybriden Pufferpools für eine Instanz von SQL Server.
- In der zweiten Tabelle sind die Datenbanken und die Einstellung auf Datenbankebene für den hybriden Pufferpool (`is_memory_optimized_enabled`) aufgeführt.

```sql
SELECT * FROM sys.configurations WHERE name = 'hybrid_buffer_pool';

SELECT name, is_memory_optimized_enabled FROM sys.databases;
```

## <a name="best-practices-for-hybrid-buffer-pool"></a>Bewährte Methoden für den hybriden Pufferpool

Verwenden Sie beim Formatieren Ihres PMEM-Geräts unter Windows die größte verfügbare Zuordnungseinheit für NTFS (2 MB in Windows Server 2019), und stellen Sie sicher, dass das Gerät für DAX (DirectAccess) formatiert wurde.

Verwenden Sie das Modell für die Speicherzuordnung mit großen Seiten, das mit [Ablaufverfolgungsflag 834](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) aktiviert werden kann. Ablaufverfolgungsflag 834 ist ein Startablaufverfolgungsflag.

Bei Verwendung des Modells für die Speicherzuordnung mit großen Seiten müssen unter Windows [gesperrte Seiten im Speicher](./enable-the-lock-pages-in-memory-option-windows.md) verwendet werden.

Dateigrößen müssen ein Vielfaches von 2 MB sein (Modulo 2 MB muss 0 (Null) sein).

Wenn die für den Server gültige Einstellung für den hybriden Pufferpool deaktiviert ist, wird das Feature von keiner Benutzerdatenbank verwendet.

Wenn die für den Server gültige Einstellung für den hybriden Pufferpool aktiviert ist, können Sie mit der für die Datenbank gültigen Einstellung das Feature für einzelne Benutzerdatenbanken deaktivieren.
