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
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Azure Cognitive Services-Module für Node.js

## <a name="overview"></a>Übersicht

Bei Azure Cognitive Services handelt es sich um eine Reihe von APIs, SDKs und Diensten für Entwickler, mit denen diese ihre Anwendungen intelligenter, ansprechender und besser ermittelbar machen können. Mit Microsoft Cognitive Services wird das wachsende Portfolio der Machine Learning-APIs von Microsoft erweitert, und Entwickler können ihren Anwendungen leicht intelligente Features hinzufügen, z.B. Emotions- und Videoerkennung, Gesichtserkennung, Spracherkennung, maschinelles Sehen sowie Sprachverständnis. Unsere Vision besteht darin, persönlichere Computing-Umgebungen zu schaffen und mit Systemen, die immer besser sehen, hören, sprechen und verstehen und sogar Schlüsse ziehen können, für bessere Produktivität zu sorgen.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren Sie das Azure Cognitive Services-npm-Modul.

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>Beispiel

In diesem Beispiel werden alle Cognitive Services-Konten aufgelistet.

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

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
