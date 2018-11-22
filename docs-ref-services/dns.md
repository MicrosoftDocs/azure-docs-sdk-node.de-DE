---
title: Azure DNS-Module für Node.js
description: Referenz zu anderen Azure DNS-Modulen für Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52106328"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="f8059-103">Azure DNS-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="f8059-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="f8059-104">Verwenden Sie Azure DNS (Domain Name System), um Ihre DNS-Domänen in Azure zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="f8059-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="f8059-105">Verwalten Sie Ihre DNS-Einträge mit den gleichen Anmeldeinformationen, der gleichen Abrechnung und dem gleichen Supportvertrag wie bei Ihren anderen Azure-Diensten.</span><span class="sxs-lookup"><span data-stu-id="f8059-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="f8059-106">Integrieren Sie Azure-basierte Dienste nahtlos in entsprechende DNS-Updates, und optimieren Sie Ihren gesamten Bereitstellungsprozess.</span><span class="sxs-lookup"><span data-stu-id="f8059-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="f8059-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="f8059-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f8059-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="f8059-108">Install the npm module</span></span>

<span data-ttu-id="f8059-109">Installieren des npm-Moduls für Azure DNS</span><span class="sxs-lookup"><span data-stu-id="f8059-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="f8059-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f8059-110">Example</span></span>

<span data-ttu-id="f8059-111">Mit diesem Beispiel werden die DNS-Verwaltungszonen aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="f8059-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f8059-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f8059-112">Samples</span></span>

<span data-ttu-id="f8059-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f8059-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
