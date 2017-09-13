---
title: "Azure Operational Insights-Module für Node.js"
description: "Referenz zu Azure Operational Insights-Modulen für Node.js"
keywords: Azure,SDK,API,Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a>Azure Operational Insights-Module für Node.js

## <a name="overview"></a>Übersicht

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-module"></a>Installieren des npm-Moduls

Installieren des Azure Operational Insights-Moduls für Node.js mithilfe von npm

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>Beispiel 

Mit diesem Beispiel wird ein Client erstellt, eine Verbindung mit Operational Insights hergestellt und eine Liste der Arbeitsbereiche anhand einer bestimmten Ressourcengruppe abgerufen:

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a>Beispiele

Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
