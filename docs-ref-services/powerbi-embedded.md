---
title: Azure Power BI Embedded-Module für Node.js
description: Referenz zu Azure Power BI Embedded-Modulen für Node.js
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50405756"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a>Azure Power BI Embedded-Module für Node.js

Mit dem Power BI Embedded-Dienst von Azure können Sie Power BI-Berichte direkt in Ihre Node-Anwendung integrieren, um Diagramme und Berichte zu erstellen oder zu bearbeiten.

Weitere Informationen zu [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/)

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des npm-Moduls für Azure Power BI

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird eine Arbeitsbereichssammlung in einer vorhandenen Ressourcengruppe erstellt:

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Beispiele

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
