---
title: "Azure Virtual Network-Module für Node.js"
description: "Referenz zu Azure Virtual Network-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: f073c700c8df7f7aa05c93d725051d3a9976bebc
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Azure Virtual Network-Module für Node.js

## <a name="overview"></a>Übersicht

Mit dem Dienst für das virtuelle Azure-Netzwerk (Azure Virtual Network) können Sie Azure-Ressourcen über virtuelle Netzwerke (VNets) sicher miteinander verbinden. Ein VNet ist eine Darstellung Ihres eigenen Netzwerks in der Cloud. Bei einem VNet handelt es sich um eine logische Isolation von der dedizierten Azure-Cloud für Ihr Abonnement. Sie können VNets auch mit Ihrem lokalen Netzwerk verbinden.

Weitere Informationen zu [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure Virtual Network

```bash
npm install azure-arm-network
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird die Liste der virtuellen Netzwerke abgerufen und ausgegeben:

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
