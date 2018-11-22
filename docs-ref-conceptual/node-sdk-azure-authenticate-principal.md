---
title: Erstellen eines Azure-Dienstprinzipals mit Node.js
description: Erfahren Sie, wie Sie die Dienstprinzipalauthentifizierung über Node.js verwenden.
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 98d52e21332138512d40ff2de9f5d3388fa596e4
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52140825"
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>Erstellen eines Azure-Dienstprinzipals mit Node.js 

Wenn eine App Zugriff auf Ressourcen benötigt, können Sie eine Identität für die App einrichten und sie mit ihren eigenen Anmeldeinformationen authentifizieren. Diese Identität wird als *Dienstprinzipal* bezeichnet. Im Grunde erstellen Sie für Ihr Azure Active Directory-Konto Schlüssel, die Sie an das SDK übergeben, um eine Authentifizierung ohne Benutzereingriff oder die Eingabe von Benutzer/Kennwort zu ermöglichen.

Der Dienstprinzipal ermöglicht Folgendes:
- Sie können der App-Identität Berechtigungen zuweisen, die sich von Ihren eigenen Berechtigungen unterscheiden. In der Regel sind diese Berechtigungen genau auf die Aufgaben der App beschränkt.
- Sie können ein Zertifikat für die Authentifizierung beim Ausführen eines unbeaufsichtigten Skripts verwenden.

In diesem Thema werden drei Methoden zum Erstellen eines Dienstprinzipals erläutert.

- Azure-Portal
- Azure CLI 2.0
- Azure SDK für Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>Erstellen eines Dienstprinzipals mit dem Azure-Portal

Führen Sie die im Thema [Erstellen einer Azure Active Directory-Anwendung und eines Dienstprinzipals mit Ressourcenzugriff mithilfe des Portals](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/) beschriebenen Schritte aus, um den Dienstprinzipal zu erstellen.

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>Erstellen eines Dienstprinzipals mit der Azure CLI 2.0

Bei der Erstellung eines Dienstprinzipals mithilfe der [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) werden die folgenden Schritte ausgeführt:

1. Laden Sie die [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) herunter.

2. Öffnen Sie ein Terminalfenster.

3. Geben Sie den folgenden Befehl ein, um den Anmeldeprozess zu starten:

    ```shell
    $ az login
    ```

4. Durch den Aufruf von `az login` werden eine URL und ein Code zurückgegeben. Navigieren Sie zur angegebenen URL, geben Sie den Code ein, und melden Sie sich mit Ihrer Azure-Identität an. (Dies geschieht unter Umständen automatisch, wenn Sie bereits angemeldet sind.) Sie können dann über die CLI auf Ihr Konto zugreifen.

5. Rufen Sie Ihr Abonnement und die Mandanten-ID ab:

    ```shell
    $ az account list
    ```

    Nachfolgend sehen Sie ein Beispiel für die Ausgabe:

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    **Notieren Sie die Abonnement-ID, da sie in Schritt 7 verwendet wird.**

6. Erstellen Sie einen Dienstprinzipal, um ein JSON-Objekt mit den anderen Informationen abzurufen, die Sie für die Authentifizierung mit Azure benötigen.

    ```shell
    $ az ad sp create-for-rbac
    ```

    Nachfolgend sehen Sie ein Beispiel für die Ausgabe:

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **Notieren Sie sich die Werte für Mandant, Name und Kennwort, da sie in Schritt 7 verwendet werden.**

7. Richten Sie die Umgebungsvariablen ein. Ersetzen Sie dabei die Platzhalter „&lt;subscriptionId>“, „&lt;tenant>“, „&lt;name>“ und „&lt;password>“ durch die in den Schritten 4 und 5 abgerufenen Werte. 

    **Verwenden von Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **Mithilfe von PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>Erstellen eines Dienstprinzipals mit dem Azure SDK für Node.js

Verwenden Sie zum programmgesteuerten Erstellen eines Dienstprinzipals mit JavaScript das [ServicePrincipal-Skript](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).   

## <a name="using-the-service-principal"></a>Verwenden des Dienstprinzipals

Nach der Erstellung des Dienstprinzipals veranschaulicht der folgende JavaScript-Codeausschnitt, wie Sie die Dienstprinzipalschlüssel für die Authentifizierung mit dem Azure SDK für Node.js verwenden. Passen Sie die folgenden Platzhalter an: „&lt;clientId or appId>“, „&lt;secret or password>“ und „&lt;domain or tenant>“.

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
