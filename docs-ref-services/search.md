---
title: "Azure Search-Module für Node.js"
description: "Referenz zu Azure Search-Modulen für Node.js"
keywords: Azure,SDK,API,Search, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="99e44-104">Azure Search-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="99e44-104">Azure Search modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="99e44-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="99e44-105">Overview</span></span>

<span data-ttu-id="99e44-106">Azure Search ist eine cloudbasierte SaaS-Lösung, deren Server- und Infrastrukturtechnologien von Microsoft verwaltet werden. Dadurch erhalten Sie einen sofort einsatzbereiten Dienst, den Sie mit Ihren Daten füllen und anschließend verwenden können, um Ihrer Anwendung eine Suchfunktion hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="99e44-106">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="99e44-107">Weitere Informationen zu [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)</span><span class="sxs-lookup"><span data-stu-id="99e44-107">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="99e44-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="99e44-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="99e44-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="99e44-109">Install the npm module</span></span>

<span data-ttu-id="99e44-110">Installieren des npm-Moduls für Azure Search</span><span class="sxs-lookup"><span data-stu-id="99e44-110">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="99e44-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="99e44-111">Example</span></span>

<span data-ttu-id="99e44-112">Mit diesem Beispiel wird ein neuer Search-Dienst in Azure erstellt, und alle Ressourcen in seiner Ressourcengruppe werden aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="99e44-112">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="99e44-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="99e44-113">Samples</span></span>

<span data-ttu-id="99e44-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="99e44-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
