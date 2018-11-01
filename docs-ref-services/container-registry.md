---
title: Azure Container Registry-Module für Node.js
description: Referenz zu Azure Container Registry-Modulen für Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406396"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="a0aff-103">Azure Container Registry-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="a0aff-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="a0aff-104">Azure Container Registry ist ein verwalteter Dienst vom Typ „Docker-Registrierung“, der auf Version 2.0 der Open Source-Docker-Registrierung basiert.</span><span class="sxs-lookup"><span data-stu-id="a0aff-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="a0aff-105">Erstellen und verwalten Sie Azure-Containerregistrierungen, um Ihre privaten Docker-Containerimages zu speichern und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a0aff-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="a0aff-106">Verwenden Sie Containerregistrierungen in Azure mit Ihren vorhandenen Containerentwicklungs- und Bereitstellungspipelines, und nutzen Sie das umfangreiche Wissen der Docker-Community.</span><span class="sxs-lookup"><span data-stu-id="a0aff-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="a0aff-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="a0aff-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a0aff-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="a0aff-108">Install the npm module</span></span>

<span data-ttu-id="a0aff-109">Installieren des npm-Moduls für Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="a0aff-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="a0aff-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a0aff-110">Example</span></span>

<span data-ttu-id="a0aff-111">Mit diesem Beispiel wird eine Liste der verfügbaren Container abgerufen:</span><span class="sxs-lookup"><span data-stu-id="a0aff-111">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="a0aff-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a0aff-112">Samples</span></span>

<span data-ttu-id="a0aff-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a0aff-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
