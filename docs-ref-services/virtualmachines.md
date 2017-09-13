---
title: "Azure-VM-Module für Node.js"
description: "Referenz zu Azure-VM-Modulen für Node.js"
keywords: Azure, Node, SDK, API, virtueller Computer, VM, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Azure-VM-Module für Node.js

## <a name="overview"></a>Übersicht

Mit den Azure-Verwaltungsmodulen für Node.js können Sie neue virtuelle Windows- und Linux-Computer und VM-Skalierungsgruppen über Ihren Code definieren, konfigurieren und bereitstellen. Die Module ermöglichen Ihnen das Starten und Beenden von vorhandenen virtuellen Computern und das Anfügen bzw. Trennen von Datenträgern für beendete VMs in Ihrem Azure-Abonnement.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren Sie das Azure Compute-npm-Modul.

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie sich an Azure anmelden, einen Verwaltungsclient erstellen und alle VM-Images für den angegebenen Standort, den Publisher, das Angebot und die SKU auflisten.

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Beispiele

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
