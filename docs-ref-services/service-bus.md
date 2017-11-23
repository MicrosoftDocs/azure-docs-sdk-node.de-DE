---
title: "Azure Service Bus-Module für Node.js"
description: "Referenz zu Azure Service Bus-Modulen für Node.js"
keywords: Azure,SDK,API,Service Bus, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="f57ef-104">Azure Service Bus-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="f57ef-104">Azure Service Bus Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f57ef-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f57ef-105">Overview</span></span>

<span data-ttu-id="f57ef-106">Azure Service Bus ist eine asynchrone Cloudplattform für Messaging, mit der Sie Daten zwischen entkoppelten Systemen senden können.</span><span class="sxs-lookup"><span data-stu-id="f57ef-106">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="f57ef-107">Weitere Informationen zu [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)</span><span class="sxs-lookup"><span data-stu-id="f57ef-107">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="f57ef-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="f57ef-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f57ef-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="f57ef-109">Install the npm module</span></span>

<span data-ttu-id="f57ef-110">Installieren der Azure Service Bus-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="f57ef-110">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="f57ef-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f57ef-111">Example</span></span>

<span data-ttu-id="f57ef-112">Mit diesem Beispiel wird ein Client erstellt, und anschließend werden alle einem bestimmten Abonnement zugeordneten Service Bus-Namespaces aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="f57ef-112">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f57ef-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="f57ef-113">Samples</span></span>

<span data-ttu-id="f57ef-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f57ef-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
