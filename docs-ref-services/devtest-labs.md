---
title: Azure DevTest Labs-Module für Node.js
description: Referenz zu Azure DevTest Labs-Modulen für Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "49694915"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="bd93f-103">Azure DevTest Labs-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="bd93f-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="bd93f-104">Azure DevTest Labs ist ein Dienst, der Entwicklern und Testern dabei hilft, Umgebungen in Azure schnell zu erstellen und dabei unnötigen Aufwand zu minimieren und die Kosten unter Kontrolle zu halten.</span><span class="sxs-lookup"><span data-stu-id="bd93f-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="bd93f-105">Sie können die neueste Version Ihrer Anwendung testen, indem Sie schnell Windows- und Linux-Umgebungen mit wiederverwendbaren Vorlagen und Artefakten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bd93f-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="bd93f-106">Integrieren Sie Ihre Bereitstellungspipeline einfach mit DevTest Labs, um Umgebungen bei Bedarf bereitstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="bd93f-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="bd93f-107">Skalieren Sie Ihre Auslastungstests zentral hoch, indem Sie mehrere Test-Agents bereitstellen, und erstellen Sie vorab bereitgestellte Umgebungen für Schulungen und Vorführungen.</span><span class="sxs-lookup"><span data-stu-id="bd93f-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="bd93f-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="bd93f-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bd93f-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="bd93f-109">Install the npm module</span></span>

<span data-ttu-id="bd93f-110">Installieren des npm-Moduls für Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="bd93f-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="bd93f-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bd93f-111">Example</span></span>

<span data-ttu-id="bd93f-112">Mit diesem Beispiel werden die Details eines Labs abgerufen und ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="bd93f-112">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="bd93f-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="bd93f-113">Samples</span></span>

<span data-ttu-id="bd93f-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bd93f-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
