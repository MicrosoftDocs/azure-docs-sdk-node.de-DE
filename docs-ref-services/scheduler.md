---
title: "Azure Scheduler-Module für Node.js"
description: "Referenz zu Azure Scheduler-Modulen für Node.js"
keywords: Azure,SDK,API,Scheduler, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="32608-104">Azure Scheduler-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="32608-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="32608-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="32608-105">Overview</span></span>

<span data-ttu-id="32608-106">Von Azure Scheduler wird geplante Arbeit über HTTP, HTTPS, eine Speicherwarteschlange oder [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) erstellt, verwaltet und aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="32608-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="32608-107">Weitere Informationen zu [Azure Scheduler](/azure/scheduler/scheduler-intro)</span><span class="sxs-lookup"><span data-stu-id="32608-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="32608-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="32608-108">Management package</span></span>

<span data-ttu-id="32608-109">Mit der Verwaltungs-API können Sie geplante Arbeit über verschiedene Kommunikationskanäle erstellen, verwalten und aufrufen.</span><span class="sxs-lookup"><span data-stu-id="32608-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="32608-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="32608-110">Install the npm module</span></span>

<span data-ttu-id="32608-111">Installieren des npm-Moduls für Azure Scheduler</span><span class="sxs-lookup"><span data-stu-id="32608-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="32608-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="32608-112">Example</span></span>

<span data-ttu-id="32608-113">Mit diesem Beispiel werden die aktuellen Planer aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="32608-113">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="32608-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="32608-114">Samples</span></span>

<span data-ttu-id="32608-115">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="32608-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
