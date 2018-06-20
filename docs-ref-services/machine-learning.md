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
ms.openlocfilehash: 7dfa6d8fa633863fe834ce73462584e79c312c5d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259889"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Azure Machine Learning-Module für Node.js

Machine Learning ist ein Data Science-Verfahren, bei dem Computer aus vorhandenen Daten lernen können, um zukünftiges Verhalten, Ergebnisse und Trends vorherzusagen. Dank solcher Vorhersagen oder Prognosen aus maschinellen Lernprozessen können Apps und Geräte "intelligenter" werden. Wenn Sie online einkaufen, trägt maschinelles Lernen dazu bei, dass Ihnen anhand der gekauften Produkte weitere Produkte empfohlen werden, die Ihnen gefallen könnten. Wenn Ihre Kreditkarte verwendet wird, vergleichen Machine Learning-Prozesse die Transaktion mit einer Transaktionsdatenbank und helfen bei der Betrugserkennung. Wenn ein automatischer Staubsauger ein Zimmer saugt, wird anhand von Machine Learning-Prozessen entschieden, ob die Arbeit erledigt ist.

## <a name="management-package"></a>Verwaltungspaket


### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure Machine Learning

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden alle Machine Learning-Vorhaben aufgelistet:

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

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
