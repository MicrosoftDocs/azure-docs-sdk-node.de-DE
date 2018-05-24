---
title: Azure-Dienstzuordnungsmodule für Node.js
description: Referenz zu Azure-Dienstzuordnungsmodulen für Node.js
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: db064603e32446ba2f094da2a1601520b99a7304
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="1dc33-103">Azure-Dienstzuordnungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="1dc33-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="1dc33-104">Service Map ermittelt automatisch Anwendungskomponenten auf Windows- und Linux-Systemen und stellt die Kommunikation zwischen Diensten dar.</span><span class="sxs-lookup"><span data-stu-id="1dc33-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="1dc33-105">Service Map zeigt Verbindungen zwischen Servern, Prozessen und Ports über die gesamte TCP-Verbindungsarchitektur an. Außer der Installation eines Agents ist keine weitere Konfiguration erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1dc33-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="1dc33-106">Weitere Informationen zur [Azure-Dienstzuordnung](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map)</span><span class="sxs-lookup"><span data-stu-id="1dc33-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="1dc33-107">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="1dc33-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1dc33-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="1dc33-108">Install the npm module</span></span>

<span data-ttu-id="1dc33-109">Installieren des npm-Moduls für die Azure-Dienstzuordnung</span><span class="sxs-lookup"><span data-stu-id="1dc33-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="1dc33-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1dc33-110">Example</span></span>

<span data-ttu-id="1dc33-111">Mit diesem Beispiel werden alle Dienstzuordnungen für die angegebene Ressourcengruppe und den angegebenen Arbeitsbereich aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="1dc33-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1dc33-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1dc33-112">Samples</span></span>

<span data-ttu-id="1dc33-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1dc33-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
