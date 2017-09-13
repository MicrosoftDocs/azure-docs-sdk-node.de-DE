---
title: "Azure Container Registry-Module für Node.js"
description: "Referenz zu Azure Container Registry-Modulen für Node.js"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Azure Container Registry-Module für Node.js

## <a name="overview"></a>Übersicht

Azure Container Registry ist ein verwalteter Dienst vom Typ „Docker-Registrierung“, der auf Version 2.0 der Open Source-Docker-Registrierung basiert. Erstellen und verwalten Sie Azure-Containerregistrierungen, um Ihre privaten Docker-Containerimages zu speichern und zu verwalten. Verwenden Sie Containerregistrierungen in Azure mit Ihren vorhandenen Containerentwicklungs- und Bereitstellungspipelines, und nutzen Sie das umfangreiche Wissen der Docker-Community.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure Container Registry

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird eine Liste der verfügbaren Container abgerufen:

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
