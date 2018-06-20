---
title: Azure Operational Insights-Module für Node.js
description: Referenz zu Azure Operational Insights-Modulen für Node.js
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 2cd948a57925954ecddc077ead727b1a7689ce0e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261969"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="92d55-103">Azure Operational Insights-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="92d55-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="92d55-104">Installieren des Azure Operational Insights-Moduls für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="92d55-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="92d55-105">Beispiel</span><span class="sxs-lookup"><span data-stu-id="92d55-105">Example</span></span> 

<span data-ttu-id="92d55-106">Mit diesem Beispiel wird ein Client erstellt, eine Verbindung mit Operational Insights hergestellt und eine Liste der Arbeitsbereiche anhand einer bestimmten Ressourcengruppe abgerufen:</span><span class="sxs-lookup"><span data-stu-id="92d55-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="92d55-107">Beispiele</span><span class="sxs-lookup"><span data-stu-id="92d55-107">Samples</span></span>

<span data-ttu-id="92d55-108">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="92d55-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
