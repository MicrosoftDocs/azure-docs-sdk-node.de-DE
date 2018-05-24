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
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="20082-103">Azure IoT Hub-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="20082-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="20082-104">Azure IoT Hub ist ein vollständig verwalteter Dienst, der eine zuverlässige und sichere bidirektionale Kommunikation zwischen Millionen von IoT-Geräten und einem Lösungs-Back-End ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="20082-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="20082-105">Azure IoT Hub:</span><span class="sxs-lookup"><span data-stu-id="20082-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="20082-106">stellt zahlreiche D2C- und C2D-Kommunikationsoptionen (Gerät-an-Cloud und Cloud-an-Gerät) bereit, einschließlich unidirektionales Messaging, Dateiübertragungen und Anforderung-Antwort-Methoden.</span><span class="sxs-lookup"><span data-stu-id="20082-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="20082-107">Bietet integriertes deklaratives Nachrichtenrouting zu anderen Azure-Diensten.</span><span class="sxs-lookup"><span data-stu-id="20082-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="20082-108">Bietet einen abfragbaren Speicher für Gerätemetadaten und synchronisierte Zustandsinformationen.</span><span class="sxs-lookup"><span data-stu-id="20082-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="20082-109">ermöglicht eine sichere Kommunikation und Zugriffssteuerung mithilfe von geräteabhängigen Sicherheitsschlüsseln oder X.509-Zertifikaten.</span><span class="sxs-lookup"><span data-stu-id="20082-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="20082-110">Bietet eine umfassende Überwachung der Ereignisse zur Verwaltung der Gerätekonnektivität und -identität.</span><span class="sxs-lookup"><span data-stu-id="20082-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="20082-111">Gerätebibliotheken für die gängigsten Sprachen und Plattformen</span><span class="sxs-lookup"><span data-stu-id="20082-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="20082-112">Installieren der Azure IoT Hub-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="20082-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="20082-113">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="20082-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="20082-114">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="20082-114">Install the npm module</span></span>

<span data-ttu-id="20082-115">Installieren des npm-Moduls für Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="20082-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="20082-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="20082-116">Example</span></span>

<span data-ttu-id="20082-117">Mit diesem Beispiel wird ein IoT-Hub erstellt und benannt:</span><span class="sxs-lookup"><span data-stu-id="20082-117">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="20082-118">Mit diesem Beispiel wird der vorhandene IoT-Hub anhand des Namens abgerufen:</span><span class="sxs-lookup"><span data-stu-id="20082-118">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="20082-119">Beispiele</span><span class="sxs-lookup"><span data-stu-id="20082-119">Samples</span></span>

- [<span data-ttu-id="20082-120">Erste Schritte mit dem Azure IoT Starter Kit für Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="20082-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="20082-121">Tweeten von Schwingungsanomalien, die von Azure IoT-Diensten für Daten von einem Intel Edison-System unter Node.js erkannt werden</span><span class="sxs-lookup"><span data-stu-id="20082-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="20082-122">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="20082-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
