---
title: "Azure Machine Learning-Module für Node.js"
description: "Referenz zu Azure Machine Learning-Modulen für Node.js"
keywords: Azure,SDK,API,Machine Learning, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="6c81b-104">Azure Machine Learning-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="6c81b-104">Azure Machine Learning modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6c81b-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="6c81b-105">Overview</span></span>

<span data-ttu-id="6c81b-106">Machine Learning ist ein Data Science-Verfahren, bei dem Computer aus vorhandenen Daten lernen können, um zukünftiges Verhalten, Ergebnisse und Trends vorherzusagen.</span><span class="sxs-lookup"><span data-stu-id="6c81b-106">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="6c81b-107">Dank solcher Vorhersagen oder Prognosen aus maschinellen Lernprozessen können Apps und Geräte "intelligenter" werden.</span><span class="sxs-lookup"><span data-stu-id="6c81b-107">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="6c81b-108">Wenn Sie online einkaufen, trägt maschinelles Lernen dazu bei, dass Ihnen anhand der gekauften Produkte weitere Produkte empfohlen werden, die Ihnen gefallen könnten.</span><span class="sxs-lookup"><span data-stu-id="6c81b-108">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="6c81b-109">Wenn Ihre Kreditkarte verwendet wird, vergleichen Machine Learning-Prozesse die Transaktion mit einer Transaktionsdatenbank und helfen bei der Betrugserkennung.</span><span class="sxs-lookup"><span data-stu-id="6c81b-109">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="6c81b-110">Wenn ein automatischer Staubsauger ein Zimmer saugt, wird anhand von Machine Learning-Prozessen entschieden, ob die Arbeit erledigt ist.</span><span class="sxs-lookup"><span data-stu-id="6c81b-110">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="6c81b-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="6c81b-111">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="6c81b-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="6c81b-112">Install the npm module</span></span>

<span data-ttu-id="6c81b-113">Installieren des npm-Moduls für Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="6c81b-113">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="6c81b-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6c81b-114">Example</span></span>

<span data-ttu-id="6c81b-115">Mit diesem Beispiel werden alle Machine Learning-Vorhaben aufgelistet:</span><span class="sxs-lookup"><span data-stu-id="6c81b-115">This example lists all machine learning committment plans.</span></span>

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

## <a name="samples"></a><span data-ttu-id="6c81b-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6c81b-116">Samples</span></span>

<span data-ttu-id="6c81b-117">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="6c81b-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
