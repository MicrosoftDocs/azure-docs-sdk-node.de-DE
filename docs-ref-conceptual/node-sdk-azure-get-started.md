---
title: Erste Schritte mit den Azure-Modulen für Node.js
description: Erste Schritte mit der Authentifizierung und Ressourcenverwaltung mit Azure-Modulen für Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: conceptual
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 73f115373c33423b7ad8895e73f5a2170b753f8f
ms.sourcegitcommit: 8c9462a8538ea3d7d3fbb27454d26755abbad001
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57327371"
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="344bd-103">Erste Schritte mit den Azure-Modulen für Node.js</span><span class="sxs-lookup"><span data-stu-id="344bd-103">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="344bd-104">In diesem Leitfaden werden die folgenden Schritte beschrieben: Installieren der Azure-Node.js-Module, Authentifizieren bei Azure mit einem Dienstprinzipal und Ausführen von Beispielcode, mit dem Ressourcen in Ihrem Azure-Abonnement erstellt werden und eine Verbindung mit Azure-Clouddiensten hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="344bd-104">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="344bd-105">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="344bd-105">Prerequisites</span></span>

- <span data-ttu-id="344bd-106">Ein Azure-Konto.</span><span class="sxs-lookup"><span data-stu-id="344bd-106">An Azure account.</span></span> <span data-ttu-id="344bd-107">Falls Sie noch kein Konto besitzen, können Sie die [kostenlose Testversion](https://azure.microsoft.com/free/) verwenden.</span><span class="sxs-lookup"><span data-stu-id="344bd-107">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="344bd-108">Node.js</span><span class="sxs-lookup"><span data-stu-id="344bd-108">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="344bd-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) oder [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="344bd-109">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="344bd-110">Vorbereiten der Umgebung</span><span class="sxs-lookup"><span data-stu-id="344bd-110">Prepare your environment</span></span>

<span data-ttu-id="344bd-111">Erstellen Sie ein neues Projekt in einem leeren Verzeichnis, und installieren Sie die folgenden npm-Module:</span><span class="sxs-lookup"><span data-stu-id="344bd-111">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="344bd-112">Einrichten der Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="344bd-112">Set up authentication</span></span>

<span data-ttu-id="344bd-113">Die Node.js-Anwendung benötigt Lese- und Schreibberechtigungen in Ihrem Azure-Abonnement, um den Beispielcode in diesem Leitfaden ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="344bd-113">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="344bd-114">Erstellen Sie einen Dienstprinzipal, und konfigurieren Sie Ihre Anwendung so, dass sie mit dessen Anmeldeinformationen ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="344bd-114">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="344bd-115">Dienstprinzipale stellen ein nicht interaktives, Ihrer Identität zugeordnetes Konto dar, dem Sie nur die Berechtigungen erteilen, die zum Ausführen Ihrer App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="344bd-115">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="344bd-116">[Erstellen Sie einen Dienstprinzipal mithilfe der Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli), und erfassen Sie die Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="344bd-116">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="344bd-117">Geben Sie im Kennwortargument anstelle von `MY_SECURE_PASSWORD` ein [sicheres Kennwort](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) an.</span><span class="sxs-lookup"><span data-stu-id="344bd-117">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

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

<span data-ttu-id="344bd-118">Exportieren Sie die Werte für *appId*, *password* und *tenant* als Umgebungsvariablen:</span><span class="sxs-lookup"><span data-stu-id="344bd-118">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="344bd-119">Rufen Sie mit [az account show](https://docs.microsoft.com/cli/azure/account#show) die ID für Ihr Abonnement ab.</span><span class="sxs-lookup"><span data-stu-id="344bd-119">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

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

<span data-ttu-id="344bd-120">Exportieren Sie die Abonnement-ID als Umgebungsvariable.</span><span class="sxs-lookup"><span data-stu-id="344bd-120">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="344bd-121">Erstellen einer virtuellen Linux-Maschine</span><span class="sxs-lookup"><span data-stu-id="344bd-121">Create a Linux virtual machine</span></span>

<span data-ttu-id="344bd-122">Erstellen Sie im aktuellen Verzeichnis eine neue Datei vom Typ *createVM.js* mit dem folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="344bd-122">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="344bd-123">Aktualisieren Sie den Wert von `adminPass` mit einem sicheren Kennwort.</span><span class="sxs-lookup"><span data-stu-id="344bd-123">Update the value of `adminPass` with a good password.</span></span>

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

<span data-ttu-id="344bd-124">Führen Sie den Code über die Befehlszeile aus:</span><span class="sxs-lookup"><span data-stu-id="344bd-124">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="344bd-125">Rufen Sie nach der Ausführung des Codes die IP des neuen virtuellen Computers ab, und melden Sie sich per SSH mithilfe des Werts für `adminPass` aus Ihrem Code an.</span><span class="sxs-lookup"><span data-stu-id="344bd-125">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="344bd-126">Schreiben eines Blobs in Azure Storage</span><span class="sxs-lookup"><span data-stu-id="344bd-126">Write a blob to Azure Storage</span></span>

<span data-ttu-id="344bd-127">Erstellen Sie im aktuellen Verzeichnis eine neue Datei vom Typ *uploadFile.js* mit dem folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="344bd-127">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

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

<span data-ttu-id="344bd-128">Führen Sie den Befehl aus, kopieren Sie die URL aus der Ausgabe, und fügen Sie sie in Ihrem Webbrowser ein, um die Datei in Azure Storage anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="344bd-128">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="344bd-129">Bereinigen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="344bd-129">Clean up resources</span></span>

<span data-ttu-id="344bd-130">Löschen Sie die Ressourcengruppe, um die in diesem Leitfahren erstellten Ressourcen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="344bd-130">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="344bd-131">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="344bd-131">Next steps</span></span>

<span data-ttu-id="344bd-132">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="344bd-132">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="344bd-133">Verweis</span><span class="sxs-lookup"><span data-stu-id="344bd-133">Reference</span></span> 

<span data-ttu-id="344bd-134">Für alle Pakete steht eine [Referenz](/javascript/api/overview/azure/) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="344bd-134">A [reference](/javascript/api/overview/azure/) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="344bd-135">Hilfe und Feedback</span><span class="sxs-lookup"><span data-stu-id="344bd-135">Get help and give feedback</span></span>

<span data-ttu-id="344bd-136">Stellen Sie in [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js) Fragen an die Community.</span><span class="sxs-lookup"><span data-stu-id="344bd-136">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="344bd-137">Melden Sie Fehler und Probleme im Zusammenhang mit den Azure-Modulen für Node.js auf der [projektspezifischen GitHub-Seite](https://github.com/Azure/azure-sdk-for-node).</span><span class="sxs-lookup"><span data-stu-id="344bd-137">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

