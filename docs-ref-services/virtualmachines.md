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
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="81d4f-103">Azure-VM-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="81d4f-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="81d4f-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="81d4f-104">Overview</span></span>

<span data-ttu-id="81d4f-105">Mit den Azure-Verwaltungsmodulen für Node.js können Sie neue virtuelle Windows- und Linux-Computer und VM-Skalierungsgruppen über Ihren Code definieren, konfigurieren und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="81d4f-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="81d4f-106">Die Module ermöglichen Ihnen das Starten und Beenden von vorhandenen virtuellen Computern und das Anfügen bzw. Trennen von Datenträgern für beendete VMs in Ihrem Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="81d4f-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="81d4f-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="81d4f-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="81d4f-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="81d4f-108">Install the npm module</span></span>

<span data-ttu-id="81d4f-109">Installieren Sie das Azure Compute-npm-Modul.</span><span class="sxs-lookup"><span data-stu-id="81d4f-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="81d4f-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="81d4f-110">Example</span></span>

<span data-ttu-id="81d4f-111">Im folgenden Beispiel wird veranschaulicht, wie Sie sich an Azure anmelden, einen Verwaltungsclient erstellen und alle VM-Images für den angegebenen Standort, den Publisher, das Angebot und die SKU auflisten.</span><span class="sxs-lookup"><span data-stu-id="81d4f-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

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

## <a name="samples"></a><span data-ttu-id="81d4f-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="81d4f-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="81d4f-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="81d4f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
