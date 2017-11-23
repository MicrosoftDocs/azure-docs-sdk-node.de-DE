---
title: "Azure Site Recovery-Module für Node.js"
description: "Referenz zu Azure Site Recovery-Modulen für Node.js"
keywords: Azure,SDK,API,Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="c6f5a-104">Azure Site Recovery-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="c6f5a-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c6f5a-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c6f5a-105">Overview</span></span>

<span data-ttu-id="c6f5a-106">Site Recovery ermöglicht die Automatisierung der Replikation von virtuellen Azure-Computern zwischen Regionen, von lokalen virtuellen Computern und physischen Servern in Azure und von lokalen Computern in einem sekundären Datencenter.</span><span class="sxs-lookup"><span data-stu-id="c6f5a-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="c6f5a-107">Weitere Informationen zu [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)</span><span class="sxs-lookup"><span data-stu-id="c6f5a-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="c6f5a-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="c6f5a-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c6f5a-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="c6f5a-109">Install the npm module</span></span>

<span data-ttu-id="c6f5a-110">Installieren des npm-Moduls für Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="c6f5a-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="c6f5a-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c6f5a-111">Example</span></span>

<span data-ttu-id="c6f5a-112">Mit diesem Beispiel wird der Site Recovery-Dienst für eine Ressourcengruppe aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="c6f5a-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="c6f5a-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c6f5a-113">Samples</span></span>

<span data-ttu-id="c6f5a-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c6f5a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
