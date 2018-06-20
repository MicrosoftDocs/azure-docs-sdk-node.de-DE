---
title: Azure Data Lake Store-Module für Node.js
description: Referenz zu Azure Data Lake Store-Modulen für Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: a108cc6d184b72d2d4227f9e60da6b7a535f92ae
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
ms.locfileid: "28117125"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="0b6f2-103">Azure Data Lake Store-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="0b6f2-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="0b6f2-104">Azure Data Lake-Speicher ist ein unternehmensweites riesiges Repository für Big Data-Analyseworkloads.</span><span class="sxs-lookup"><span data-stu-id="0b6f2-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="0b6f2-105">Azure Data Lake bietet Ihnen die Möglichkeit, Daten von beliebiger Größe, Art und Erfassungsgeschwindigkeit zur Durchführung operativer und explorativer Analysen an einem einzigen Ort zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="0b6f2-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="0b6f2-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="0b6f2-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0b6f2-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="0b6f2-107">Install the npm module</span></span>

<span data-ttu-id="0b6f2-108">Installieren der Azure Data Lake Store-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="0b6f2-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="0b6f2-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0b6f2-109">Example</span></span>

<span data-ttu-id="0b6f2-110">Mit diesem Beispiel werden alle Data Lake Store-Konten innerhalb eines bestimmten Azure-Abonnements aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="0b6f2-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="0b6f2-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="0b6f2-111">Samples</span></span>

<span data-ttu-id="0b6f2-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0b6f2-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
