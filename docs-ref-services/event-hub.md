---
title: Azure Event Hub-Module für Node.js
description: Referenz zu Azure Event Hub-Modulen für Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: cf50d0e69e336dac9addc85625599fbbefd1902e
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51121829"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="ec57c-103">Azure Event Hub-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="ec57c-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="ec57c-104">Azure Event Hubs ist eine hochgradig skalierbare Datenstreamingplattform und ein Dienst zur Erfassung von Ereignissen, der bzw. die Millionen Ereignisse pro Sekunde empfangen und verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="ec57c-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="ec57c-105">Event Hubs kann Ereignisse, Daten oder Telemetriedaten, die von verteilter Software und verteilten Geräten erzeugt wurden, verarbeiten und speichern.</span><span class="sxs-lookup"><span data-stu-id="ec57c-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="ec57c-106">An einen Event Hub gesendete Daten können transformiert und mit einem beliebigen Echtzeitanalyse-Anbieter oder Batchverarbeitungs-/Speicheradapter gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="ec57c-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="ec57c-107">Mit der Möglichkeit, Veröffentlichen-/Abonnieren-Funktionen mit niedriger Latenz und enormem Umfang anzubieten, sind Event Hubs der Einstiegspunkt für Big Data.</span><span class="sxs-lookup"><span data-stu-id="ec57c-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="ec57c-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="ec57c-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ec57c-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="ec57c-109">Install the npm module</span></span> 

<span data-ttu-id="ec57c-110">Installieren der Azure Event Hub-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="ec57c-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="ec57c-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ec57c-111">Example</span></span>

<span data-ttu-id="ec57c-112">Mit diesem Beispiel werden Informationen zu einem vorhandenen Event Hub abgerufen:</span><span class="sxs-lookup"><span data-stu-id="ec57c-112">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="ec57c-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ec57c-113">Samples</span></span>

<span data-ttu-id="ec57c-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ec57c-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
