---
title: Azure DNS-Module für Node.js
description: Referenz zu anderen Azure DNS-Modulen für Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262217"
---
# <a name="azure-dns-modules-for-nodejs"></a>Azure DNS-Module für Node.js

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

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
