---
title: Azure-Module für JavaScript
description: Übersicht über die Azure-Verwaltungsmodule und -Dienstmodule für JavaScript
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 1d97df65f12c465cf6c790d1e3c016a9ff4aa5ba
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50310967"
---
# <a name="azure-modules-for-javascript"></a><span data-ttu-id="bfa33-103">Azure-Module für JavaScript</span><span class="sxs-lookup"><span data-stu-id="bfa33-103">Azure modules for JavaScript</span></span>

<span data-ttu-id="bfa33-104">Mit den Azure-Modulen für JavaScript können Sie Azure-Ressourcen verwalten und über Ihre JavaScript-Anwendungen Verbindungen mit Diensten herstellen.</span><span class="sxs-lookup"><span data-stu-id="bfa33-104">Manage Azure resources and connect to services from your JavaScript applications with the Azure modules for JavaScript.</span></span> <span data-ttu-id="bfa33-105">Der Code ist in Form von [npm-Modulen](node-sdk-azure-install.md) für die Verwendung in Ihren Projekten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bfa33-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="bfa33-106">Verwalten von Azure-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bfa33-106">Manage Azure resources</span></span>

<span data-ttu-id="bfa33-107">Verwenden Sie die Verwaltungsmodule, um über Ihre Apps Ressourcen zu erstellen und abzufragen oder Ihre eigenen Azure-Automatisierungstools zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bfa33-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="bfa33-108">Sie können beispielsweise den folgenden Code schreiben, um mit einer vorhandenen Netzwerkschnittstelle eine Linux-VM zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="bfa33-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
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
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="bfa33-109">Die [Installationsanleitung](node-sdk-azure-install.md) enthält eine vollständige Liste mit den Modulen. Im [Artikel zu den ersten Schritten](node-sdk-azure-get-started.md) finden Sie Informationen zur Einrichtung der Authentifizierung und Ausführung von Beispielcode zum Erstellen und Aktualisieren von Ressourcen für Ihr eigenes Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="bfa33-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="bfa33-110">Herstellen einer Verbindung mit Azure-Diensten</span><span class="sxs-lookup"><span data-stu-id="bfa33-110">Connect to Azure services</span></span>

<span data-ttu-id="bfa33-111">Zusätzlich zur Verwendung der Azure-Module zum Erstellen und Verwalten von Ressourcen in Azure können Sie auch Pakete einsetzen, um Azure-Clouddienste in Ihren Apps zu verbinden und zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="bfa33-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="bfa33-112">Beispielsweise können Sie eine tabellarische SQL-Datenbank aktualisieren oder Dateien in Azure Storage hochladen.</span><span class="sxs-lookup"><span data-stu-id="bfa33-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="bfa33-113">Wählen Sie das Paket, das Sie für einen bestimmten Dienst benötigen, aus der [vollständigen Liste](node-sdk-azure-install.md) aus. Im [Entwicklercenter für JavaScript](https://azure.microsoft.com/develop/nodejs/) finden Sie Tutorials und Beispielcode zur Verwendung der Module in Ihren Apps.</span><span class="sxs-lookup"><span data-stu-id="bfa33-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [JavaScript developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="bfa33-114">So drucken Sie beispielsweise die Inhalte der einzelnen Blobs in einem Azure-Speichercontainer aus:</span><span class="sxs-lookup"><span data-stu-id="bfa33-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="bfa33-115">Beispielcode und Referenz</span><span class="sxs-lookup"><span data-stu-id="bfa33-115">Sample code and reference</span></span>

<span data-ttu-id="bfa33-116">In den folgenden Beispielen werden häufig anfallende Aufgaben für die Azure-Verwaltungsmodule behandelt, und sie enthalten Code, den Sie direkt in Ihren eigenen Apps verwenden können:</span><span class="sxs-lookup"><span data-stu-id="bfa33-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="bfa33-117">Virtuelle Computer</span><span class="sxs-lookup"><span data-stu-id="bfa33-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="bfa33-118">Web-Apps</span><span class="sxs-lookup"><span data-stu-id="bfa33-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="bfa33-119">SQL-Datenbank</span><span class="sxs-lookup"><span data-stu-id="bfa33-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="bfa33-120">Sowohl in den Dienst- als auch den Verwaltungsmodulen ist eine [Referenz](https://docs.microsoft.com/javascript/api) für alle Module verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bfa33-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="bfa33-121">Neue Funktionen, wichtige Änderungen und Migrationsanweisungen aus älteren Versionen finden Sie in den [Versionshinweisen](https://github.com/Azure/azure-sdk-for-node/releases).</span><span class="sxs-lookup"><span data-stu-id="bfa33-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>