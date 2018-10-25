---
title: Azure Analysis Services-Module für Node.js
description: Referenz zu Azure Analysis Services-Modulen für Node.js
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "49702681"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="dea75-103">Azure Analysis Services-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="dea75-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dea75-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="dea75-104">Overview</span></span>
<span data-ttu-id="dea75-105">Dieses Paket enthält ein Node.js-Modul, das die Verwaltung von Microsoft Azure Analysis Services erleichtert.</span><span class="sxs-lookup"><span data-stu-id="dea75-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="dea75-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="dea75-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dea75-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="dea75-107">Install the npm module</span></span>

<span data-ttu-id="dea75-108">Installieren des npm-Moduls für Azure Analysis Services</span><span class="sxs-lookup"><span data-stu-id="dea75-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="dea75-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="dea75-109">Example</span></span>

<span data-ttu-id="dea75-110">Mit diesem Beispiel werden alle verfügbaren Analysis Services-Server aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="dea75-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="dea75-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="dea75-111">Samples</span></span>

<span data-ttu-id="dea75-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="dea75-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
