---
title: Azure Advisor-Module für Node.js
description: Referenz zu Azure Advisor-Modulen für Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 952ac4bb67f4c177a06ce0ae3eb0fac7fa8ded54
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052587"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="ca5c8-103">Azure Advisor-Module für Node.js</span><span class="sxs-lookup"><span data-stu-id="ca5c8-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ca5c8-104">Übersicht</span><span class="sxs-lookup"><span data-stu-id="ca5c8-104">Overview</span></span>

<span data-ttu-id="ca5c8-105">Bei Azure Advisor handelt es sich um einen personalisierten Cloudberater, der Sie mit bewährten Methoden zum Optimieren von Azure-Bereitstellungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ca5c8-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="ca5c8-106">Der Advisor analysiert Ihre Ressourcenkonfiguration und Nutzungstelemetrie und macht anschließend Vorschläge zu Lösungen, die die Wirtschaftlichkeit, Leistung, Hochverfügbarkeit und Sicherheit Ihrer Azure-Ressourcen steigern können.</span><span class="sxs-lookup"><span data-stu-id="ca5c8-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="ca5c8-107">Der Advisor ermöglicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ca5c8-107">With Advisor, you can:</span></span>
- <span data-ttu-id="ca5c8-108">Abrufen proaktiver, umsetzbarer und individueller Empfehlungen und bewährter Methoden.</span><span class="sxs-lookup"><span data-stu-id="ca5c8-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="ca5c8-109">Verbessern der Leistung, Sicherheit und Hochverfügbarkeit Ihrer Ressourcen und Ermitteln von Möglichkeiten der Senkung Ihrer Gesamtausgaben für Azure.</span><span class="sxs-lookup"><span data-stu-id="ca5c8-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="ca5c8-110">Abrufen von Empfehlungen mit vorgeschlagenen Inlineaktionen.</span><span class="sxs-lookup"><span data-stu-id="ca5c8-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="ca5c8-111">Verwaltungspaket</span><span class="sxs-lookup"><span data-stu-id="ca5c8-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ca5c8-112">Installieren des npm-Moduls</span><span class="sxs-lookup"><span data-stu-id="ca5c8-112">Install the npm module</span></span>

<span data-ttu-id="ca5c8-113">Installieren des npm-Moduls für den Azure Advisor</span><span class="sxs-lookup"><span data-stu-id="ca5c8-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="ca5c8-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ca5c8-114">Example</span></span>

<span data-ttu-id="ca5c8-115">Mit diesem Beispiel wird die Liste der Empfehlungen von Azure Advisor angezeigt:</span><span class="sxs-lookup"><span data-stu-id="ca5c8-115">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="ca5c8-116">Beispiele</span><span class="sxs-lookup"><span data-stu-id="ca5c8-116">Samples</span></span>

<span data-ttu-id="ca5c8-117">Sehen Sie sich den weiteren [Node.js-Beispielcode](https://azure.microsoft.com/resources/samples/?platform=nodejs) an, den Sie in Ihren Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ca5c8-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
