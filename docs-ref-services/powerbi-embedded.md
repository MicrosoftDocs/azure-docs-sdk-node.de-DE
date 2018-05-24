---
title: Azure Power BI Embedded-Module für Node.js
description: Referenz zu Azure Power BI Embedded-Modulen für Node.js
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 4d0a1ebf75591a9a3575172f325309ddbac7885c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="90619-103">Azure Power BI Embedded-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="90619-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="90619-104">Mit dem Power BI Embedded-Dienst von Azure können Sie Power BI-Berichte direkt in Ihre Node-Anwendung integrieren, um Diagramme und Berichte zu erstellen oder zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="90619-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="90619-105">Weitere Informationen zu [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)</span><span class="sxs-lookup"><span data-stu-id="90619-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="90619-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="90619-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="90619-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="90619-107">Install the npm module</span></span>

<span data-ttu-id="90619-108">Installieren des npm-Moduls für Azure Power BI</span><span class="sxs-lookup"><span data-stu-id="90619-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="90619-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="90619-109">Example</span></span>

<span data-ttu-id="90619-110">Mit diesem Beispiel wird eine Arbeitsbereichssammlung in einer vorhandenen Ressourcengruppe erstellt:</span><span class="sxs-lookup"><span data-stu-id="90619-110">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="90619-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="90619-111">Samples</span></span>

<span data-ttu-id="90619-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="90619-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
