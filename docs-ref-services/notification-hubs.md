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
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="47120-104">Azure Notification Hubs-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="47120-104">Azure Notification Hubs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="47120-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="47120-105">Overview</span></span>

<span data-ttu-id="47120-106">Azure Notification Hubs bietet ein einfach zu bedienendes, horizontal skaliertes Pushmodul.</span><span class="sxs-lookup"><span data-stu-id="47120-106">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="47120-107">Mit einem einzelnen plattformübergreifende API-Aufruf können Sie zielgerichtete und personalisierte Pushbenachrichtigungen aus einem beliebigen Cloud- oder lokalen Back-End an sämtliche mobile Plattformen senden.</span><span class="sxs-lookup"><span data-stu-id="47120-107">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="47120-108">Notification Hubs eignet sich sowohl für Unternehmens- als auch Privatkundenszenarien.</span><span class="sxs-lookup"><span data-stu-id="47120-108">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="47120-109">Es folgen einige Beispiele, wofür Kunden Notification Hubs nutzen:</span><span class="sxs-lookup"><span data-stu-id="47120-109">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="47120-110">Senden von Benachrichtigungen zu brandaktuellen Nachrichten an Millionen von Empfängern mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="47120-110">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="47120-111">Senden standortbasierter Gutscheine an interessierte Kundengruppen</span><span class="sxs-lookup"><span data-stu-id="47120-111">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="47120-112">Senden von Ereignisbenachrichtigungen an Benutzer oder Gruppen für Medien-/Sport-/Finanz-/Spieleanwendungen</span><span class="sxs-lookup"><span data-stu-id="47120-112">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="47120-113">Pushübertragung von Werbeinhalten an Apps, um Kunden anzusprechen und zum Kauf anzuregen</span><span class="sxs-lookup"><span data-stu-id="47120-113">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="47120-114">Benachrichtigen von Benutzer zu Unternehmensereignissen wie neue Nachrichten und Arbeitsaufgaben</span><span class="sxs-lookup"><span data-stu-id="47120-114">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="47120-115">Senden von Codes für die mehrstufige Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="47120-115">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="47120-116">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="47120-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="47120-117">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="47120-117">Install the npm module</span></span>

<span data-ttu-id="47120-118">Installieren des Azure Notification Hubs-Moduls</span><span class="sxs-lookup"><span data-stu-id="47120-118">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="47120-119">Beispiel</span><span class="sxs-lookup"><span data-stu-id="47120-119">Example</span></span>

<span data-ttu-id="47120-120">Mit diesem Beispiel werden alle Notification Hubs aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="47120-120">This example lists all notification hubs.</span></span>

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

## <a name="samples"></a><span data-ttu-id="47120-121">Beispiele</span><span class="sxs-lookup"><span data-stu-id="47120-121">Samples</span></span>

* [<span data-ttu-id="47120-122">Mobile App Service-Apps: Abgeschlossener Schnellstart für Node.js-Back-End</span><span class="sxs-lookup"><span data-stu-id="47120-122">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="47120-123">Tweeten von Vibrationsanomalien, die von Azure IoT-Diensten anhand von Daten eines Intel Edison-Systems unter Node.js erkannt werden</span><span class="sxs-lookup"><span data-stu-id="47120-123">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="47120-124">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="47120-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
