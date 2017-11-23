---
title: "Azure App Service-Module für Node.js"
description: "Referenz zu Azure App Service-Modulen für Node.js"
keywords: Azure, Node, SDK, API, Web-Apps, mobil, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="63404-104">Azure App Service-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="63404-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="63404-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="63404-105">Overview</span></span>

<span data-ttu-id="63404-106">Azure App Service ist ein Platform-as-a-Service-Angebot (PaaS) von Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="63404-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="63404-107">Erstellen Sie Web-Apps und mobile Apps für alle Plattformen oder Geräte.</span><span class="sxs-lookup"><span data-stu-id="63404-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="63404-108">Integrieren Sie Ihre Apps in SaaS-Lösungen, stellen Sie eine Verbindung mit lokalen Anwendungen her, und automatisieren Sie Ihre Geschäftsprozesse.</span><span class="sxs-lookup"><span data-stu-id="63404-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="63404-109">Azure führt Ihre Apps auf vollständig verwalteten virtuellen Computern (VMs) mit den freigegebenen VM-Ressourcen oder dedizierten VMs aus.</span><span class="sxs-lookup"><span data-stu-id="63404-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="63404-110">App Service umfasst die Webfunktionen und mobilen Funktionen, die wir vorher separat als Azure Websites und Azure Mobile Services bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="63404-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="63404-111">Außerdem sind neue Funktionen zum Automatisieren von Geschäftsprozessen und Hosten von Cloud-APIs enthalten.</span><span class="sxs-lookup"><span data-stu-id="63404-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="63404-112">Als einzelner integrierter Dienst können Sie mit App Service verschiedene Komponenten – Websites, Back-Ends für mobile Apps, RESTful-APIs und Geschäftsprozesse – in einer zentralen Lösung zusammenstellen.</span><span class="sxs-lookup"><span data-stu-id="63404-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="63404-113">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="63404-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="63404-114">Installieren des npm-Pakets</span><span class="sxs-lookup"><span data-stu-id="63404-114">Install the npm package</span></span>

<span data-ttu-id="63404-115">Installieren des Azure App Service-Moduls für Node.js mithilfe von npm</span><span class="sxs-lookup"><span data-stu-id="63404-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="63404-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="63404-116">Example</span></span>

<span data-ttu-id="63404-117">Mit diesem Beispiel wird eine Website in Azure mithilfe von Node.js erstellt:</span><span class="sxs-lookup"><span data-stu-id="63404-117">This example creates a website on Azure using Node.js.</span></span>

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

## <a name="samples"></a><span data-ttu-id="63404-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="63404-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="63404-119">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="63404-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
