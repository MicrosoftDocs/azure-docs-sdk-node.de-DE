---
title: "Azure IoT Hub-Module für Node.js"
description: "Referenz zu Azure IoT Hub-Modulen für Node.js"
keywords: Azure,SDK,API,IoT Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 44d01ceb833d2acbef6f9f22b32d4ad66b1fd5ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="2d637-104">Azure IoT Hub-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="2d637-104">Azure IoT Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2d637-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2d637-105">Overview</span></span>

<span data-ttu-id="2d637-106">Azure IoT Hub ist ein vollständig verwalteter Dienst, der eine zuverlässige und sichere bidirektionale Kommunikation zwischen Millionen von IoT-Geräten und einem Lösungs-Back-End ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="2d637-106">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="2d637-107">Azure IoT Hub:</span><span class="sxs-lookup"><span data-stu-id="2d637-107">Azure IoT Hub:</span></span>
- <span data-ttu-id="2d637-108">stellt zahlreiche D2C- und C2D-Kommunikationsoptionen (Gerät-an-Cloud und Cloud-an-Gerät) bereit, einschließlich unidirektionales Messaging, Dateiübertragungen und Anforderung-Antwort-Methoden.</span><span class="sxs-lookup"><span data-stu-id="2d637-108">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="2d637-109">Bietet integriertes deklaratives Nachrichtenrouting zu anderen Azure-Diensten.</span><span class="sxs-lookup"><span data-stu-id="2d637-109">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="2d637-110">Bietet einen abfragbaren Speicher für Gerätemetadaten und synchronisierte Zustandsinformationen.</span><span class="sxs-lookup"><span data-stu-id="2d637-110">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="2d637-111">ermöglicht eine sichere Kommunikation und Zugriffssteuerung mithilfe von geräteabhängigen Sicherheitsschlüsseln oder X.509-Zertifikaten.</span><span class="sxs-lookup"><span data-stu-id="2d637-111">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="2d637-112">Bietet eine umfassende Überwachung der Ereignisse zur Verwaltung der Gerätekonnektivität und -identität.</span><span class="sxs-lookup"><span data-stu-id="2d637-112">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="2d637-113">Gerätebibliotheken für die gängigsten Sprachen und Plattformen</span><span class="sxs-lookup"><span data-stu-id="2d637-113">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="2d637-114">Installieren der Azure IoT Hub-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="2d637-114">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="2d637-115">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="2d637-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2d637-116">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="2d637-116">Install the npm module</span></span>

<span data-ttu-id="2d637-117">Installieren des npm-Moduls für Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="2d637-117">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="2d637-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2d637-118">Example</span></span>

<span data-ttu-id="2d637-119">Mit diesem Beispiel wird ein IoT-Hub erstellt und benannt:</span><span class="sxs-lookup"><span data-stu-id="2d637-119">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="2d637-120">Mit diesem Beispiel wird der vorhandene IoT-Hub anhand des Namens abgerufen:</span><span class="sxs-lookup"><span data-stu-id="2d637-120">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2d637-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="2d637-121">Samples</span></span>

- [<span data-ttu-id="2d637-122">Erste Schritte mit dem Azure IoT Starter Kit für Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="2d637-122">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="2d637-123">Tweeten von Vibrationsanomalien, die von Azure IoT-Diensten anhand von Daten eines Intel Edison-Systems unter Node.js erkannt werden</span><span class="sxs-lookup"><span data-stu-id="2d637-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="2d637-124">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2d637-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
