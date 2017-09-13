---
title: "Azure-Dienstzuordnungsmodule für Node.js"
description: "Referenz zu Azure-Dienstzuordnungsmodulen für Node.js"
keywords: Azure,SDK,API,Dienstzuordnung, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="a7150-104">Azure-Dienstzuordnungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="a7150-104">Azure Service Map modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a7150-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="a7150-105">Overview</span></span>

<span data-ttu-id="a7150-106">Service Map ermittelt automatisch Anwendungskomponenten auf Windows- und Linux-Systemen und stellt die Kommunikation zwischen Diensten dar.</span><span class="sxs-lookup"><span data-stu-id="a7150-106">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="a7150-107">Service Map zeigt Verbindungen zwischen Servern, Prozessen und Ports über die gesamte TCP-Verbindungsarchitektur an. Außer der Installation eines Agents ist keine weitere Konfiguration erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a7150-107">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="a7150-108">Weitere Informationen zur [Azure-Dienstzuordnung](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)</span><span class="sxs-lookup"><span data-stu-id="a7150-108">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="a7150-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="a7150-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a7150-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="a7150-110">Install the npm module</span></span>

<span data-ttu-id="a7150-111">Installieren des npm-Moduls für die Azure-Dienstzuordnung</span><span class="sxs-lookup"><span data-stu-id="a7150-111">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="a7150-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a7150-112">Example</span></span>

<span data-ttu-id="a7150-113">Mit diesem Beispiel werden alle Dienstzuordnungen für die angegebene Ressourcengruppe und den angegebenen Arbeitsbereich aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="a7150-113">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="a7150-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a7150-114">Samples</span></span>

<span data-ttu-id="a7150-115">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a7150-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
