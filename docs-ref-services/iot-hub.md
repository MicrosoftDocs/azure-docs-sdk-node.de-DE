---
title: Azure IoT Hub-Module für Node.js
description: Referenz zu Azure IoT Hub-Modulen für Node.js
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 77dd4c30da43af7cace048b43b7997fb1952abf1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Azure IoT Hub-Module für Node.js

Azure IoT Hub ist ein vollständig verwalteter Dienst, der eine zuverlässige und sichere bidirektionale Kommunikation zwischen Millionen von IoT-Geräten und einem Lösungs-Back-End ermöglicht. Azure IoT Hub:
- stellt zahlreiche D2C- und C2D-Kommunikationsoptionen (Gerät-an-Cloud und Cloud-an-Gerät) bereit, einschließlich unidirektionales Messaging, Dateiübertragungen und Anforderung-Antwort-Methoden.
- Bietet integriertes deklaratives Nachrichtenrouting zu anderen Azure-Diensten.
- Bietet einen abfragbaren Speicher für Gerätemetadaten und synchronisierte Zustandsinformationen.
- ermöglicht eine sichere Kommunikation und Zugriffssteuerung mithilfe von geräteabhängigen Sicherheitsschlüsseln oder X.509-Zertifikaten.
- Bietet eine umfassende Überwachung der Ereignisse zur Verwaltung der Gerätekonnektivität und -identität.
- Gerätebibliotheken für die gängigsten Sprachen und Plattformen

Installieren der Azure IoT Hub-Module für Node.js mithilfe von npm

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure IoT Hub

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird ein IoT-Hub erstellt und benannt:

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

Mit diesem Beispiel wird der vorhandene IoT-Hub anhand des Namens abgerufen:

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a>Beispiele

- [Erste Schritte mit dem Azure IoT Starter Kit für Raspberry Pi](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Tweeten von Schwingungsanomalien, die von Azure IoT-Diensten für Daten von einem Intel Edison-System unter Node.js erkannt werden](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
