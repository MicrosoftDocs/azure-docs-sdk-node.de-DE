---
title: "Azure App Service-Module für Node.js"
description: "Referenz zu Azure App Service-Modulen für Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: b722344f056a52785aef6d853a797231dcafc699
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a>Azure App Service-Module für Node.js

## <a name="overview"></a>Übersicht

Azure App Service ist ein Platform-as-a-Service-Angebot (PaaS) von Microsoft Azure. Erstellen Sie Web-Apps und mobile Apps für alle Plattformen oder Geräte. Integrieren Sie Ihre Apps in SaaS-Lösungen, stellen Sie eine Verbindung mit lokalen Anwendungen her, und automatisieren Sie Ihre Geschäftsprozesse. Azure führt Ihre Apps auf vollständig verwalteten virtuellen Computern (VMs) mit den freigegebenen VM-Ressourcen oder dedizierten VMs aus.

App Service umfasst die Webfunktionen und mobilen Funktionen, die wir vorher separat als Azure Websites und Azure Mobile Services bereitgestellt haben. Außerdem sind neue Funktionen zum Automatisieren von Geschäftsprozessen und Hosten von Cloud-APIs enthalten. Als einzelner integrierter Dienst können Sie mit App Service verschiedene Komponenten – Websites, Back-Ends für mobile Apps, RESTful-APIs und Geschäftsprozesse – in einer zentralen Lösung zusammenstellen.

## <a name="management-package"></a>Verwaltungspaket

### <a name="install-the-npm-package"></a>Installieren des npm-Pakets

Installieren des Azure App Service-Moduls für Node.js mithilfe von npm

```bash
npm install azure-arm-website
```

### <a name="example"></a>Beispiel

Mit diesem Beispiel wird eine Website in Azure mithilfe von Node.js erstellt:

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>Beispiele

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.
