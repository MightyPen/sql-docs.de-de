---
title: Ausführen eines Beispielnotebooks | Microsoft-Dokumentation
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird gezeigt, wie Sie ein Spark-Beispielnotebook für einen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] laden und ausführen können.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4acb5c2306064da29d3537fc881dbfc3d312ad2f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73844241"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-big-data-cluster"></a>Tutorial: Ausführen eines Beispielnotebooks für einen Big Data-Cluster für SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird veranschaulicht, wie Sie in Azure Data Studio ein Notebook für einen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] laden und ausführen. Dies ermöglicht es Data Scientists und Datentechnikern, Python-, R- oder Scala-Code für den Cluster auszuführen.

> [!TIP]
> Wenn Sie möchten, können Sie ein Skript für die Befehle in diesem Tutorial herunterladen und ausführen. Anweisungen finden Sie in den [Spark-Beispielen](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) auf GitHub.

## <a id="prereqs"></a> Voraussetzungen

- [Big-Data-Tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
- [Laden von Beispieldaten in einen Big Data-Cluster von SQL Server](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>Herunterladen der Notebook-Beispieldatei

Verwenden Sie die folgenden Anweisungen, um die Notebook-Beispieldatei **spark-sql.ipynb** in Azure Data Studio zu laden.

1. Öffnen Sie eine bash-Eingabeaufforderung (Linux) oder Windows PowerShell.

1. Navigieren Sie zu dem Verzeichnis, in das Sie die Notebook-Beispieldatei herunterladen möchten.

1. Führen Sie den folgenden **curl**-Befehl aus, um die Notebook-Datei von GitHub herunterzuladen:

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-loading/transform-csv-files.ipynb' -o transform-csv-files.ipynb
   ```

## <a name="open-the-notebook"></a>Öffnen des Notebooks

In den folgenden Schritte ist gezeigt, wie Sie die Notebook-Datei in Azure Data Studio öffnen:

1. Stellen Sie in Azure Data Studio eine Verbindung mit der Masterinstanz Ihres Big-Data-Clusters her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Big-Data-Cluster](connect-to-big-data-cluster.md).

1. Doppelklicken Sie im Fenster **Server** auf die HDFS/Spark-Gatewayverbindung. Wählen Sie dann **Notebook öffnen** aus.

   ![Notebook öffnen](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. Warten Sie, bis die Felder für den **Kernel** und den Zielkontext (**Anfügen an**) ausgefüllt sind. Legen Sie den **Kernel** auf **PySpark3** fest, und legen Sie **Anfügen an** auf die IP-Adresse des Endpunkts Ihres Big Data-Clusters fest.

   ![„Kernel“ und „Anfügen an“ festlegen](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Ausführen der Notebookzellen

Sie können jede Notebookzelle ausführen, indem Sie auf das Symbol für Ausführen klicken, das sich links neben der Zelle befindet. Die Ergebnisse werden im Notebook angezeigt, nachdem das Ausführen der Zelle abgeschlossen ist.

![Notebookzelle ausführen](media/tutorial-notebook-spark/run-notebook-cell.png)

Führen Sie nacheinander jede der Zellen im Beispielnotebook aus. Weitere Informationen zur Verwendung von Notebooks mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Quellen:

- [Verwenden von Notebooks in SQL Server](notebooks-guidance.md)
- [How to manage notebooks in Azure Data Studio (Vorgehensweise: Verwalten von Notebooks in Azure Data Studio)](notebooks-how-to-manage.md)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über Notebooks:
> [!div class="nextstepaction"]
> [Weitere Informationen über Notebooks](notebooks-guidance.md)
