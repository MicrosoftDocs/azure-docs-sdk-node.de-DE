---
title: "Azure Search-Module für Node.js"
description: "Referenz zu Azure Search-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: bf99013b4479548d07531358bc5103b4e6ac7977
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="5fc17-103">Azure Search-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="5fc17-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="5fc17-104">Azure Search ist eine cloudbasierte SaaS-Lösung, deren Server- und Infrastrukturtechnologien von Microsoft verwaltet werden. Dadurch erhalten Sie einen sofort einsatzbereiten Dienst, den Sie mit Ihren Daten füllen und anschließend verwenden können, um Ihrer Anwendung eine Suchfunktion hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5fc17-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="5fc17-105">Weitere Informationen zu [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)</span><span class="sxs-lookup"><span data-stu-id="5fc17-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="5fc17-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="5fc17-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5fc17-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="5fc17-107">Install the npm module</span></span>

<span data-ttu-id="5fc17-108">Installieren des npm-Moduls für Azure Search</span><span class="sxs-lookup"><span data-stu-id="5fc17-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="5fc17-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5fc17-109">Example</span></span>

<span data-ttu-id="5fc17-110">Mit diesem Beispiel wird ein neuer Search-Dienst in Azure erstellt, und alle Ressourcen in seiner Ressourcengruppe werden aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="5fc17-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="5fc17-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="5fc17-111">Samples</span></span>

<span data-ttu-id="5fc17-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5fc17-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
