---
title: Erste Schritte mit den Azure-Modulen für Node.js
description: Erste Schritte mit der Authentifizierung und Ressourcenverwaltung mit Azure-Modulen für Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 072574c70b658806cd998dc0af8a81be3ea56bb4
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a>Erste Schritte mit den Azure-Modulen für Node.js

In diesem Leitfaden werden die folgenden Schritte beschrieben: Installieren der Azure-Node.js-Module, Authentifizieren bei Azure mit einem Dienstprinzipal und Ausführen von Beispielcode, mit dem Ressourcen in Ihrem Azure-Abonnement erstellt werden und eine Verbindung mit Azure-Clouddiensten hergestellt wird.

## <a name="prerequisites"></a>Voraussetzungen

- Ein Azure-Konto. Falls Sie noch kein Konto besitzen, können Sie die [kostenlose Testversion](https://azure.microsoft.com/free/) verwenden.
- [Node.js](https://nodejs.org)
- [Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) oder [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a>Vorbereiten der Umgebung

Erstellen Sie ein neues Projekt in einem leeren Verzeichnis, und installieren Sie die folgenden npm-Module:

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a>Einrichten der Authentifizierung

Die Node.js-Anwendung benötigt Lese- und Schreibberechtigungen in Ihrem Azure-Abonnement, um den Beispielcode in diesem Leitfaden ausführen zu können. Erstellen Sie einen Dienstprinzipal, und konfigurieren Sie Ihre Anwendung so, dass sie mit dessen Anmeldeinformationen ausgeführt wird. Dienstprinzipale stellen ein nicht interaktives, Ihrer Identität zugeordnetes Konto dar, dem Sie nur die Berechtigungen erteilen, die zum Ausführen Ihrer App erforderlich sind.

[Erstellen Sie einen Dienstprinzipal mithilfe der Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli), und erfassen Sie die Ausgabe. Geben Sie im Kennwortargument anstelle von `MY_SECURE_PASSWORD` ein [sicheres Kennwort](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) an.

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

Exportieren Sie die Werte für *appId*, *password* und *tenant* als Umgebungsvariablen:

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

Rufen Sie mit [az account show](https://docs.microsoft.com/cli/azure/account#show) die ID für Ihr Abonnement ab.

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

Exportieren Sie die Abonnement-ID als Umgebungsvariable.

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a>Erstellen einer virtuellen Linux-Maschine

Erstellen Sie im aktuellen Verzeichnis eine neue Datei vom Typ *createVM.js* mit dem folgenden Code. Aktualisieren Sie den Wert von `adminPass` mit einem sicheren Kennwort.

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
                        primary: true
                    }
                ]
            },
            storageProfile: {
                imageReference: {
                    publisher: 'Canonical',
                    offer: 'UbuntuServer',
                    sku: '16.04-LTS',
                    version: 'latest'
                },
            }
        };

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

Führen Sie den Code über die Befehlszeile aus:

```bash
node createVM.js
```

Rufen Sie nach der Ausführung des Codes die IP des neuen virtuellen Computers ab, und melden Sie sich per SSH mithilfe des Werts für `adminPass` aus Ihrem Code an.

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a>Schreiben eines Blobs in Azure Storage

Erstellen Sie im aktuellen Verzeichnis eine neue Datei vom Typ *uploadFile.js* mit dem folgenden Code:

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

Führen Sie den Befehl aus, kopieren Sie die URL aus der Ausgabe, und fügen Sie sie in Ihrem Webbrowser ein, um die Datei in Azure Storage anzuzeigen:

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Löschen Sie die Ressourcengruppe, um die in diesem Leitfahren erstellten Ressourcen zu entfernen.

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.

## <a name="reference"></a>Verweis 

Für alle Pakete steht eine [Referenz](/javascript/api/overview/azure/) zur Verfügung.

## <a name="get-help-and-give-feedback"></a>Hilfe und Feedback

Stellen Sie in [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js) Fragen an die Community. Melden Sie Fehler und Probleme im Zusammenhang mit den Azure-Modulen für Node.js auf der [projektspezifischen GitHub-Seite](https://github.com/Azure/azure-sdk-for-node).

