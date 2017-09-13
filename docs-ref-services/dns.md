---
title: "Azure DNS-Module für Node.js"
description: "Referenz zu anderen Azure DNS-Modulen für Node.js"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="7d50f-104">Azure DNS-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="7d50f-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="7d50f-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7d50f-105">Overview</span></span>

<span data-ttu-id="7d50f-106">Verwenden Sie Azure DNS (Domain Name System), um Ihre DNS-Domänen in Azure zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="7d50f-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="7d50f-107">Verwalten Sie Ihre DNS-Einträge mit den gleichen Anmeldeinformationen, der gleichen Abrechnung und dem gleichen Supportvertrag wie bei Ihren anderen Azure-Diensten.</span><span class="sxs-lookup"><span data-stu-id="7d50f-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="7d50f-108">Integrieren Sie Azure-basierte Dienste nahtlos in entsprechende DNS-Updates, und optimieren Sie Ihren gesamten Bereitstellungsprozess.</span><span class="sxs-lookup"><span data-stu-id="7d50f-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="7d50f-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="7d50f-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7d50f-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="7d50f-110">Install the npm module</span></span>

<span data-ttu-id="7d50f-111">Installieren des npm-Moduls für Azure DNS</span><span class="sxs-lookup"><span data-stu-id="7d50f-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="7d50f-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7d50f-112">Example</span></span>

<span data-ttu-id="7d50f-113">Mit diesem Beispiel werden die DNS-Verwaltungszonen aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="7d50f-113">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="7d50f-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7d50f-114">Samples</span></span>

<span data-ttu-id="7d50f-115">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7d50f-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
