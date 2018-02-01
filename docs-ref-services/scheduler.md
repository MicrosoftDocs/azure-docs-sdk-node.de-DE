---
title: "Azure Scheduler-Module für Node.js"
description: "Referenz zu Azure Scheduler-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 539337abd2fff3830cb022a49aff374e877a08ee
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="531ab-103">Azure Scheduler-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="531ab-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="531ab-104">Von Azure Scheduler wird geplante Arbeit über HTTP, HTTPS, eine Speicherwarteschlange oder [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) erstellt, verwaltet und aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="531ab-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="531ab-105">Weitere Informationen zu [Azure Scheduler](/azure/scheduler/scheduler-intro)</span><span class="sxs-lookup"><span data-stu-id="531ab-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="531ab-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="531ab-106">Management package</span></span>

<span data-ttu-id="531ab-107">Mit der Verwaltungs-API können Sie geplante Arbeit über verschiedene Kommunikationskanäle erstellen, verwalten und aufrufen.</span><span class="sxs-lookup"><span data-stu-id="531ab-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="531ab-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="531ab-108">Install the npm module</span></span>

<span data-ttu-id="531ab-109">Installieren des npm-Moduls für Azure Scheduler</span><span class="sxs-lookup"><span data-stu-id="531ab-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="531ab-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="531ab-110">Example</span></span>

<span data-ttu-id="531ab-111">Mit diesem Beispiel werden die aktuellen Planer aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="531ab-111">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="531ab-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="531ab-112">Samples</span></span>

<span data-ttu-id="531ab-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="531ab-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
