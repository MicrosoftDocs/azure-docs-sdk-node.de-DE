---
title: Azure Virtual Network-Module für Node.js
description: Referenz zu Azure Virtual Network-Modulen für Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 456839dbecb9ddd1ad0d4b3f8aa7570a04c100b1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260699"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="c3efc-103">Azure Virtual Network-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="c3efc-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c3efc-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c3efc-104">Overview</span></span>

<span data-ttu-id="c3efc-105">Mit dem Dienst für das virtuelle Azure-Netzwerk (Azure Virtual Network) können Sie Azure-Ressourcen über virtuelle Netzwerke (VNets) sicher miteinander verbinden.</span><span class="sxs-lookup"><span data-stu-id="c3efc-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="c3efc-106">Ein VNet ist eine Darstellung Ihres eigenen Netzwerks in der Cloud.</span><span class="sxs-lookup"><span data-stu-id="c3efc-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="c3efc-107">Bei einem VNet handelt es sich um eine logische Isolation von der dedizierten Azure-Cloud für Ihr Abonnement.</span><span class="sxs-lookup"><span data-stu-id="c3efc-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="c3efc-108">Sie können VNets auch mit Ihrem lokalen Netzwerk verbinden.</span><span class="sxs-lookup"><span data-stu-id="c3efc-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="c3efc-109">Weitere Informationen zu [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)</span><span class="sxs-lookup"><span data-stu-id="c3efc-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="c3efc-110">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="c3efc-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c3efc-111">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="c3efc-111">Install the npm module</span></span>

<span data-ttu-id="c3efc-112">Installieren des npm-Moduls für Azure Virtual Network</span><span class="sxs-lookup"><span data-stu-id="c3efc-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="c3efc-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c3efc-113">Example</span></span>

<span data-ttu-id="c3efc-114">Mit diesem Beispiel wird die Liste der virtuellen Netzwerke abgerufen und ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="c3efc-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="c3efc-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c3efc-115">Samples</span></span>

<span data-ttu-id="c3efc-116">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c3efc-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
