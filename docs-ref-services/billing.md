---
title: "Azure-Abrechnungsmodule für Node.js"
description: "Referenz zu Azure-Abrechnungsmodulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="37813-103">Azure-Abrechnungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="37813-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="37813-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="37813-104">Overview</span></span>
<span data-ttu-id="37813-105">Die Azure-Abrechnungs-APIs ermöglichen den Zugriff auf Ihre Azure-Abrechnungsinformationen und -Rechnungen.</span><span class="sxs-lookup"><span data-stu-id="37813-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="37813-106">Der Kontoadministrator muss diese API im Azure-Portal abonnieren, damit sie verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="37813-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="37813-107">Informationen finden Sie unter [Verwalten des Zugriffs auf die Azure-Abrechnung mithilfe von Rollen](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="37813-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="37813-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="37813-108">Install the npm module</span></span> 

<span data-ttu-id="37813-109">Installieren des npm-Moduls für die Azure-Abrechnung</span><span class="sxs-lookup"><span data-stu-id="37813-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="37813-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="37813-110">Example</span></span> 
 
<span data-ttu-id="37813-111">Mit diesem Beispiel wird eine Liste aller bisherigen Rechnung ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="37813-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="37813-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="37813-112">Samples</span></span>

<span data-ttu-id="37813-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="37813-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
