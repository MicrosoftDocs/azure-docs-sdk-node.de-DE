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
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50354258"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="2bbc1-103">Azure Data Lake Store-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="2bbc1-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="2bbc1-104">Azure Data Lake-Speicher ist ein unternehmensweites riesiges Repository für Big Data-Analyseworkloads.</span><span class="sxs-lookup"><span data-stu-id="2bbc1-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="2bbc1-105">Azure Data Lake bietet Ihnen die Möglichkeit, Daten von beliebiger Größe, Art und Erfassungsgeschwindigkeit zur Durchführung operativer und explorativer Analysen an einem einzigen Ort zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="2bbc1-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="2bbc1-106">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="2bbc1-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2bbc1-107">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="2bbc1-107">Install the npm module</span></span>

<span data-ttu-id="2bbc1-108">Installieren der Azure Data Lake Store-Module für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="2bbc1-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="2bbc1-109">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2bbc1-109">Example</span></span>

<span data-ttu-id="2bbc1-110">Mit diesem Beispiel werden alle Data Lake Store-Konten innerhalb eines bestimmten Azure-Abonnements aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="2bbc1-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="2bbc1-111">Beispiele</span><span class="sxs-lookup"><span data-stu-id="2bbc1-111">Samples</span></span>

<span data-ttu-id="2bbc1-112">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2bbc1-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
