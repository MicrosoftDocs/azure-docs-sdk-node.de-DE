---
title: Azure Notification Hubs-Module für Node.js
description: Referenz zu Azure Notification Hubs-Modulen für Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094384"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Azure Notification Hubs-Module für Node.js

Azure Notification Hubs bietet eine einfach zu bedienende, horizontal skalierte Push-Engine. Mit einem einzelnen plattformübergreifende API-Aufruf können Sie zielgerichtete und personalisierte Pushbenachrichtigungen aus einem beliebigen Cloud- oder lokalen Back-End an sämtliche mobile Plattformen senden.

Notification Hubs eignet sich sowohl für Unternehmens- als auch Privatkundenszenarien. Es folgen einige Beispiele, wofür Kunden Notification Hubs nutzen:
- Senden von Benachrichtigungen zu brandaktuellen Nachrichten an Millionen von Empfängern mit niedriger Latenz
- Senden standortbasierter Gutscheine an interessierte Kundengruppen
- Senden von Ereignisbenachrichtigungen an Benutzer oder Gruppen für Medien-/Sport-/Finanz-/Spieleanwendungen
- Pushübertragung von Werbeinhalten an Apps, um Kunden anzusprechen und zum Kauf anzuregen
- Benachrichtigen von Benutzer zu Unternehmensereignissen wie neue Nachrichten und Arbeitselementen
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

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
