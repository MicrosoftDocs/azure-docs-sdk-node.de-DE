---
title: Azure Search-Module für Node.js
description: Referenz zu Azure Search-Modulen für Node.js
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: 895281acd2359240f3d483e4205c628e1f85f724
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="889c5-103">Azure Search-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="889c5-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="889c5-104">Azure Search ist eine cloudbasierte SaaS-Lösung, deren Server- und Infrastrukturtechnologien von Microsoft verwaltet werden. Dadurch erhalten Sie einen sofort einsatzbereiten Dienst, den Sie mit Ihren Daten füllen und anschließend verwenden können, um Ihrer Anwendung eine Suchfunktion hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="889c5-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="889c5-105">Weitere Informationen zu [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search)</span><span class="sxs-lookup"><span data-stu-id="889c5-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="889c5-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="889c5-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="889c5-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="889c5-107">Install the npm module</span></span>

<span data-ttu-id="889c5-108">Installieren des npm-Moduls für Azure Search</span><span class="sxs-lookup"><span data-stu-id="889c5-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="889c5-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="889c5-109">Example</span></span>

<span data-ttu-id="889c5-110">Mit diesem Beispiel wird ein neuer Search-Dienst in Azure erstellt, und alle Ressourcen in seiner Ressourcengruppe werden aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="889c5-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="889c5-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="889c5-111">Samples</span></span>

<span data-ttu-id="889c5-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="889c5-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
