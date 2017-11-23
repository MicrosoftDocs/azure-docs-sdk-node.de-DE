---
title: "Azure DevTest Labs-Module für Node.js"
description: "Referenz zu Azure DevTest Labs-Modulen für Node.js"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="e2f5b-104">Azure DevTest Labs-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="e2f5b-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e2f5b-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="e2f5b-105">Overview</span></span>

<span data-ttu-id="e2f5b-106">Azure DevTest Labs ist ein Dienst, der Entwicklern und Testern dabei hilft, Umgebungen in Azure schnell zu erstellen und dabei unnötigen Aufwand zu minimieren und die Kosten unter Kontrolle zu halten.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="e2f5b-107">Sie können die neueste Version Ihrer Anwendung testen, indem Sie schnell Windows- und Linux-Umgebungen mit wiederverwendbaren Vorlagen und Artefakten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="e2f5b-108">Integrieren Sie Ihre Bereitstellungspipeline einfach mit DevTest Labs, um Umgebungen bei Bedarf bereitstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="e2f5b-109">Skalieren Sie Ihre Auslastungstests zentral hoch, indem Sie mehrere Test-Agents bereitstellen, und erstellen Sie vorab bereitgestellte Umgebungen für Schulungen und Vorführungen.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="e2f5b-110">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="e2f5b-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e2f5b-111">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="e2f5b-111">Install the npm module</span></span>

<span data-ttu-id="e2f5b-112">Installieren des npm-Moduls für Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="e2f5b-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="e2f5b-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e2f5b-113">Example</span></span>

<span data-ttu-id="e2f5b-114">Mit diesem Beispiel werden die Details eines Labs abgerufen und ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="e2f5b-114">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="e2f5b-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e2f5b-115">Samples</span></span>

<span data-ttu-id="e2f5b-116">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e2f5b-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
