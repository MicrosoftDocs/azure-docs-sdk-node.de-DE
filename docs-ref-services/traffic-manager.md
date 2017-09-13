---
title: "Azure Traffic Manager-Module für Node.js"
description: "Referenz zu Azure Traffic Manager-Modulen für Node.js"
keywords: Azure,SDK,API,Traffic Manager, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="576c2-104">Azure Traffic Manager-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="576c2-104">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="576c2-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="576c2-105">Overview</span></span>

<span data-ttu-id="576c2-106">Microsoft Azure Traffic Manager ermöglicht die Verteilung von Benutzerdatenverkehr für Dienstendpunkte in unterschiedlichen Rechenzentren.</span><span class="sxs-lookup"><span data-stu-id="576c2-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="576c2-107">Zu den von Traffic Manager unterstützten Dienstendpunkten zählen virtuelle Azure-Computer, Web-Apps und Clouddienste.</span><span class="sxs-lookup"><span data-stu-id="576c2-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="576c2-108">Darüber hinaus kann Traffic Manager auch mit externen, Azure-fremden Endpunkten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="576c2-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="576c2-109">Weitere Informationen zu [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="576c2-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="576c2-110">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="576c2-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="576c2-111">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="576c2-111">Install the npm module</span></span>

<span data-ttu-id="576c2-112">Installieren des npm-Moduls für Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="576c2-112">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="576c2-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="576c2-113">Example</span></span>

<span data-ttu-id="576c2-114">Mit diesem Beispiel werden alle Traffic Manager für eine bestimmte Ressourcengruppe aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="576c2-114">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="576c2-115">Beispiele</span><span class="sxs-lookup"><span data-stu-id="576c2-115">Samples</span></span>

<span data-ttu-id="576c2-116">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="576c2-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
