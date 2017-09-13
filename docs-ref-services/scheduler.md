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
# <a name="azure-scheduler-modules-for-nodejs"></a>Azure Scheduler-Module für Node.js

## <a name="overview"></a>Übersicht

Von Azure Scheduler wird geplante Arbeit über HTTP, HTTPS, eine Speicherwarteschlange oder [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview) erstellt, verwaltet und aufgerufen.

Weitere Informationen zu [Azure Scheduler](/azure/scheduler/scheduler-intro)

## <a name="management-package"></a>Verwaltungspaket

Mit der Verwaltungs-API können Sie geplante Arbeit über verschiedene Kommunikationskanäle erstellen, verwalten und aufrufen.

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure Scheduler

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden die aktuellen Planer aufgelistet.

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

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
