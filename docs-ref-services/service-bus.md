---
title: "Azure Service Bus-Module für Node.js"
description: "Referenz zu Azure Service Bus-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 792e51acf2577649432b26e4b840bc1d40b7abaf
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="62245-103">Azure Service Bus-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="62245-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="62245-104">Azure Service Bus ist eine asynchrone Cloudplattform für Messaging, mit der Sie Daten zwischen entkoppelten Systemen senden können.</span><span class="sxs-lookup"><span data-stu-id="62245-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="62245-105">Weitere Informationen zu [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)</span><span class="sxs-lookup"><span data-stu-id="62245-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="62245-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="62245-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="62245-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="62245-107">Install the npm module</span></span>

<span data-ttu-id="62245-108">Installieren der Azure Service Bus-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="62245-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="62245-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="62245-109">Example</span></span>

<span data-ttu-id="62245-110">Mit diesem Beispiel wird ein Client erstellt, und anschließend werden alle einem bestimmten Abonnement zugeordneten Service Bus-Namespaces aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="62245-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="62245-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="62245-111">Samples</span></span>

<span data-ttu-id="62245-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="62245-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
