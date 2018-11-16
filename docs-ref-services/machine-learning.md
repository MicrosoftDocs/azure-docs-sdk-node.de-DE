---
title: Azure Machine Learning-Module für Node.js
description: Referenz zu Azure Machine Learning-Modulen für Node.js
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439104"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="e2863-103">Azure Machine Learning-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="e2863-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="e2863-104">Machine Learning ist ein Data Science-Verfahren, bei dem Computer aus vorhandenen Daten lernen können, um zukünftiges Verhalten, Ergebnisse und Trends vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="e2863-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="e2863-105">Dank solcher Vorhersagen oder Prognosen aus maschinellen Lernprozessen können Apps und Geräte "intelligenter" werden.</span><span class="sxs-lookup"><span data-stu-id="e2863-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="e2863-106">Wenn Sie online einkaufen, trägt maschinelles Lernen dazu bei, dass Ihnen anhand der gekauften Produkte weitere Produkte empfohlen werden, die Ihnen gefallen könnten.</span><span class="sxs-lookup"><span data-stu-id="e2863-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="e2863-107">Wenn Ihre Kreditkarte verwendet wird, vergleichen Machine Learning-Prozesse die Transaktion mit einer Transaktionsdatenbank und helfen bei der Betrugserkennung.</span><span class="sxs-lookup"><span data-stu-id="e2863-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="e2863-108">Wenn ein automatischer Staubsauger ein Zimmer saugt, wird anhand von Machine Learning-Prozessen entschieden, ob die Arbeit erledigt ist.</span><span class="sxs-lookup"><span data-stu-id="e2863-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="e2863-109">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="e2863-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="e2863-110">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="e2863-110">Install the npm module</span></span>

<span data-ttu-id="e2863-111">Installieren des npm-Moduls für Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="e2863-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="e2863-112">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e2863-112">Example</span></span>

<span data-ttu-id="e2863-113">Mit diesem Beispiel werden alle Machine Learning-Vorhaben aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="e2863-113">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="e2863-114">Beispiele</span><span class="sxs-lookup"><span data-stu-id="e2863-114">Samples</span></span>

<span data-ttu-id="e2863-115">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e2863-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
