---
title: "Azure DNS-Module für Node.js"
description: "Referenz zu anderen Azure DNS-Modulen für Node.js"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a>Azure DNS-Module für Node.js

## <a name="overview"></a>Übersicht

Verwenden Sie Azure DNS (Domain Name System), um Ihre DNS-Domänen in Azure zu verwalten. Verwalten Sie Ihre DNS-Einträge mit den gleichen Anmeldeinformationen, der gleichen Abrechnung und dem gleichen Supportvertrag wie bei Ihren anderen Azure-Diensten. Integrieren Sie Azure-basierte Dienste nahtlos in entsprechende DNS-Updates, und optimieren Sie Ihren gesamten Bereitstellungsprozess.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure DNS

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden die DNS-Verwaltungszonen aufgelistet:

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
