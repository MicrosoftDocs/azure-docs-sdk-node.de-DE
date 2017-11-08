---
title: "Azure CDN-Module für Node.js"
description: "Referenz zu anderen Azure CDN-Modulen für Node.js"
keywords: Azure,SDK,API,CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a>Azure CDN-Module für Node.js

## <a name="overview"></a>Übersicht

Das Azure Content Delivery Network (CDN) bietet Entwicklern eine globale Lösung für die Bereitstellung von Inhalten mit hoher Bandbreite, die in Azure oder an einem beliebigen anderen Ort gehostet werden. Mit einem CDN können Sie öffentlich verfügbare Objekte zwischenspeichern, die aus dem Azure-Blobspeicher, einer Webanwendung, einem virtuellen Computer, einem Anwendungsordner oder einem anderen HTTP-/HTTPS-Speicherort geladen werden. Der zum Zwischenspeichern verwendete CDN-Cache kann an strategischen Standorten angesiedelt werden, um beim Übermitteln des Inhalts an die Benutzer eine maximale Bandbreite zu gewährleisten. Ein CDN wird normalerweise zum Bereitstellen statischer Inhalte wie Bilder, Stylesheets, Dokumente, Dateien, clientseitige Skripts und HTML-Seiten verwendet.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure CDN

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden CDN-Profile aufgelistet:

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.