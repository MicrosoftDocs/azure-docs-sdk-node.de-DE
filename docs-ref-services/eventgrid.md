---
title: Azure Event Grid-Bibliotheken für Node.js
description: Referenz für Azure Event Grid-Bibliotheken für Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48425748"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="1c6cc-103">Azure Event Grid-Bibliotheken für Node.js</span><span class="sxs-lookup"><span data-stu-id="1c6cc-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="1c6cc-104">Buildereignisgesteuerte Anwendungen, die mit einfacher HTTP-basierter Ereignisbehandlung und Azure Event Grid auf Ereignisse von Azure-Diensten und benutzerdefinierten Quellen lauschen und reagieren</span><span class="sxs-lookup"><span data-stu-id="1c6cc-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="1c6cc-105">[Weitere Informationen](/azure/event-grid/overview) zu Azure Event Grid und erste Schritte mit dem [Tutorial zu Azure Blob Storage-Ereignissen](/azure/storage/blobs/storage-blob-event-quickstart)</span><span class="sxs-lookup"><span data-stu-id="1c6cc-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="1c6cc-106">Veröffentlichungs-SDK</span><span class="sxs-lookup"><span data-stu-id="1c6cc-106">Publish SDK</span></span>

<span data-ttu-id="1c6cc-107">Mit dem Veröffentlichungs-SDK von Azure Event Grid können Sie Ereignisse erstellen, die Authentifizierung durchführen und Beiträge in Themen posten.</span><span class="sxs-lookup"><span data-stu-id="1c6cc-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="1c6cc-108">Installation</span><span class="sxs-lookup"><span data-stu-id="1c6cc-108">Installation</span></span>

<span data-ttu-id="1c6cc-109">Fügen Sie Ihrem Projekt das Modul mit npm hinzu:</span><span class="sxs-lookup"><span data-stu-id="1c6cc-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="1c6cc-110">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="1c6cc-110">Example code</span></span>

<span data-ttu-id="1c6cc-111">Das folgende Codesegment veröffentlicht ein Modellereignis in einem Event Grid-Thema.</span><span class="sxs-lookup"><span data-stu-id="1c6cc-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="1c6cc-112">Sie können den Endpunkt und die Zugriffsschlüssel des Themas über das Azure-Portal oder die Azure-Befehlszeilenschnittstelle abrufen:</span><span class="sxs-lookup"><span data-stu-id="1c6cc-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="1c6cc-113">In diesem Beispiel wird gezeigt, wie Sie ein Ereignis aus Azure Storage behandeln:</span><span class="sxs-lookup"><span data-stu-id="1c6cc-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c6cc-114">Informationen zu den Client-APIs</span><span class="sxs-lookup"><span data-stu-id="1c6cc-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="1c6cc-115">Verwaltungs-SDK</span><span class="sxs-lookup"><span data-stu-id="1c6cc-115">Management SDK</span></span>

<span data-ttu-id="1c6cc-116">Das Verwaltungs-SDK ermöglicht Ihnen das Erstellen, Aktualisieren und Löschen von Event Grid-Instanzen, -Themen und -Abonnements.</span><span class="sxs-lookup"><span data-stu-id="1c6cc-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="1c6cc-117">Installation</span><span class="sxs-lookup"><span data-stu-id="1c6cc-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="1c6cc-118">Beispielcode</span><span class="sxs-lookup"><span data-stu-id="1c6cc-118">Example code</span></span>

<span data-ttu-id="1c6cc-119">Der folgende Code erstellt das Event Grid-Thema `topic1` und gibt die Zugriffsschlüssel für das neu erstellte Thema zurück:</span><span class="sxs-lookup"><span data-stu-id="1c6cc-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c6cc-120">Informationen zu den Verwaltungs-APIs</span><span class="sxs-lookup"><span data-stu-id="1c6cc-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="1c6cc-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1c6cc-121">Learn more</span></span>

- <span data-ttu-id="1c6cc-122">[Receive events using the Event Grid SDK](/azure/event-grid/receive-events) (Empfangen von Ereignissen mithilfe des Event Grid SDK)</span><span class="sxs-lookup"><span data-stu-id="1c6cc-122">[Receive events using the Event Grid SDK](/azure/event-grid/receive-events)</span></span>
