---
title: "Azure Media Services-Module für Node.js"
description: "Referenz zu Azure Media Services-Modulen für Node.js"
keywords: Azure,SDK,API,Media Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="d7cdc-104">Azure Media Services-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="d7cdc-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d7cdc-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d7cdc-105">Overview</span></span>

<span data-ttu-id="d7cdc-106">Azure Media Services ist eine erweiterbare, cloudbasierte Plattform, die Entwicklern das Erstellen von skalierbaren Medienverwaltungslösungen und Bereitstellungsanwendungen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d7cdc-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="d7cdc-107">Media Services basiert auf REST-APIs, mit denen Sie auf sichere Weise Video- oder Audioinhalte hochladen, speichern, codieren und verpacken können – sowohl für eine bedarfsgesteuerte als auch für eine auf Livestreaming basierende Bereitstellung auf verschiedenen Clients (z.B. TV, PC und mobile Geräte).</span><span class="sxs-lookup"><span data-stu-id="d7cdc-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="d7cdc-108">Mit Azure Media Services haben Sie folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="d7cdc-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="d7cdc-109">Erstellen vollständiger End-to-End-Workflows mithilfe von Media Services</span><span class="sxs-lookup"><span data-stu-id="d7cdc-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="d7cdc-110">Nutzen von Drittanbieterkomponenten für einige Elemente Ihres Workflows</span><span class="sxs-lookup"><span data-stu-id="d7cdc-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="d7cdc-111">Beispielsweise können Sie die Codierung mit einem Encoder eines Drittanbieters durchführen.</span><span class="sxs-lookup"><span data-stu-id="d7cdc-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="d7cdc-112">Anschließend sorgen Sie mit Media Services für Upload, Schutz, Paketierung und Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="d7cdc-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="d7cdc-113">Streamen Sie Ihre Inhalte live, oder stellen Sie sie bei Bedarf bereit.</span><span class="sxs-lookup"><span data-stu-id="d7cdc-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="d7cdc-114">Das Thema enthält außerdem Links zu anderen relevanten Themen.</span><span class="sxs-lookup"><span data-stu-id="d7cdc-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="d7cdc-115">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="d7cdc-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d7cdc-116">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="d7cdc-116">Install the npm module</span></span>

<span data-ttu-id="d7cdc-117">Installieren des npm-Moduls für Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="d7cdc-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="d7cdc-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d7cdc-118">Example</span></span>

<span data-ttu-id="d7cdc-119">Mit diesem Beispiel werden alle Mediendienste für eine Ressourcengruppe aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="d7cdc-119">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="d7cdc-120">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d7cdc-120">Samples</span></span>

<span data-ttu-id="d7cdc-121">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d7cdc-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
