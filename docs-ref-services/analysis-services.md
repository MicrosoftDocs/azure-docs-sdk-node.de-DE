---
title: "Azure Analysis Services-Module für Node.js"
description: "Referenz zu Azure Analysis Services-Modulen für Node.js"
keywords: Azure,SDK,API,Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="7600a-104">Azure Analysis Services-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="7600a-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7600a-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7600a-105">Overview</span></span>
<span data-ttu-id="7600a-106">Dieses Paket enthält ein Node.js-Modul, das die Verwaltung von Microsoft Azure Analysis Services erleichtert.</span><span class="sxs-lookup"><span data-stu-id="7600a-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="7600a-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="7600a-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7600a-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="7600a-108">Install the npm module</span></span>

<span data-ttu-id="7600a-109">Installieren des npm-Moduls für Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="7600a-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="7600a-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7600a-110">Example</span></span>

<span data-ttu-id="7600a-111">Mit diesem Beispiel werden alle verfügbaren Analysis Services-Server aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="7600a-111">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="7600a-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7600a-112">Samples</span></span>

<span data-ttu-id="7600a-113">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7600a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
