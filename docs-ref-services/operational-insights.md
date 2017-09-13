---
title: "Azure Operational Insights-Module für Node.js"
description: "Referenz zu Azure Operational Insights-Modulen für Node.js"
keywords: Azure,SDK,API,Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="3d630-104">Azure Operational Insights-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="3d630-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="3d630-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="3d630-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="3d630-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="3d630-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3d630-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="3d630-107">Install the npm module</span></span>

<span data-ttu-id="3d630-108">Installieren des Azure Operational Insights-Moduls für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="3d630-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="3d630-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3d630-109">Example</span></span> 

<span data-ttu-id="3d630-110">Mit diesem Beispiel wird ein Client erstellt, eine Verbindung mit Operational Insights hergestellt und eine Liste der Arbeitsbereiche anhand einer bestimmten Ressourcengruppe abgerufen:</span><span class="sxs-lookup"><span data-stu-id="3d630-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="3d630-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3d630-111">Samples</span></span>

<span data-ttu-id="3d630-112">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3d630-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
