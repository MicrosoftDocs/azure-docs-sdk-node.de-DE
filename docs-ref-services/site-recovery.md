---
title: Azure Site Recovery-Module für Node.js
description: Referenz zu Azure Site Recovery-Modulen für Node.js
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: f8cddf806b921d5445cd0757b64aeb0dc5df03cf
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51053709"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="85060-103">Azure Site Recovery-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="85060-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="85060-104">Site Recovery ermöglicht die Automatisierung der Replikation von virtuellen Azure-Computern zwischen Regionen, von lokalen virtuellen Computern und physischen Servern in Azure und von lokalen Computern in einem sekundären Datencenter.</span><span class="sxs-lookup"><span data-stu-id="85060-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="85060-105">Weitere Informationen zu [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)</span><span class="sxs-lookup"><span data-stu-id="85060-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="85060-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="85060-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="85060-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="85060-107">Install the npm module</span></span>

<span data-ttu-id="85060-108">Installieren des npm-Moduls für Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="85060-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="85060-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="85060-109">Example</span></span>

<span data-ttu-id="85060-110">Mit diesem Beispiel wird der Site Recovery-Dienst für eine Ressourcengruppe aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="85060-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="85060-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="85060-111">Samples</span></span>

<span data-ttu-id="85060-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="85060-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
