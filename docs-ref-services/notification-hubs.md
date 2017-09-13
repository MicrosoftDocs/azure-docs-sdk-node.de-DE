---
title: "Azure Notification Hubs-Module für Node.js"
description: "Referenz zu Azure Notification Hubs-Modulen für Node.js"
keywords: Azure,SDK,API,Notification Hubs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Azure Notification Hubs-Module für Node.js

## <a name="overview"></a>Übersicht

Azure Notification Hubs bietet ein einfach zu bedienendes, horizontal skaliertes Pushmodul. Mit einem einzelnen plattformübergreifende API-Aufruf können Sie zielgerichtete und personalisierte Pushbenachrichtigungen aus einem beliebigen Cloud- oder lokalen Back-End an sämtliche mobile Plattformen senden.

Notification Hubs eignet sich sowohl für Unternehmens- als auch Privatkundenszenarien. Es folgen einige Beispiele, wofür Kunden Notification Hubs nutzen:
- Senden von Benachrichtigungen zu brandaktuellen Nachrichten an Millionen von Empfängern mit niedriger Latenz
- Senden standortbasierter Gutscheine an interessierte Kundengruppen
- Senden von Ereignisbenachrichtigungen an Benutzer oder Gruppen für Medien-/Sport-/Finanz-/Spieleanwendungen
- Pushübertragung von Werbeinhalten an Apps, um Kunden anzusprechen und zum Kauf anzuregen
- Benachrichtigen von Benutzer zu Unternehmensereignissen wie neue Nachrichten und Arbeitsaufgaben
- Senden von Codes für die mehrstufige Authentifizierung

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des Azure Notification Hubs-Moduls 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Notification Hubs aufgeführt:

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>Beispiele

* [Mobile App Service-Apps: Abgeschlossener Schnellstart für Node.js-Back-End](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Tweeten von Vibrationsanomalien, die von Azure IoT-Diensten anhand von Daten eines Intel Edison-Systems unter Node.js erkannt werden](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
