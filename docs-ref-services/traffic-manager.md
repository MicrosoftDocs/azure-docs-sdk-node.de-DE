---
title: Azure Traffic Manager-Module für Node.js
description: Referenz zu Azure Traffic Manager-Modulen für Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 904a6693f557b90f5a1eeeea2367b56f8dfe3ff1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="ed58a-103">Azure Traffic Manager-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="ed58a-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ed58a-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="ed58a-104">Overview</span></span>

<span data-ttu-id="ed58a-105">Microsoft Azure Traffic Manager ermöglicht die Verteilung von Benutzerdatenverkehr für Dienstendpunkte in unterschiedlichen Rechenzentren.</span><span class="sxs-lookup"><span data-stu-id="ed58a-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="ed58a-106">Zu den von Traffic Manager unterstützten Dienstendpunkten zählen virtuelle Azure-Computer, Web-Apps und Clouddienste.</span><span class="sxs-lookup"><span data-stu-id="ed58a-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="ed58a-107">Darüber hinaus kann Traffic Manager auch mit externen, Azure-fremden Endpunkten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ed58a-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="ed58a-108">Weitere Informationen zu [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="ed58a-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="ed58a-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="ed58a-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ed58a-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="ed58a-110">Install the npm module</span></span>

<span data-ttu-id="ed58a-111">Installieren des npm-Moduls für Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="ed58a-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="ed58a-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ed58a-112">Example</span></span>

<span data-ttu-id="ed58a-113">Mit diesem Beispiel werden alle Traffic Manager für eine bestimmte Ressourcengruppe aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="ed58a-113">This example lists all Traffic Managers for a given resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ed58a-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ed58a-114">Samples</span></span>

<span data-ttu-id="ed58a-115">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ed58a-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
