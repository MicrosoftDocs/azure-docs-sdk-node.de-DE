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
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="29f3d-104">Azure-Abrechnungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="29f3d-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="29f3d-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="29f3d-105">Overview</span></span>
<span data-ttu-id="29f3d-106">Die Azure-Abrechnungs-APIs ermöglichen den Zugriff auf Ihre Azure-Abrechnungsinformationen und -Rechnungen.</span><span class="sxs-lookup"><span data-stu-id="29f3d-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="29f3d-107">Der Kontoadministrator muss diese API im Azure-Portal abonnieren, damit sie verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="29f3d-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="29f3d-108">Informationen finden Sie unter [Verwalten des Zugriffs auf die Azure-Abrechnung mithilfe von Rollen](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="29f3d-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="29f3d-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="29f3d-109">Install the npm module</span></span> 

<span data-ttu-id="29f3d-110">Installieren des npm-Moduls für die Azure-Abrechnung</span><span class="sxs-lookup"><span data-stu-id="29f3d-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="29f3d-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="29f3d-111">Example</span></span> 
 
<span data-ttu-id="29f3d-112">Mit diesem Beispiel wird eine Liste aller bisherigen Rechnung ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="29f3d-112">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="29f3d-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="29f3d-113">Samples</span></span>

<span data-ttu-id="29f3d-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="29f3d-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
