---
title: "Azure Commerce-Module für Node.js"
description: "Referenz zu Azure Commerce-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 0597765543cd838049d3946b90ae128875edd4e5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="ebc41-103">Azure Commerce-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="ebc41-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ebc41-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="ebc41-104">Overview</span></span>

<span data-ttu-id="ebc41-105">Verwenden Sie Azure Commerce-APIs, um Nutzungs- und Ressourcendaten mittels Pull in Ihre bevorzugten Datenanalysetools zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="ebc41-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="ebc41-106">Mithilfe der Azure-Ressourcennutzungs- und -Gebührenkarten-APIs können Sie Ihre Kosten genau vorhersagen und verwalten.</span><span class="sxs-lookup"><span data-stu-id="ebc41-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="ebc41-107">Die APIs werden als Ressourcenanbieter implementiert und sind Teil der API-Familie, die von Azure Resource Manager verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="ebc41-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="ebc41-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="ebc41-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ebc41-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="ebc41-109">Install the npm module</span></span>

<span data-ttu-id="ebc41-110">Installieren des npm-Moduls für Azure Commerce</span><span class="sxs-lookup"><span data-stu-id="ebc41-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="ebc41-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ebc41-111">Example</span></span>

<span data-ttu-id="ebc41-112">Mit diesem Beispiel werden die geschätzten Azure-Nutzungsdaten für den letzten Monat abgerufen:</span><span class="sxs-lookup"><span data-stu-id="ebc41-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ebc41-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ebc41-113">Samples</span></span>

<span data-ttu-id="ebc41-114">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ebc41-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
