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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51173089"
---
# <a name="azure-modules-for-javascript"></a>Azure-Module für JavaScript

Mit den Azure-Modulen für JavaScript können Sie Azure-Ressourcen verwalten und über Ihre JavaScript-Anwendungen Verbindungen mit Diensten herstellen. Der Code ist in Form von [npm-Modulen](node-sdk-azure-install.md) für die Verwendung in Ihren Projekten verfügbar. 

## <a name="manage-azure-resources"></a>Verwalten von Azure-Ressourcen

Verwenden Sie die Verwaltungsmodule, um über Ihre Apps Ressourcen zu erstellen und abzufragen oder Ihre eigenen Azure-Automatisierungstools zu erstellen. 

Sie können beispielsweise den folgenden Code schreiben, um mit einer vorhandenen Netzwerkschnittstelle eine Linux-VM zu erstellen:

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

Die [Installationsanleitung](node-sdk-azure-install.md) enthält eine vollständige Liste mit den Modulen. Im [Artikel zu den ersten Schritten](node-sdk-azure-get-started.md) finden Sie Informationen zur Einrichtung der Authentifizierung und Ausführung von Beispielcode zum Erstellen und Aktualisieren von Ressourcen für Ihr eigenes Azure-Abonnement. 

## <a name="connect-to-azure-services"></a>Herstellen einer Verbindung mit Azure-Diensten

Zusätzlich zur Verwendung der Azure-Module zum Erstellen und Verwalten von Ressourcen in Azure können Sie auch Pakete einsetzen, um Azure-Clouddienste in Ihren Apps zu verbinden und zu nutzen. Beispielsweise können Sie eine tabellarische SQL-Datenbank aktualisieren oder Dateien in Azure Storage hochladen. Wählen Sie das Paket, das Sie für einen bestimmten Dienst benötigen, aus der [vollständigen Liste](node-sdk-azure-install.md) aus. Im [Entwicklercenter für JavaScript](https://azure.microsoft.com/develop/nodejs/) finden Sie Tutorials und Beispielcode zur Verwendung der Module in Ihren Apps.

So drucken Sie beispielsweise die Inhalte der einzelnen Blobs in einem Azure-Speichercontainer aus:

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>Beispielcode und Referenz

In den folgenden Beispielen werden häufig anfallende Aufgaben für die Azure-Verwaltungsmodule behandelt, und sie enthalten Code, den Sie direkt in Ihren eigenen Apps verwenden können:

- [Virtuelle Computer](node-samples-services-compute.md)
- [Web-Apps](node-samples-services-web-and-mobile.md)
- [SQL-Datenbank](node-samples-services-database.md)
   
Sowohl in den Dienst- als auch den Verwaltungsmodulen ist eine [Referenz](https://docs.microsoft.com/javascript/api) für alle Module verfügbar. Neue Funktionen, wichtige Änderungen und Migrationsanweisungen aus älteren Versionen finden Sie in den [Versionshinweisen](https://github.com/Azure/azure-sdk-for-node/releases).