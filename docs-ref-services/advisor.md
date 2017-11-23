---
title: "Azure-Ratgeber-Module für Node.js"
description: "Referenz zu Azure-Ratgeber-Modulen für Node.js"
keywords: Azure,SDK,API,Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="c2fcc-104">Azure-Ratgeber-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="c2fcc-104">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c2fcc-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c2fcc-105">Overview</span></span>

<span data-ttu-id="c2fcc-106">Bei Azure Advisor handelt es sich um einen personalisierten Cloudberater, der Sie mit bewährten Methoden zum Optimieren von Azure-Bereitstellungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2fcc-106">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="c2fcc-107">Ratgeber analysiert Ihre Ressourcenkonfiguration und Nutzungstelemetrie und macht anschließend Vorschläge zu Lösungen, die die Wirtschaftlichkeit, Leistung, Verfügbarkeit und Sicherheit Ihrer Azure-Ressourcen steigern können.</span><span class="sxs-lookup"><span data-stu-id="c2fcc-107">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="c2fcc-108">Der Ratgeber ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c2fcc-108">With Advisor, you can:</span></span>
- <span data-ttu-id="c2fcc-109">Abrufen proaktiver, umsetzbarer und individueller Empfehlungen und bewährter Methoden.</span><span class="sxs-lookup"><span data-stu-id="c2fcc-109">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="c2fcc-110">Verbessern der Leistung, Sicherheit und Verfügbarkeit Ihrer Ressourcen und Ermitteln von Möglichkeiten der Senkung Ihrer Gesamtausgaben für Azure.</span><span class="sxs-lookup"><span data-stu-id="c2fcc-110">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="c2fcc-111">Abrufen von Empfehlungen mit vorgeschlagenen Inlineaktionen.</span><span class="sxs-lookup"><span data-stu-id="c2fcc-111">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="c2fcc-112">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="c2fcc-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c2fcc-113">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="c2fcc-113">Install the npm module</span></span>

<span data-ttu-id="c2fcc-114">Installieren des npm-Moduls für Azure-Ratgeber</span><span class="sxs-lookup"><span data-stu-id="c2fcc-114">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="c2fcc-115">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c2fcc-115">Example</span></span>

<span data-ttu-id="c2fcc-116">Mit diesem Beispiel wird die Liste der Empfehlungen von Azure-Ratgeber angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c2fcc-116">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="c2fcc-117">Beispiele</span><span class="sxs-lookup"><span data-stu-id="c2fcc-117">Samples</span></span>

<span data-ttu-id="c2fcc-118">Sehen Sie sich weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="c2fcc-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
