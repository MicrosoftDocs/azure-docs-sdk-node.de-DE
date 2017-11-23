---
title: "Azure Data Lake Store-Module für Node.js"
description: "Referenz zu Azure Data Lake Store-Modulen für Node.js"
keywords: Azure,SDK,API,Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="44b8f-104">Azure Data Lake Store-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="44b8f-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="44b8f-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="44b8f-105">Overview</span></span>
<span data-ttu-id="44b8f-106">Azure Data Lake-Speicher ist ein unternehmensweites riesiges Repository für Big Data-Analyseworkloads.</span><span class="sxs-lookup"><span data-stu-id="44b8f-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="44b8f-107">Azure Data Lake bietet Ihnen die Möglichkeit, Daten von beliebiger Größe, Art und Erfassungsgeschwindigkeit zur Durchführung operativer und explorativer Analysen an einem einzigen Ort zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="44b8f-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="44b8f-108">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="44b8f-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="44b8f-109">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="44b8f-109">Install the npm module</span></span>

<span data-ttu-id="44b8f-110">Installieren der Azure Data Lake Store-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="44b8f-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="44b8f-111">Beispiel</span><span class="sxs-lookup"><span data-stu-id="44b8f-111">Example</span></span>

<span data-ttu-id="44b8f-112">Mit diesem Beispiel werden alle Data Lake Store-Konten innerhalb eines bestimmten Azure-Abonnements aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="44b8f-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="44b8f-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="44b8f-113">Samples</span></span>

<span data-ttu-id="44b8f-114">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="44b8f-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
