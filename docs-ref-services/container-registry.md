---
title: "Azure Container Registry-Module für Node.js"
description: "Referenz zu Azure Container Registry-Modulen für Node.js"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="bbadf-104">Azure Container Registry-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="bbadf-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bbadf-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="bbadf-105">Overview</span></span>

<span data-ttu-id="bbadf-106">Azure Container Registry ist ein verwalteter Dienst vom Typ „Docker-Registrierung“, der auf Version 2.0 der Open Source-Docker-Registrierung basiert.</span><span class="sxs-lookup"><span data-stu-id="bbadf-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="bbadf-107">Erstellen und verwalten Sie Azure-Containerregistrierungen, um Ihre privaten Docker-Containerimages zu speichern und zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="bbadf-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="bbadf-108">Verwenden Sie Containerregistrierungen in Azure mit Ihren vorhandenen Containerentwicklungs- und Bereitstellungspipelines, und nutzen Sie das umfangreiche Wissen der Docker-Community.</span><span class="sxs-lookup"><span data-stu-id="bbadf-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="bbadf-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="bbadf-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bbadf-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="bbadf-110">Install the npm module</span></span>

<span data-ttu-id="bbadf-111">Installieren des npm-Moduls für Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="bbadf-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="bbadf-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bbadf-112">Example</span></span>

<span data-ttu-id="bbadf-113">Mit diesem Beispiel wird eine Liste der verfügbaren Container abgerufen:</span><span class="sxs-lookup"><span data-stu-id="bbadf-113">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="bbadf-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="bbadf-114">Samples</span></span>

<span data-ttu-id="bbadf-115">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bbadf-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
