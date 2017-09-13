---
title: "Azure-Abrechnungsmodule für Node.js"
description: "Referenz zu Azure-Abrechnungsmodulen für Node.js"
keywords: Azure,SDK,API,Abrechnung, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a>Azure-Abrechnungsmodule für Node.js

## <a name="overview"></a>Übersicht
Die Azure-Abrechnungs-APIs ermöglichen den Zugriff auf Ihre Azure-Abrechnungsinformationen und -Rechnungen.

Der Kontoadministrator muss diese API im Azure-Portal abonnieren, damit sie verwendet werden kann. Informationen finden Sie unter [Verwalten des Zugriffs auf die Azure-Abrechnung mithilfe von Rollen](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls 

Installieren des npm-Moduls für die Azure-Abrechnung 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>Beispiel 
 
Mit diesem Beispiel wird eine Liste aller bisherigen Rechnung ausgegeben:
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
