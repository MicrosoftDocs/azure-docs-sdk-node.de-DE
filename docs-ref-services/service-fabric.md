---
title: "Azure Service Fabric-Module für Node.js"
description: "Referenz zu Azure Service Fabric-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: c855e0003a4b6f4a4d75f37b4c8480721fe0a942
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="4d3e8-103">Azure Service Fabric-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="4d3e8-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4d3e8-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="4d3e8-104">Overview</span></span>

<span data-ttu-id="4d3e8-105">Azure Service Fabric ist eine Plattform für verteilte Systeme, die das Packen, Bereitstellen und Verwalten skalierbarer und zuverlässiger Microservices und Container vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="4d3e8-106">Weitere Informationen zu [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)</span><span class="sxs-lookup"><span data-stu-id="4d3e8-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="4d3e8-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="4d3e8-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4d3e8-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="4d3e8-108">Install the npm module</span></span>

<span data-ttu-id="4d3e8-109">Installieren des npm-Moduls für Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="4d3e8-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="4d3e8-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4d3e8-110">Example</span></span>

<span data-ttu-id="4d3e8-111">In diesem Beispiel wird gezeigt, wie Sie die Cluster für ein Azure-Abonnement auflisten können:</span><span class="sxs-lookup"><span data-stu-id="4d3e8-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4d3e8-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="4d3e8-112">Samples</span></span>

<span data-ttu-id="4d3e8-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="4d3e8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
