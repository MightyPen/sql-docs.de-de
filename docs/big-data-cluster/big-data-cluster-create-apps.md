---
title: Bereitstellen von Anwendungen mit azdata
titleSuffix: SQL Server Big Data Clusters
description: Stellen Sie ein Python- oder R-Skript als Anwendung in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] bereit.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 33b5bf6061e9168fd150adcb4a7ccf29302bce63
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253148"
---
# <a name="how-to-deploy-an-app-on-big-data-clusters-2019"></a>Bereitstellen einer App in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie R- und Python-Skripts als Anwendung in einem SQL Server 2019-Big Data-Cluster bereitstellen und verwalten.

## <a name="whats-new-and-improved"></a>Neuerungen und Verbesserungen

- Ein einzelnes Befehlszeilen-Hilfsprogramm zum Verwalten von Cluster und App.
- Vereinfachte App-Bereitstellung bei gleichzeitiger Bereitstellung einer differenzierten Steuerung durch Spezifikationsdateien.
- Unterstützung für das Hosting zusätzlicher Anwendungstypen: SSIS und MLeap
- [Visual Studio Code-Erweiterung](app-deployment-extension.md) zum Verwalten der Anwendungsbereitstellung

Anwendungen werden mit dem `azdata`-Befehlszeilen-Hilfsprogramm bereitgestellt und verwaltet. Dieser Artikel enthält Beispiele für die Bereitstellung von Apps über die Befehlszeile. Weitere Informationen zur Verwendung in Visual Studio Code finden Sie unter [Visual Studio Code-Erweiterung](app-deployment-extension.md).

Die folgenden Typen von Apps werden unterstützt:
- R- und Python-Apps (Funktionen, Modelle und Apps)
- MLeap Serving
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Voraussetzungen

- [SQL Server 2019: Big Data-Cluster](deployment-guidance.md)
- [Befehlszeilen-Hilfsprogramm „azdata“](deploy-install-azdata.md)

## <a name="capabilities"></a>Funktionen

In SQL Server 2019 können Sie Ihre Anwendung erstellen, löschen, beschreiben, initialisieren, auflisten und aktualisieren. In der folgenden Tabelle werden die Befehle für die Anwendungsbereitstellung beschrieben, die Sie mit **azdata** verwenden können.

|Get-Help |Beschreibung |
|:---|:---|
|`azdata login` | Anmelden bei einem Big Data-Cluster für SQL Server |
|`azdata app create` | Erstellen einer Anwendung. |
|`azdata app delete` | Löschen einer Anwendung. |
|`azdata app describe` | Beschreiben einer Anwendung. |
|`azdata app init` | Starten eines neuen Anwendungsgerüsts. |
|`azdata app list` | Auflisten von Anwendungen. |
|`azdata app run` | Ausführen einer Anwendung. |
|`azdata app update`| Aktualisieren einer Anwendung. |

Mit dem Parameter `--help` können Sie wie im folgenden Beispiel Hilfe erhalten:

```bash
azdata app create --help
```

In den folgenden Abschnitten werden diese Parameter eingehender beschrieben.

## <a name="sign-in"></a>Anmelden

Bevor Sie Anwendungen bereitstellen oder mit ihnen interagieren, melden Sie sich zunächst mit dem `azdata login`-Befehl bei Ihrem SQL Server-Big Data-Cluster an. Geben Sie die externe IP-Adresse des `controller-svc-external`-Diensts (z.B. `https://ip-address:30080`) zusammen mit dem Benutzernamen und dem Kennwort für den Cluster an.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>AKS

Wenn Sie AKS verwenden, müssen Sie den folgenden Befehl ausführen, um die IP-Adresse des `controller-svc-external`-Diensts zu erhalten, indem Sie diesen Befehl in einem Bash-oder CMD-Fenster ausführen:


```bash
kubectl get svc controller-svc-external -n <name of your big data cluster>
```

## <a name="kubernetes-clusters-created-with-kubeadm"></a>Mit kubeadm erstellte Kubernetes-Cluster

Führen Sie folgenden Befehl aus, um die IP-Adresse für die Anmeldung beim Cluster abzurufen.

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Erstellen einer App

Verwenden Sie zum Erstellen einer Anwendung `azdata` mit dem `app create`-Befehl. Diese Dateien befinden sich lokal auf dem Computer, auf dem Sie die App erstellen.

Verwenden Sie die folgende Syntax, um eine neue App im Big Data-Cluster zu erstellen:

```bash
azdata app create --spec <directory containing spec file>
```

Der Befehl könnte z.B. wie folgt aussehen:

```bash
azdata app create --spec ./addpy
```

Dabei wird vorausgesetzt, dass Sie die Anwendung im `addpy`-Ordner gespeichert haben. Dieser Ordner sollte auch eine Spezifikationsdatei für die Anwendung mit dem Namen `spec.yaml` enthalten. Auf der Seite [Anwendungsbereitstellung](concept-application-deployment.md) finden Sie weitere Informationen zur `spec.yaml`-Datei.

Um diese Beispiel-App bereitzustellen, erstellen Sie die folgenden Dateien in einem Verzeichnis mit dem Namen `addpy`:

- `add.py`. Kopieren Sie den folgenden Python-Code in diese Datei:
   ```py
   #add.py
  def add(x, y):
    result = x+y
    return result
  result=add(x,y)
   ```
- `spec.yaml`. Kopieren Sie den folgenden Code in diese Datei:
   ```yaml
   #spec.yaml
   name: add-app #name of your python script
   version: v1  #version of the app
   runtime: Python #the language this app uses (R or Python)
   src: ./add.py #full path to the location of the app
   entrypoint: add #the function that will be called upon execution
   replicas: 1  #number of replicas needed
   poolsize: 1  #the pool size that you need your app to scale
   inputs:  #input parameters that the app expects and the type
     x: int
     y: int
   output: #output parameter the app expects and the type
     result: int
   ```

Führen Sie anschließend den folgenden Befehl aus:

```bash
azdata app create --spec ./addpy
```

Mithilfe des list-Befehls können Sie überprüfen, ob die App bereitgestellt wurde:

```bash
azdata app list
```

Wenn die Bereitstellung nicht fertiggestellt ist, sollte für `state` wie im folgenden Beispiel `WaitingforCreate` angezeigt werden:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

Nach erfolgreicher Bereitstellung sollte `state` in den `Ready`-Status wechseln:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Auflisten einer App

Sie können mit dem `app list`-Befehl alle erfolgreich erstellten Apps auflisten.

Der folgende Befehl listet alle verfügbaren Anwendungen in Ihrem Big Data-Cluster auf:

```bash
azdata app list
```

Wenn Sie einen Namen und eine Version angeben, werden diese spezifische App und deren Status („Wird erstellt“ oder „Bereit“) aufgelistet:

```bash
azdata app list --name <app_name> --version <app_version>
```

Dieser Befehl wird im folgenden Beispiel veranschaulicht:

```bash
azdata app list --name add-app --version v1
```

Die Ausgabe sollte etwa folgendem Beispiel entsprechen:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Ausführen einer App

Wenn sich die App in einem `Ready`-Status befindet, können Sie sie verwenden, indem Sie sie mit den angegebenen Eingabeparametern ausführen. Verwenden Sie die folgende Syntax zum Ausführen einer App:

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Der folgende Beispielbefehl veranschaulicht den run-Befehl:

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Wenn die Ausführung erfolgreich war, sollte die Ausgabe angezeigt werden, wie Sie beim Erstellen der App angegeben haben. Im Folgenden finden Sie ein Beispiel.

```json
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```

## <a name="create-an-app-skeleton"></a>Erstellen eines App-Gerüsts

Der init-Befehl bietet ein Gerüst mit den relevanten Artefakten, die für die Bereitstellung einer App erforderlich sind. Im folgenden Beispiel wird mit dem entsprechenden Befehl „hello“ erstellt.

```bash
azdata app init --name hello --version v1 --template python
```

„hello“ ist der Name des erstellten Ordners.  Sie können mit `cd` in das Verzeichnis wechseln und die generierten Dateien im Ordner überprüfen. „spec.yaml“ definiert die App, z. B. deren Name, Version und Quellcode. Sie können die Spezifikation bearbeiten, um den Namen, die Version, die Eingabe und die Ausgaben zu ändern.

Im Folgenden finden Sie eine Beispielausgabe des Befehls „init“, die im Ordner enthalten ist.

```
hello.py
run-spec.yaml
spec.yaml
```

## <a name="describe-an-app"></a>Beschreiben einer Anwendung

Der describe-Befehl stellt ausführliche Informationen zur App bereit, darunter auch den Endpunkt in Ihrem Cluster. Dieser wird in der Regel von einem App-Entwickler dazu verwendet, eine App mithilfe des Swagger-Clients zu erstellen und mithilfe des Webdiensts RESTful mit der App zu interagieren. Weitere Informationen finden Sie unter [Nutzen von Anwendungen auf Big Data-Clustern](big-data-cluster-consume-apps.md).

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30080/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30080/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

## <a name="delete-an-app"></a>Löschen einer App

Verwenden Sie die folgende Syntax, um eine App aus Ihrem Big Data-Cluster zu löschen:

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Nächste Schritte

Im Artikel [Nutzen von Anwendungen auf Big Data-Clustern](big-data-cluster-consume-apps.md) erfahren Sie, wie Sie Apps, die in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] bereitgestellt wurden, in Ihre eigenen Anwendungen integrieren können. Weitere Beispiele finden Sie außerdem unter den [Beispielen zur App-Bereitstellung](https://aka.ms/sql-app-deploy).

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
