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
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49057644"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="440bd-103">Azure-Abrechnungsmodule für Node.js</span><span class="sxs-lookup"><span data-stu-id="440bd-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="440bd-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="440bd-104">Overview</span></span>
<span data-ttu-id="440bd-105">Die Azure-Abrechnungs-APIs ermöglichen den Zugriff auf Ihre Azure-Abrechnungsinformationen und -Rechnungen.</span><span class="sxs-lookup"><span data-stu-id="440bd-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="440bd-106">Der Kontoadministrator muss diese API im Azure-Portal abonnieren, damit sie verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="440bd-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="440bd-107">Informationen finden Sie unter [Verwalten des Zugriffs auf die Azure-Abrechnung mithilfe von Rollen](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="440bd-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="440bd-108">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="440bd-108">Install the npm module</span></span> 

<span data-ttu-id="440bd-109">Installieren des npm-Moduls für die Azure-Abrechnung</span><span class="sxs-lookup"><span data-stu-id="440bd-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="440bd-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="440bd-110">Example</span></span> 
 
<span data-ttu-id="440bd-111">Mit diesem Beispiel wird eine Liste aller bisherigen Rechnung ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="440bd-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="440bd-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="440bd-112">Samples</span></span>

<span data-ttu-id="440bd-113">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="440bd-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
