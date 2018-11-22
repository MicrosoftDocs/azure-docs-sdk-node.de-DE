---
title: Azure-Abrechnungsmodule für Node.js
description: Referenz zu Azure-Abrechnungsmodulen für Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 7be64d01c1bf8d247694735b8581f72678f55983
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094469"
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

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
