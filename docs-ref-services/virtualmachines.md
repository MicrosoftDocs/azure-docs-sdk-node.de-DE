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
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="42fb7-104">Azure-VM-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="42fb7-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="42fb7-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="42fb7-105">Overview</span></span>

<span data-ttu-id="42fb7-106">Mit den Azure-Verwaltungsmodulen für Node.js können Sie neue virtuelle Windows- und Linux-Computer und VM-Skalierungsgruppen über Ihren Code definieren, konfigurieren und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="42fb7-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="42fb7-107">Die Module ermöglichen Ihnen das Starten und Beenden von vorhandenen virtuellen Computern und das Anfügen bzw. Trennen von Datenträgern für beendete VMs in Ihrem Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="42fb7-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="42fb7-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="42fb7-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="42fb7-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="42fb7-109">Install the npm module</span></span>

<span data-ttu-id="42fb7-110">Installieren Sie das Azure Compute-npm-Modul.</span><span class="sxs-lookup"><span data-stu-id="42fb7-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="42fb7-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="42fb7-111">Example</span></span>

<span data-ttu-id="42fb7-112">Im folgenden Beispiel wird veranschaulicht, wie Sie sich an Azure anmelden, einen Verwaltungsclient erstellen und alle VM-Images für den angegebenen Standort, den Publisher, das Angebot und die SKU auflisten.</span><span class="sxs-lookup"><span data-stu-id="42fb7-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

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

## <a name="samples"></a><span data-ttu-id="42fb7-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="42fb7-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="42fb7-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="42fb7-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
