---
title: "Azure Service Fabric-Module für Node.js"
description: "Referenz zu Azure Service Fabric-Modulen für Node.js"
keywords: Azure,SDK,API,Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="80124-104">Azure Service Fabric-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="80124-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="80124-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="80124-105">Overview</span></span>

<span data-ttu-id="80124-106">Azure Service Fabric ist eine Plattform für verteilte Systeme, die das Packen, Bereitstellen und Verwalten skalierbarer und zuverlässiger Microservices und Container vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="80124-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="80124-107">Weitere Informationen zu [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)</span><span class="sxs-lookup"><span data-stu-id="80124-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="80124-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="80124-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="80124-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="80124-109">Install the npm module</span></span>

<span data-ttu-id="80124-110">Installieren des npm-Moduls für Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="80124-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="80124-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="80124-111">Example</span></span>

<span data-ttu-id="80124-112">In diesem Beispiel wird gezeigt, wie Sie die Cluster für ein Azure-Abonnement auflisten können:</span><span class="sxs-lookup"><span data-stu-id="80124-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="80124-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="80124-113">Samples</span></span>

<span data-ttu-id="80124-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="80124-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
