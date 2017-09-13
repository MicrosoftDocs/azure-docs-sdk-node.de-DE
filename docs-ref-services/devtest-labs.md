---
title: "Azure DevTest Labs-Module für Node.js"
description: "Referenz zu Azure DevTest Labs-Modulen für Node.js"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Azure DevTest Labs-Module für Node.js

## <a name="overview"></a>Übersicht

Azure DevTest Labs ist ein Dienst, der Entwicklern und Testern dabei hilft, Umgebungen in Azure schnell zu erstellen und dabei unnötigen Aufwand zu minimieren und die Kosten unter Kontrolle zu halten. Sie können die neueste Version Ihrer Anwendung testen, indem Sie schnell Windows- und Linux-Umgebungen mit wiederverwendbaren Vorlagen und Artefakten bereitstellen. Integrieren Sie Ihre Bereitstellungspipeline einfach mit DevTest Labs, um Umgebungen bei Bedarf bereitstellen zu können. Skalieren Sie Ihre Auslastungstests zentral hoch, indem Sie mehrere Test-Agents bereitstellen, und erstellen Sie vorab bereitgestellte Umgebungen für Schulungen und Vorführungen.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure DevTest Labs

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel werden die Details eines Labs abgerufen und ausgegeben:

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
