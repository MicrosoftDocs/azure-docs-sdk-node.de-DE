---
title: "Azure Commerce-Module für Node.js"
description: "Referenz zu Azure Commerce-Modulen für Node.js"
keywords: Azure,SDK,API,Commerce, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a>Azure Commerce-Module für Node.js

## <a name="overview"></a>Übersicht

Verwenden Sie Azure Commerce-APIs, um Nutzungs- und Ressourcendaten mittels Pull in Ihre bevorzugten Datenanalysetools zu übertragen. Mithilfe der Azure-Ressourcennutzungs- und -Gebührenkarten-APIs können Sie Ihre Kosten genau vorhersagen und verwalten. Die APIs werden als Ressourcenanbieter implementiert und sind Teil der API-Familie, die von Azure Resource Manager verfügbar gemacht wird.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure Commerce

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden die geschätzten Azure-Nutzungsdaten für den letzten Monat abgerufen:

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
