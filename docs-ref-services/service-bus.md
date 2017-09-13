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
# <a name="azure-service-bus-modules-for-nodejs"></a>Azure Service Bus-Module für Node.js

## <a name="overview"></a>Übersicht

Azure Service Bus ist eine asynchrone Cloudplattform für Messaging, mit der Sie Daten zwischen entkoppelten Systemen senden können.

Weitere Informationen zu [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren der Azure Service Bus-Module für Node.js mithilfe von npm

```bash
npm install azure-arm-sb
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird ein Client erstellt, und anschließend werden alle einem bestimmten Abonnement zugeordneten Service Bus-Namespaces aufgeführt.

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

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
