---
title: "Azure Cognitive Services-Module für Node.js"
description: "Referenz zu Azure Cognitive Services-Modulen für Node.js"
keywords: Azure, SDK, API, Cognitive Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="808ba-104">Azure Cognitive Services-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="808ba-104">Azure Cognitive Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="808ba-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="808ba-105">Overview</span></span>

<span data-ttu-id="808ba-106">Bei Azure Cognitive Services handelt es sich um eine Reihe von APIs, SDKs und Diensten für Entwickler, mit denen diese ihre Anwendungen intelligenter, ansprechender und besser ermittelbar machen können.</span><span class="sxs-lookup"><span data-stu-id="808ba-106">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="808ba-107">Mit Microsoft Cognitive Services wird das wachsende Portfolio der Machine Learning-APIs von Microsoft erweitert, und Entwickler können ihren Anwendungen leicht intelligente Features hinzufügen, z.B. Emotions- und Videoerkennung, Gesichtserkennung, Spracherkennung, maschinelles Sehen sowie Sprachverständnis.</span><span class="sxs-lookup"><span data-stu-id="808ba-107">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="808ba-108">Unsere Vision besteht darin, persönlichere Computing-Umgebungen zu schaffen und mit Systemen, die immer besser sehen, hören, sprechen und verstehen und sogar Schlüsse ziehen können, für bessere Produktivität zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="808ba-108">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="808ba-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="808ba-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="808ba-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="808ba-110">Install the npm module</span></span>

<span data-ttu-id="808ba-111">Installieren Sie das Azure Cognitive Services-npm-Modul.</span><span class="sxs-lookup"><span data-stu-id="808ba-111">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="808ba-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="808ba-112">Example</span></span>

<span data-ttu-id="808ba-113">In diesem Beispiel werden alle Cognitive Services-Konten aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="808ba-113">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="808ba-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="808ba-114">Samples</span></span>

<span data-ttu-id="808ba-115">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="808ba-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
