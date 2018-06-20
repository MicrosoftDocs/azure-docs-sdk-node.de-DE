---
title: VM-Module für Node.js – Azure
description: Referenzhandbuch zu Azure-VM-Modulen für Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259842"
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
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Beispiele

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
